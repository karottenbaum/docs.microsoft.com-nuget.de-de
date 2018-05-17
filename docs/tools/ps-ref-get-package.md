---
title: NuGet-Get-Package-PowerShell-Referenz
description: Referenz für die Get-Package-PowerShell-Befehl in der NuGet-Paket-Manager-Konsole in Visual Studio.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 12/07/2017
ms.topic: reference
ms.openlocfilehash: c70e60b7391f19026e2dcd502d667fbe1da7e6e2
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="get-package-package-manager-console-in-visual-studio"></a><span data-ttu-id="a2eaa-103">Get-Paket (Paket-Manager-Konsole in Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="a2eaa-103">Get-Package (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="a2eaa-104">*In diesem Thema wird beschrieben, den Befehl innerhalb der [NuGet Package Manager Console](package-manager-console.md) in Visual Studio unter Windows. Der generische PowerShell Get-Package-Befehl finden Sie unter der [PowerShell PackageManagement-Verweis](/powershell/module/packagemanagement/?view=powershell-6).*</span><span class="sxs-lookup"><span data-stu-id="a2eaa-104">*This topic describes the command within the [NuGet Package Manager Console](package-manager-console.md) in Visual Studio on Windows. For the generic PowerShell Get-Package command, see the [PowerShell PackageManagement reference](/powershell/module/packagemanagement/?view=powershell-6).*</span></span>

<span data-ttu-id="a2eaa-105">Ruft die Liste der Pakete, die im lokalen Repository installiert, listet die verfügbaren Pakete aus einem Paketquelle bei Verwendung mit dem Switch - ListAvailable oder verfügbaren Updates bei Verwendung mit dem Schalter Update aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-105">Retrieves the list of packages installed in the local repository, lists packages available from a package source when used with the -ListAvailable switch, or lists available updates when used with the -Update switch.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2eaa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a2eaa-106">Syntax</span></span>

```ps
Get-Package -Source <string> [-ListAvailable] [-Updates] [-ProjectName <string>]
    [-Filter <string>] [-First <int>] [-Skip <int>] [-AllVersions] [-IncludePrerelease]
    [-PageSize] [<CommonParameters>]
```

<span data-ttu-id="a2eaa-107">Ohne Parameter `Get-Package` zeigt die Liste der im Standardprojekt installierten Pakete.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-107">With no parameters, `Get-Package` displays the list of packages installed in the default project.</span></span>

## <a name="parameters"></a><span data-ttu-id="a2eaa-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="a2eaa-108">Parameters</span></span>

| <span data-ttu-id="a2eaa-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="a2eaa-109">Parameter</span></span> | <span data-ttu-id="a2eaa-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a2eaa-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="a2eaa-111">Quelle</span><span class="sxs-lookup"><span data-stu-id="a2eaa-111">Source</span></span> | <span data-ttu-id="a2eaa-112">Der URL oder einen Ordner Pfad für das Paket.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-112">The URL or folder path for the package .</span></span> <span data-ttu-id="a2eaa-113">Lokale Ordnerpfaden kann absolut oder relativ zum aktuellen Ordner.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-113">Local folder paths can be absolute, or relative to the current folder.</span></span> <span data-ttu-id="a2eaa-114">Wenn nicht angegeben, `Get-Package` die aktuell ausgewählten Paketquelle durchsucht.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-114">If omitted, `Get-Package` searches the currently selected package source.</span></span> <span data-ttu-id="a2eaa-115">Bei Verwendung mit - ListAvailable, standardmäßig nuget.org.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-115">When used with -ListAvailable, defaults to nuget.org.</span></span> |
| <span data-ttu-id="a2eaa-116">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="a2eaa-116">ListAvailable</span></span> | <span data-ttu-id="a2eaa-117">Listet die verfügbaren Pakete aus einem Paketquelle nuget.org direktionales. Zeigt den Standardwert von 50 Paketen an, es sei denn, - PageSize und/oder -erste angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-117">Lists packages available from a package source, defaulting to nuget.org. Shows a default of 50 packages unless -PageSize and/or -First are specified.</span></span> |
| <span data-ttu-id="a2eaa-118">Updates</span><span class="sxs-lookup"><span data-stu-id="a2eaa-118">Updates</span></span> | <span data-ttu-id="a2eaa-119">Listet die Pakete, die in der Paketquelle ein Update verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-119">Lists packages that have an update available from the package source.</span></span> |
| <span data-ttu-id="a2eaa-120">ProjektName</span><span class="sxs-lookup"><span data-stu-id="a2eaa-120">ProjectName</span></span> | <span data-ttu-id="a2eaa-121">Das Projekt aus dem installierte Pakete abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-121">The project from which to get installed packages.</span></span> <span data-ttu-id="a2eaa-122">Wenn nicht angegeben ist, installiert gibt Projekte für die gesamte Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-122">If omitted, returns installed projects for the entire solution.</span></span> |
| <span data-ttu-id="a2eaa-123">Filter</span><span class="sxs-lookup"><span data-stu-id="a2eaa-123">Filter</span></span> | <span data-ttu-id="a2eaa-124">Eine Filterzeichenfolge verwendet, um die Liste der Pakete eingrenzen, indem Sie die Paket-ID, die Beschreibung und den Tags zuweisen.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-124">A filter string used to narrow down the list of packages by applying it to the package ID, description, and tags.</span></span> |
| <span data-ttu-id="a2eaa-125">First</span><span class="sxs-lookup"><span data-stu-id="a2eaa-125">First</span></span> | <span data-ttu-id="a2eaa-126">Die Anzahl der Pakete an, ab dem Anfang der Liste zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-126">The number of packages to return from the beginning of the list.</span></span> <span data-ttu-id="a2eaa-127">Wenn nicht angegeben ist, wird standardmäßig auf 50.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-127">If not specified, defaults to 50.</span></span> |
| <span data-ttu-id="a2eaa-128">Skip</span><span class="sxs-lookup"><span data-stu-id="a2eaa-128">Skip</span></span> | <span data-ttu-id="a2eaa-129">Lässt die erste &lt;Int&gt; Pakete aus der angezeigten Liste.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-129">Omits the first &lt;int&gt; packages from the displayed list.</span></span>  |
| <span data-ttu-id="a2eaa-130">AllVersions</span><span class="sxs-lookup"><span data-stu-id="a2eaa-130">AllVersions</span></span> | <span data-ttu-id="a2eaa-131">Zeigt alle verfügbaren Versionen der einzelnen Pakete, anstatt nur die neueste Version.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-131">Displays all available versions of each package instead of only the latest version.</span></span> |
| <span data-ttu-id="a2eaa-132">IncludePrerelease</span><span class="sxs-lookup"><span data-stu-id="a2eaa-132">IncludePrerelease</span></span> | <span data-ttu-id="a2eaa-133">Enthält Vorabversionen von Paketen in den Ergebnissen an.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-133">Includes prerelease packages in the results.</span></span> |
| <span data-ttu-id="a2eaa-134">PageSize</span><span class="sxs-lookup"><span data-stu-id="a2eaa-134">PageSize</span></span> | <span data-ttu-id="a2eaa-135">*(3.0 +)*  Bei Verwendung mit - ListAvailable (erforderlich), die Anzahl der Pakete auflisten, die vor der Übergabe einer Eingabeaufforderung aus, um den Vorgang fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-135">*(3.0+)* When used with -ListAvailable (required), the number of packages to list before giving a prompt to continue.</span></span> |

<span data-ttu-id="a2eaa-136">Keines dieser Parameter akzeptieren Pipeline Eingabe- oder Platzhalter-Zeichen.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-136">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="a2eaa-137">Allgemeine Parameter</span><span class="sxs-lookup"><span data-stu-id="a2eaa-137">Common Parameters</span></span>

<span data-ttu-id="a2eaa-138">`Get-Package` unterstützt die folgenden [allgemeine PowerShell-Parameter](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Fehleraktion, ErrorVariable, -OutBuffer, OutVariable, mit "pipelinevariable", ausführlich, WarningAction und WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a2eaa-138">`Get-Package` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="a2eaa-139">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a2eaa-139">Examples</span></span>

```ps
# Lists the packages installed in the current solution
Get-Package

# Lists the packages installed in a project
Get-Package -ProjectName MyProject

# Lists packages available in the current package source
Get-Package -ListAvailable

# Lists 30 packages at a time from the current source, and prompts to continue if more are available
Get-Package -ListAvailable -PageSize 30

# Lists packages with the Ninject keyword in the current source, up to 50
Get-Package -ListAvailable -Filter Ninject

# List all versions of packages matching the filter "jquery"
Get-Package -ListAvailable -Filter jquery -AllVersions

# Lists packages installed in the solution that have available updates
Get-Package -Updates

# Lists packages installed in a specific project that have available updates
Get-Package -Updates -ProjectName MyProject
```