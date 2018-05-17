---
title: NuGet-CLI-Restore-Befehl
description: Referenz für die nuget.exe Restore-Befehl
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: dd0a74c9ed9b879643ed24cbddacff87310dfd6b
ms.sourcegitcommit: a6ca160b1e7e5c58b135af4eba0e9463127a59e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="restore-command-nuget-cli"></a><span data-ttu-id="9583b-103">RESTORE-Befehl (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="9583b-103">restore command (NuGet CLI)</span></span>

<span data-ttu-id="9583b-104">**Gilt für:** Verpacken Sie Verbrauch &bullet; **unterstützte Versionen:** 2.7 +</span><span class="sxs-lookup"><span data-stu-id="9583b-104">**Applies to:** package consumption &bullet; **Supported versions:** 2.7+</span></span>

<span data-ttu-id="9583b-105">Herunterlädt und installiert alle Pakete fehlen in der `packages` Ordner.</span><span class="sxs-lookup"><span data-stu-id="9583b-105">Downloads and installs any packages missing from the `packages` folder.</span></span> <span data-ttu-id="9583b-106">Bei Verwendung mit NuGet 4.0 und höher und das Format PackageReference generiert eine `<project>.nuget.props` -Datei bei Bedarf in den `obj` Ordner.</span><span class="sxs-lookup"><span data-stu-id="9583b-106">When used with NuGet 4.0+ and the PackageReference format, generates a `<project>.nuget.props` file, if needed, in the `obj` folder.</span></span> <span data-ttu-id="9583b-107">(Die Datei kann aus der quellcodeverwaltung ausgelassen werden.)</span><span class="sxs-lookup"><span data-stu-id="9583b-107">(The file can be omitted from source control.)</span></span>

<span data-ttu-id="9583b-108">Unter Mac OS x und Linux mit der CLI auf Mono wird Wiederherstellen von Paketen mit PackageReference nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9583b-108">On Mac OSX and Linux with the CLI on Mono, restoring packages is not supported with PackageReference.</span></span>

## <a name="usage"></a><span data-ttu-id="9583b-109">Verwendung</span><span class="sxs-lookup"><span data-stu-id="9583b-109">Usage</span></span>

```cli
nuget restore <projectPath> [options]
```

<span data-ttu-id="9583b-110">wobei `<projectPath>` gibt den Speicherort einer Projektmappe oder ein `packages.config` Datei.</span><span class="sxs-lookup"><span data-stu-id="9583b-110">where `<projectPath>` specifies the location of a solution or a `packages.config` file.</span></span> <span data-ttu-id="9583b-111">Finden Sie unter ["Hinweise"](#remarks) unten überwachungshilfsprogrammen Informationen.</span><span class="sxs-lookup"><span data-stu-id="9583b-111">See [Remarks](#remarks) below for behavioral details.</span></span>

## <a name="options"></a><span data-ttu-id="9583b-112">Optionen</span><span class="sxs-lookup"><span data-stu-id="9583b-112">Options</span></span>

| <span data-ttu-id="9583b-113">Option</span><span class="sxs-lookup"><span data-stu-id="9583b-113">Option</span></span> | <span data-ttu-id="9583b-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9583b-114">Description</span></span> |
| --- | --- |
| <span data-ttu-id="9583b-115">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="9583b-115">ConfigFile</span></span> | <span data-ttu-id="9583b-116">Die NuGet-Konfigurationsdatei angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="9583b-116">The NuGet configuration file to apply.</span></span> <span data-ttu-id="9583b-117">Wenn nicht angegeben, `%AppData%\NuGet\NuGet.Config` (Windows) oder `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9583b-117">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="9583b-118">DirectDownload</span><span class="sxs-lookup"><span data-stu-id="9583b-118">DirectDownload</span></span> | <span data-ttu-id="9583b-119">*(4.0 und höher)*  Werden Pakete direkt ohne das Auffüllen des Caches mit Binärdateien oder Metadaten heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="9583b-119">*(4.0+)* Downloads packages directly without populating caches with any binaries or metadata.</span></span> |
| <span data-ttu-id="9583b-120">DisableParallelProcessing</span><span class="sxs-lookup"><span data-stu-id="9583b-120">DisableParallelProcessing</span></span> | <span data-ttu-id="9583b-121">Deaktiviert, die mehrere Pakete gleichzeitig wiederhergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="9583b-121">Disables restoring multiple packages in parallel.</span></span> |
| <span data-ttu-id="9583b-122">FallbackSource</span><span class="sxs-lookup"><span data-stu-id="9583b-122">FallbackSource</span></span> | <span data-ttu-id="9583b-123">*(3.2 +)*  Eine Liste der Paketquellen überein, die als Zugriffe verwendet werden soll, für den Fall, dass das Paket nicht, in der primären gefunden wird oder Standardquelle.</span><span class="sxs-lookup"><span data-stu-id="9583b-123">*(3.2+)* A list of package sources to use as fallbacks in case the package isn't found in the primary or default source.</span></span> |
| <span data-ttu-id="9583b-124">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="9583b-124">ForceEnglishOutput</span></span> | <span data-ttu-id="9583b-125">*(3.5 +)*  Erzwingt nuget.exe über eine invariante Kultur Englisch-basierte ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9583b-125">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="9583b-126">Hilfe</span><span class="sxs-lookup"><span data-stu-id="9583b-126">Help</span></span> | <span data-ttu-id="9583b-127">Zeigt die Hilfe Informationen für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="9583b-127">Displays help information for the command.</span></span> |
| <span data-ttu-id="9583b-128">MSBuildPath</span><span class="sxs-lookup"><span data-stu-id="9583b-128">MSBuildPath</span></span> | <span data-ttu-id="9583b-129">*(4.0 und höher)*  Gibt den Pfad des MSBuild für die Verwendung mit dem Befehl, Vorrang vor `-MSBuildVersion`.</span><span class="sxs-lookup"><span data-stu-id="9583b-129">*(4.0+)* Specifies the path of MSBuild to use with the command, taking precedence over `-MSBuildVersion`.</span></span> |
| <span data-ttu-id="9583b-130">MSBuildVersion</span><span class="sxs-lookup"><span data-stu-id="9583b-130">MSBuildVersion</span></span> | <span data-ttu-id="9583b-131">*(3.2 +)*  Gibt die Version von MSBuild mit diesem Befehl verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="9583b-131">*(3.2+)* Specifies the version of MSBuild to be used with this command.</span></span> <span data-ttu-id="9583b-132">Unterstützte Werte sind 4, 12, 14, 15.</span><span class="sxs-lookup"><span data-stu-id="9583b-132">Supported values are 4, 12, 14, 15.</span></span> <span data-ttu-id="9583b-133">Standardmäßig werden die MSBuild-Datei in Ihrem Pfad abgerufen wird, wird standardmäßig andernfalls die neueste installierte Version von MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9583b-133">By default the MSBuild in your path is picked, otherwise it defaults to the highest installed version of MSBuild.</span></span> |
| <span data-ttu-id="9583b-134">NoCache</span><span class="sxs-lookup"><span data-stu-id="9583b-134">NoCache</span></span> | <span data-ttu-id="9583b-135">Verhindert, dass NuGet zwischengespeicherten Pakete verwenden.</span><span class="sxs-lookup"><span data-stu-id="9583b-135">Prevents NuGet from using cached packages.</span></span> <span data-ttu-id="9583b-136">Finden Sie unter [Verwaltung der globalen Pakete und der Cacheordner](../consume-packages/managing-the-global-packages-and-cache-folders.md).</span><span class="sxs-lookup"><span data-stu-id="9583b-136">See [Managing the global packages and cache folders](../consume-packages/managing-the-global-packages-and-cache-folders.md).</span></span> |
| <span data-ttu-id="9583b-137">NonInteractive</span><span class="sxs-lookup"><span data-stu-id="9583b-137">NonInteractive</span></span> | <span data-ttu-id="9583b-138">Unterdrückt aufforderungen für Benutzereingaben oder Bestätigungen an.</span><span class="sxs-lookup"><span data-stu-id="9583b-138">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="9583b-139">OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="9583b-139">OutputDirectory</span></span> | <span data-ttu-id="9583b-140">Gibt den Ordner, in dem Pakete installiert sind.</span><span class="sxs-lookup"><span data-stu-id="9583b-140">Specifies the folder in which packages are installed.</span></span> <span data-ttu-id="9583b-141">Wenn kein Ordner angegeben wird, wird der aktuelle Ordner verwendet.</span><span class="sxs-lookup"><span data-stu-id="9583b-141">If no folder is specified, the current folder is used.</span></span> <span data-ttu-id="9583b-142">Erforderlich, wenn die Wiederherstellung mit einem `packages.config` Datei, es sei denn, `PackagesDirectory` oder `SolutionDirectory` verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9583b-142">Required when restoring with a `packages.config` file unless `PackagesDirectory` or `SolutionDirectory` is used.</span></span>|
| <span data-ttu-id="9583b-143">PackageSaveMode</span><span class="sxs-lookup"><span data-stu-id="9583b-143">PackageSaveMode</span></span> | <span data-ttu-id="9583b-144">Gibt die Typen von Dateien nach der Paketinstallation speichern: einer der `nuspec`, `nupkg`, oder `nuspec;nupkg`.</span><span class="sxs-lookup"><span data-stu-id="9583b-144">Specifies the types of files to save after package installation: one of `nuspec`, `nupkg`, or `nuspec;nupkg`.</span></span> |
| <span data-ttu-id="9583b-145">PackagesDirectory</span><span class="sxs-lookup"><span data-stu-id="9583b-145">PackagesDirectory</span></span> | <span data-ttu-id="9583b-146">Wie in `OutputDirectory`.</span><span class="sxs-lookup"><span data-stu-id="9583b-146">Same as `OutputDirectory`.</span></span> <span data-ttu-id="9583b-147">Erforderlich, wenn die Wiederherstellung mit einem `packages.config` Datei, es sei denn, `OutputDirectory` oder `SolutionDirectory` verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9583b-147">Required when restoring with a `packages.config` file unless `OutputDirectory` or `SolutionDirectory` is used.</span></span> |
| <span data-ttu-id="9583b-148">Project2ProjectTimeOut</span><span class="sxs-lookup"><span data-stu-id="9583b-148">Project2ProjectTimeOut</span></span> | <span data-ttu-id="9583b-149">Timeout in Sekunden für das Auflösen von Verweisen zwischen Projekten.</span><span class="sxs-lookup"><span data-stu-id="9583b-149">Timeout in seconds for resolving project-to-project references.</span></span> |
| <span data-ttu-id="9583b-150">Rekursive</span><span class="sxs-lookup"><span data-stu-id="9583b-150">Recursive</span></span> | <span data-ttu-id="9583b-151">*(4.0 und höher)*  Stellt alle Verweise-Projekte für universelle Windows-Plattform und .NET Core-Projekte wieder her.</span><span class="sxs-lookup"><span data-stu-id="9583b-151">*(4.0+)* Restores all references projects for UWP and .NET Core projects.</span></span> <span data-ttu-id="9583b-152">Gilt nicht für Projekte mit `packages.config`.</span><span class="sxs-lookup"><span data-stu-id="9583b-152">Does not apply to projects using `packages.config`.</span></span> |
| <span data-ttu-id="9583b-153">RequireConsent</span><span class="sxs-lookup"><span data-stu-id="9583b-153">RequireConsent</span></span> | <span data-ttu-id="9583b-154">Überprüft, ob Pakete werden wiederhergestellt aktiviert wird vor dem Herunterladen und Installieren der Pakete.</span><span class="sxs-lookup"><span data-stu-id="9583b-154">Verifies that restoring packages is enabled before downloading and installing the packages.</span></span> <span data-ttu-id="9583b-155">Weitere Informationen finden Sie unter [Paketwiederherstellung](../consume-packages/package-restore.md).</span><span class="sxs-lookup"><span data-stu-id="9583b-155">For details, see [Package Restore](../consume-packages/package-restore.md).</span></span> |
| <span data-ttu-id="9583b-156">SolutionDirectory</span><span class="sxs-lookup"><span data-stu-id="9583b-156">SolutionDirectory</span></span> | <span data-ttu-id="9583b-157">Gibt den Projektmappenordner.</span><span class="sxs-lookup"><span data-stu-id="9583b-157">Specifies the solution folder.</span></span> <span data-ttu-id="9583b-158">Gilt nicht beim Wiederherstellen von Paketen für eine Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="9583b-158">Not valid when restoring packages for a solution.</span></span> <span data-ttu-id="9583b-159">Erforderlich, wenn die Wiederherstellung mit einem `packages.config` Datei, es sei denn, `PackagesDirectory` oder `OutputDirectory` verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9583b-159">Required when restoring with a `packages.config` file unless `PackagesDirectory` or `OutputDirectory` is used.</span></span> |
| <span data-ttu-id="9583b-160">Quelle</span><span class="sxs-lookup"><span data-stu-id="9583b-160">Source</span></span> | <span data-ttu-id="9583b-161">Gibt die Liste der Paketquellen (wie URLs) für die Verwendung für die Wiederherstellung an.</span><span class="sxs-lookup"><span data-stu-id="9583b-161">Specifies the list of package sources (as URLs) to use for the restore.</span></span> <span data-ttu-id="9583b-162">Wenn nicht angegeben, wird der Befehl verwendet die Quellen in Konfigurationsdateien bereitgestellt, finden Sie unter [NuGet Konfigurieren von Verhalten](../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="9583b-162">If omitted, the command uses the sources provided in configuration files, see [Configuring NuGet behavior](../consume-packages/configuring-nuget-behavior.md).</span></span> |
| <span data-ttu-id="9583b-163">Ausführlichkeit</span><span class="sxs-lookup"><span data-stu-id="9583b-163">Verbosity</span></span> |<span data-ttu-id="9583b-164">> Gibt die Anzahl der Details in der Ausgabe angezeigt: *normalen*, *stillen*, *ausführliche*.</span><span class="sxs-lookup"><span data-stu-id="9583b-164">>Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

<span data-ttu-id="9583b-165">Siehe auch [Umgebungsvariablen](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="9583b-165">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

## <a name="remarks"></a><span data-ttu-id="9583b-166">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9583b-166">Remarks</span></span>

<span data-ttu-id="9583b-167">Der Restore-Befehl führt die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="9583b-167">The restore command performs the following steps:</span></span>

1. <span data-ttu-id="9583b-168">Bestimmen Sie den Betriebsmodus des Restore-Befehl.</span><span class="sxs-lookup"><span data-stu-id="9583b-168">Determine the operation mode of the restore command.</span></span>

   | <span data-ttu-id="9583b-169">ProjectPath-Dateityp</span><span class="sxs-lookup"><span data-stu-id="9583b-169">projectPath file type</span></span> | <span data-ttu-id="9583b-170">Verhalten</span><span class="sxs-lookup"><span data-stu-id="9583b-170">Behavior</span></span> |
   | --- | --- |
   | <span data-ttu-id="9583b-171">Lösung (Ordner)</span><span class="sxs-lookup"><span data-stu-id="9583b-171">Solution (folder)</span></span> | <span data-ttu-id="9583b-172">NuGet sucht nach einem `.sln` Datei und verwendet, die andernfalls einen Fehler enthält.</span><span class="sxs-lookup"><span data-stu-id="9583b-172">NuGet looks for a `.sln` file and uses that if found; otherwise gives an error.</span></span> <span data-ttu-id="9583b-173">`(SolutionDir)\.nuget` Dient als Ordner ab.</span><span class="sxs-lookup"><span data-stu-id="9583b-173">`(SolutionDir)\.nuget` is used as the starting folder.</span></span> |
   | <span data-ttu-id="9583b-174">`.sln` Datei</span><span class="sxs-lookup"><span data-stu-id="9583b-174">`.sln` file</span></span> | <span data-ttu-id="9583b-175">Wiederherstellen von Paketen, die von der Lösung identifiziert; generiert einen Fehler, wenn `-SolutionDirectory` verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9583b-175">Restore packages identified by the solution; gives an error if `-SolutionDirectory` is used.</span></span> <span data-ttu-id="9583b-176">`$(SolutionDir)\.nuget` Dient als Ordner ab.</span><span class="sxs-lookup"><span data-stu-id="9583b-176">`$(SolutionDir)\.nuget` is used as the starting folder.</span></span> |
   | <span data-ttu-id="9583b-177">`packages.config` oder der Projektdatei</span><span class="sxs-lookup"><span data-stu-id="9583b-177">`packages.config` or project file</span></span> | <span data-ttu-id="9583b-178">Stellen Sie Pakete, die in der Datei, die zu beheben, und Installieren von Abhängigkeiten aufgelisteten wieder her.</span><span class="sxs-lookup"><span data-stu-id="9583b-178">Restore packages listed in the file, resolving and installing dependencies.</span></span> |
   | <span data-ttu-id="9583b-179">Andere Dateityp</span><span class="sxs-lookup"><span data-stu-id="9583b-179">Other file type</span></span> | <span data-ttu-id="9583b-180">Datei wird angenommen, ein `.sln` Datei wie oben beschrieben; Wenn es sich nicht um eine Lösung, die NuGet-gibt einen Fehler handelt.</span><span class="sxs-lookup"><span data-stu-id="9583b-180">File is assumed to be a `.sln` file as above; if it's not a solution, NuGet gives an error.</span></span> |
   | <span data-ttu-id="9583b-181">(ProjectPath nicht angegeben)</span><span class="sxs-lookup"><span data-stu-id="9583b-181">(projectPath not specified)</span></span> | <ul><li><span data-ttu-id="9583b-182">NuGet sucht nach berichtsprojektmappen-Dateien im aktuellen Ordner.</span><span class="sxs-lookup"><span data-stu-id="9583b-182">NuGet looks for solution files in the current folder.</span></span> <span data-ttu-id="9583b-183">Wenn eine einzelne Datei gefunden wird, verwendet wird, dass eine, Pakete wiederherzustellen. Wenn mehrere Lösungen gefunden werden, wird von NuGet ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="9583b-183">If a single file is found, that one is used to restore packages; if multiple solutions are found, NuGet gives an error.</span></span></li><li><span data-ttu-id="9583b-184">Wenn keine Lösungsdateien vorhanden sind, NuGet sucht eine `packages.config` dann verwendet, um das Wiederherstellen von Paketen.</span><span class="sxs-lookup"><span data-stu-id="9583b-184">If there are no solution files, NuGet looks for a `packages.config` and uses that to restore packages.</span></span></li><li><span data-ttu-id="9583b-185">Wenn keine Lösung oder `packages.config` Datei gefunden wird, NuGet generiert einen Fehler.</span><span class="sxs-lookup"><span data-stu-id="9583b-185">If no solution or `packages.config` file is found, NuGet gives an error.</span></span></ul> |

2. <span data-ttu-id="9583b-186">Bestimmen Sie den Ordner "Pakete" mithilfe der folgenden Prioritätsreihenfolge (NuGet generiert einen Fehler, wenn keiner dieser Ordner gefunden werden):</span><span class="sxs-lookup"><span data-stu-id="9583b-186">Determine the packages folder using the following priority order (NuGet gives an error if none of these folders are found):</span></span>

    - <span data-ttu-id="9583b-187">Mit angegebenen Ordner `-PackagesDirectory`.</span><span class="sxs-lookup"><span data-stu-id="9583b-187">The folder specified with `-PackagesDirectory`.</span></span>
    - <span data-ttu-id="9583b-188">Die `repositoryPath` Wert in `Nuget.Config`</span><span class="sxs-lookup"><span data-stu-id="9583b-188">The `repositoryPath` vale in `Nuget.Config`</span></span>
    - <span data-ttu-id="9583b-189">Den Ordner mit angegeben wird. `-SolutionDirectory`</span><span class="sxs-lookup"><span data-stu-id="9583b-189">The folder specified with `-SolutionDirectory`</span></span>
    - `$(SolutionDir)\packages`

3. <span data-ttu-id="9583b-190">Beim Wiederherstellen von Paketen für eine Projektmappe führt NuGet Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="9583b-190">When restoring packages for a solution, NuGet does the following:</span></span>
    - <span data-ttu-id="9583b-191">Lädt die Projektmappendatei.</span><span class="sxs-lookup"><span data-stu-id="9583b-191">Loads the solution file.</span></span>
    - <span data-ttu-id="9583b-192">Level-Lösungspakete abgelesen wiederhergestellt `$(SolutionDir)\.nuget\packages.config` in den `packages` Ordner.</span><span class="sxs-lookup"><span data-stu-id="9583b-192">Restores solution level packages listed in `$(SolutionDir)\.nuget\packages.config` into the `packages` folder.</span></span>
    - <span data-ttu-id="9583b-193">Wiederherstellen aufgelisteten Pakete `$(ProjectDir)\packages.config` in den `packages` Ordner.</span><span class="sxs-lookup"><span data-stu-id="9583b-193">Restore packages listed in `$(ProjectDir)\packages.config` into the `packages` folder.</span></span> <span data-ttu-id="9583b-194">Für jedes Paket angegeben wird, Wiederherstellen das Paket gleichzeitig, es sei denn, `-DisableParallelProcessing` angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="9583b-194">For each package specified, restore the package in parallel unless `-DisableParallelProcessing` is specified.</span></span>

## <a name="examples"></a><span data-ttu-id="9583b-195">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9583b-195">Examples</span></span>

```cli
# Restore packages for a solution file
nuget restore a.sln

# Restore packages for a solution file, using MSBuild version 14.0 to load the solution and its project(s)
nuget restore a.sln -MSBuildVersion 14

# Restore packages for a project's packages.config file, with the packages folder at the parent
nuget restore proj1\packages.config -PackagesDirectory ..\packages

# Restore packages for the solution in the current folder, specifying package sources
nuget restore -source "https://api.nuget.org/v3/index.json;https://www.myget.org/F/nuget"
```