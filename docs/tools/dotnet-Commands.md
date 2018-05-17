---
title: Dotnet NuGet-Befehle
description: Eine kurze Referenz für NuGet-bezogenen Befehlen, die über die Befehlszeilenschnittstelle Dotnet.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/23/2018
ms.topic: conceptual
ms.openlocfilehash: fe49274af339c987d5e090c99edd78f62f59ce47
ms.sourcegitcommit: 5fcd6d664749aa720359104ef7a66d38aeecadc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
# <a name="dotnet-commands"></a><span data-ttu-id="1cd10-103">dotnet-Befehle</span><span class="sxs-lookup"><span data-stu-id="1cd10-103">dotnet commands</span></span>

<span data-ttu-id="1cd10-104">Die `dotnet` Befehlszeilen-Schnittstelle, die unter Windows, Mac OS X und Linux ausgeführt wird, bietet eine Reihe von wesentlichen nuget.exe Befehle aus, wie im folgenden aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="1cd10-104">The `dotnet` command-line interface, which runs on Windows, Mac OS X, and Linux, provides a number of essential nuget.exe commands as listed below.</span></span> <span data-ttu-id="1cd10-105">Wenn Dotnet Ihre Anforderungen erfüllt, ist es nicht erforderlich, verwenden Sie `nuget.exe`.</span><span class="sxs-lookup"><span data-stu-id="1cd10-105">If dotnet satisfies your needs, it's not necessary to use `nuget.exe`.</span></span>

<span data-ttu-id="1cd10-106">Weitere Informationen zum `dotnet`, finden Sie unter [.NET Core-Befehlszeilenschnittstelle (CLI) Tools](/dotnet/core/tools/?tabs=netcore2x).</span><span class="sxs-lookup"><span data-stu-id="1cd10-106">For complete information on `dotnet`, see [.NET Core command-line interface (CLI) tools](/dotnet/core/tools/?tabs=netcore2x).</span></span>

## <a name="package-consumption"></a><span data-ttu-id="1cd10-107">Paket-Verbrauch</span><span class="sxs-lookup"><span data-stu-id="1cd10-107">Package consumption</span></span>

- <span data-ttu-id="1cd10-108">[**Dotnet Paket hinzufügen**](/dotnet/core/tools/dotnet-add-package): Fügt einen Verweis Paket an der Projektdatei, führt dann `dotnet restore` zum Installieren des Pakets.</span><span class="sxs-lookup"><span data-stu-id="1cd10-108">[**dotnet add package**](/dotnet/core/tools/dotnet-add-package): Adds a package reference to the project file, then runs `dotnet restore` to install the package.</span></span>
- <span data-ttu-id="1cd10-109">[**Dotnet Paket entfernen**](/dotnet/core/tools/dotnet-remove-package): entfernt einen Paket-Verweis aus der Projektdatei.</span><span class="sxs-lookup"><span data-stu-id="1cd10-109">[**dotnet remove package**](/dotnet/core/tools/dotnet-remove-package): Removes a package reference from the project file.</span></span>
- <span data-ttu-id="1cd10-110">[**Dotnet Wiederherstellung**](/dotnet/core/tools/dotnet-restore?tabs=netcore2x): stellt die Abhängigkeiten und Tools eines Projekts wieder her.</span><span class="sxs-lookup"><span data-stu-id="1cd10-110">[**dotnet restore**](/dotnet/core/tools/dotnet-restore?tabs=netcore2x): Restores the dependencies and tools of a project.</span></span> <span data-ttu-id="1cd10-111">Ab NuGet 4.0, führt dies denselben Code wie `nuget restore`.</span><span class="sxs-lookup"><span data-stu-id="1cd10-111">As of NuGet 4.0, this runs the same code as `nuget restore`.</span></span>
- <span data-ttu-id="1cd10-112">[**Dotnet Nuget "lokal"**](/dotnet/core/tools/dotnet-nuget-locals): Listet die Speicherorte von der *globalen Pakete*, *http-Cache*, und *Temp* Ordner und löscht den Inhalt der Diese Ordner.</span><span class="sxs-lookup"><span data-stu-id="1cd10-112">[**dotnet nuget locals**](/dotnet/core/tools/dotnet-nuget-locals): Lists locations of the *global-packages*, *http-cache*, and *temp* folders and clears the contents of those folders.</span></span>

## <a name="package-creation"></a><span data-ttu-id="1cd10-113">Erstellen von Paketen</span><span class="sxs-lookup"><span data-stu-id="1cd10-113">Package creation</span></span>

- <span data-ttu-id="1cd10-114">[**Dotnet Pack**](/dotnet/core/tools/dotnet-pack?tabs=netcore2x): Packs den Code in ein NuGet-Paket.</span><span class="sxs-lookup"><span data-stu-id="1cd10-114">[**dotnet pack**](/dotnet/core/tools/dotnet-pack?tabs=netcore2x): Packs the code into a NuGet package.</span></span> <span data-ttu-id="1cd10-115">Ab NuGet 4.0, führt dies denselben Code wie `nuget pack`.</span><span class="sxs-lookup"><span data-stu-id="1cd10-115">As of NuGet 4.0, this runs the same code as `nuget pack`.</span></span>
- <span data-ttu-id="1cd10-116">[**Dotnet Nuget Push**](/dotnet/core/tools/dotnet-nuget-push): Es wird ein Paket an einem Server und veröffentlicht ihn, auf nuget.org, Visual Studio Team Services und Drittanbieter-NuGet-Server angewendet.</span><span class="sxs-lookup"><span data-stu-id="1cd10-116">[**dotnet nuget push**](/dotnet/core/tools/dotnet-nuget-push): Pushes a package to a server and publishes it, applicable to nuget.org, Visual Studio Team Services, and third-party NuGet servers.</span></span>
- <span data-ttu-id="1cd10-117">[**Löschen von Dotnet Nuget**](/dotnet/core/tools/dotnet-nuget-delete): Löscht oder unlists ein Paket von einem Host, auf nuget.org, Visual Studio Team Services und Drittanbieter-NuGet-Server angewendet.</span><span class="sxs-lookup"><span data-stu-id="1cd10-117">[**dotnet nuget delete**](/dotnet/core/tools/dotnet-nuget-delete): Deletes or unlists a package from a host, applicable to nuget.org, Visual Studio Team Services, and third-party NuGet servers.</span></span>