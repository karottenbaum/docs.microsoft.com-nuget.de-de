---
title: "NuGet-Unterstützung für das Visual Studio-Projektsystem | Microsoft-Dokumentation"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 1/9/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 9d7fa7f6-82ed-4df6-9734-f43a3d8e3b98
description: "Integration von NuGet in das Visual Studio-Projektsystem für Projekttypen von Drittanbietern."
keywords: NuGet in Visual Studio, benutzerdefinierte Projekttypen, Visual Studio-Projekte
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 9c8cad46f18578bec41bd9280985e42972a9b3c1
ms.sourcegitcommit: a40c1c1cc05a46410f317a72f695ad1d80f39fa2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="nuget-support-for-the-visual-studio-project-system"></a>NuGet-Unterstützung für das Visual Studio-Projektsystem

Zur Unterstützung der Projekttypen von Drittanbietern in Visual Studio unterstützt NuGet-3.x und höher das [gemeinsame Projektsystem](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/intro.md) (CPS, Common Project System). NuGet 3.2 und höher unterstützt auch Projektsysteme, bei denen es sich nicht um CPS handelt.

Für die Integration in NuGet muss ein Projektsystem seine eigene Unterstützung für alle in diesem Abschnitt beschriebenen Projektfunktionen ankündigen.


> [!NOTE]
> Deklarieren Sie keine Funktionen, die Ihr Projekt eigentlich gar nicht aufweist, nur um Pakete in Ihrem Projekt installieren zu können. Viele Funktionen von Visual Studio und andere Erweiterungen hängen neben dem NuGet-Client von Projektfunktionen ab. Eine falsche Ankündigung von Funktionen Ihres Projekts kann dazu führen, dass diese Komponenten Fehlfunktionen aufweisen und die Erfahrung Ihres Benutzers beeinträchtigt wird.

## <a name="advertise-project-capabilities"></a>Ankündigen von Projektfunktionen

Der NuGet-Client bestimmt basierend auf den [Projektfunktionen](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/about_project_capabilities.md), welche Pakete mit Ihrem Projekttyp kompatibel sind, wie in der folgenden Tabelle beschrieben.


|Funktion|description|
|----------------|-----------|
|AssemblyReferences|Gibt an, dass das Projekt Assemblyverweise unterstützt (im Unterschied zu WinRTReferences)|
|DeclaredSourceItems|Gibt an, dass es sich bei dem Projekt um ein typisches MSBuild-Projekt (nicht DNX) handelt, da es Quellelemente im Projekt selbst deklariert (anstelle einer Datei vom Typ `project.json`, die voraussetzt, dass alle Dateien im Ordner Teil einer Kompilierung sind).|
|UserSourceItems|Gibt an, dass der Benutzer beliebige Dateien zu seinem Projekt hinzufügen darf.|

Bei CPS-basierten Projektsystemen wurden die Implementierungsdetails für Projektfunktionen, die im folgenden Teil dieses Abschnitts beschrieben werden, für Sie ausgeführt. Weitere Informationen finden Sie unter [Deklarieren von Projektfunktionen in CPS-Projekten](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/about_project_capabilities.md#how-to-declare-project-capabilities-in-your-project).

## <a name="implementing-vsprojectcapabilitiespresencechecker"></a>Implementieren von VsProjectCapabilitiesPresenceChecker

Die Klasse `VsProjectCapabilitiesPresenceChecker` muss die Schnittstelle `IVsBooleanSymbolPresenceChecker` implementieren, die wie folgt definiert ist:

```cs
public interface IVsBooleanSymbolPresenceChecker
{
    /// <summary>
    /// Checks whether the symbols defined may have changed since the last time
    /// this method was called.
    /// </summary>
    /// <param name="versionObject">
    /// The response version object assigned at the last call.
    /// May be null to get the initial version.
    /// At the conclusion of this method call, the reference may be changed so that on a subsequent call
    /// we know what version was last observed. The caller should treat this value as an opaque object,
    /// and should not assume any significance from whether the pointer changed or not.
    /// </param>
    /// <returns>
    /// <c>true</c> if the symbols defined may have changed since the last call to this method
    /// or if <paramref name="versionObject"/> was <c>null</c> upon entering this method.
    /// <c>false</c> if the responses would all be the same.
    /// </returns>
    bool HasChangedSince(ref object versionObject);

    /// <summary>
    /// Checks for the presence of a given symbol.
    /// </summary>
    /// <param name="symbol">The symbol to check for.</param>
    /// <returns><c>true</c> if the symbol is present; <c>false</c> otherwise.</returns>
    bool IsSymbolPresent(string symbol);
}
```


Eine Beispielimplementierung dieser Schnittstelle lautet dann wie folgt:
    
```cs
class VsProjectCapabilitiesPresenceChecker : IVsBooleanSymbolPresenceChecker
{
    /// <summary>
    /// The set of capabilities this project system actually has.
    /// This should be kept current, and honestly reflect what the project can do.
    /// </summary>
    private static readonly HashSet<string> ActualProjectCapabilities = new HashSet<string>(StringComparer.OrdinalIgnoreCase)
        {
            "AssemblyReferences",
            "DeclaredSourceItems",
            "UserSourceItems",
        };

    public bool HasChangedSince(ref object versionObject)
    {
        // If your project capabilities do not change over time while the project is open,
        // you may simply `return false;` from your `HasChangedSince` method.
        return false;
    }

    public bool IsSymbolPresent(string symbol)
    {
        return ActualProjectCapabilities.Contains(symbol);
    }
}
```

Denken Sie daran, Funktionen aus der Gruppe `ActualProjectCapabilities` basierend darauf, was von Ihrem Projektsystem tatsächlich unterstützt wird, hinzuzufügen bzw. zu entfernen. Umfassende Beschreibungen finden Sie in der [Dokumentation zu Projektfunktionen](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/project_capabilities.md).

## <a name="responding-to-queries"></a>Reagieren auf Abfragen

Ein Projekt deklariert diese Funktion durch die Unterstützung der Eigenschaft `VSHPROPID_ProjectCapabilitiesChecker` über die `IVsHierarchy::GetProperty`. Es sollte eine Instanz von `Microsoft.VisualStudio.Shell.Interop.IVsBooleanSymbolPresenceChecker` zurückgeben, die in der Assembly `Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll` definiert ist. Verweisen Sie auf diese Assembly, indem Sie das zugehörige [NuGet-Paket](https://www.nuget.org/packages/Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime) installieren.

Sie könnten beispielsweise die folgende `case`-Anweisung zu der `switch`-Anweisung Ihrer `IVsHierarchy::GetProperty`-Methode hinzufügen:

```cs
case __VSHPROPID8.VSHPROPID_ProjectCapabilitiesChecker:
    propVal = new VsProjectCapabilitiesPresenceChecker();
    return VSConstants.S_OK;
```

## <a name="dte-support"></a>DTE-Unterstützung

NuGet betreibt das Projektsystem, um Referenzen, Inhaltselemente und MSBuild-Importe durch Aufrufen in [DTE](/dotnet/api/envdte.dte?view=visualstudiosdk-2017) hinzuzufügen. DTE ist in Visual Studio die Automatisierungsschnittstelle der obersten Ebene. DTE setzt sich aus einer Reihe von COM-Schnittstellen zusammen, die Sie bereits implementieren können.

Wenn Ihr Projekttyp auf CPS basiert, wird DTE für Sie implementiert.