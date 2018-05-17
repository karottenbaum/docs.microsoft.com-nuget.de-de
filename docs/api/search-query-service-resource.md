---
title: NuGet-API-Suche
description: Der Search-Dienst ermöglicht Clients zum Abfragen von Paketen von Schlüsselwort und Filterergebnisse auf bestimmte paketfelder.
author: joelverhagen
ms.author: jver
manager: skofman
ms.date: 10/26/2017
ms.topic: reference
ms.reviewer: kraigb
ms.openlocfilehash: 76600ee916305ee01ddfb675c83c184e980c5a42
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="search"></a><span data-ttu-id="dfb9b-103">Suchen</span><span class="sxs-lookup"><span data-stu-id="dfb9b-103">Search</span></span>

<span data-ttu-id="dfb9b-104">Es ist möglich, mithilfe der API V3 Paketquelle verfügbaren Pakete suchen.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-104">It is possible to search for packages available on a package source using the V3 API.</span></span> <span data-ttu-id="dfb9b-105">Ist die Ressource für die Suche verwendet die `SearchQueryService` Ressource gefunden, der [Dienst Index](service-index.md).</span><span class="sxs-lookup"><span data-stu-id="dfb9b-105">The resource used for searching is the `SearchQueryService` resource found in the [service index](service-index.md).</span></span>

## <a name="versioning"></a><span data-ttu-id="dfb9b-106">Versionskontrolle</span><span class="sxs-lookup"><span data-stu-id="dfb9b-106">Versioning</span></span>

<span data-ttu-id="dfb9b-107">Die folgenden `@type` Werte werden verwendet:</span><span class="sxs-lookup"><span data-stu-id="dfb9b-107">The following `@type` values are used:</span></span>

<span data-ttu-id="dfb9b-108">@type-Wert</span><span class="sxs-lookup"><span data-stu-id="dfb9b-108">@type value</span></span>                   | <span data-ttu-id="dfb9b-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dfb9b-109">Notes</span></span>
----------------------------- | -----
<span data-ttu-id="dfb9b-110">SearchQueryService</span><span class="sxs-lookup"><span data-stu-id="dfb9b-110">SearchQueryService</span></span>            | <span data-ttu-id="dfb9b-111">Die erste Version</span><span class="sxs-lookup"><span data-stu-id="dfb9b-111">The initial release</span></span>
<span data-ttu-id="dfb9b-112">SearchQueryService/3.0.0-beta</span><span class="sxs-lookup"><span data-stu-id="dfb9b-112">SearchQueryService/3.0.0-beta</span></span> | <span data-ttu-id="dfb9b-113">Alias der `SearchQueryService`</span><span class="sxs-lookup"><span data-stu-id="dfb9b-113">Alias of `SearchQueryService`</span></span>
<span data-ttu-id="dfb9b-114">SearchQueryService/3.0.0-rc</span><span class="sxs-lookup"><span data-stu-id="dfb9b-114">SearchQueryService/3.0.0-rc</span></span>   | <span data-ttu-id="dfb9b-115">Alias der `SearchQueryService`</span><span class="sxs-lookup"><span data-stu-id="dfb9b-115">Alias of `SearchQueryService`</span></span>

## <a name="base-url"></a><span data-ttu-id="dfb9b-116">Basis-URL</span><span class="sxs-lookup"><span data-stu-id="dfb9b-116">Base URL</span></span>

<span data-ttu-id="dfb9b-117">Die base-URL für die folgende API wird der Wert von der `@id` mit einem der oben genannten Ressource verknüpfte Eigenschaft `@type` Werte.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-117">The base URL for the following API is the value of the `@id` property associated with one of the aforementioned resource `@type` values.</span></span> <span data-ttu-id="dfb9b-118">Im folgenden Dokument Platzhalter für die Basis-URL `{@id}` verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-118">In the following document, the placeholder base URL `{@id}` will be used.</span></span>

## <a name="http-methods"></a><span data-ttu-id="dfb9b-119">HTTP-Methoden</span><span class="sxs-lookup"><span data-stu-id="dfb9b-119">HTTP methods</span></span>

<span data-ttu-id="dfb9b-120">Alle URLs, die bei der Unterstützung der Registrierung-Ressource gefunden, die HTTP-Methoden `GET` und `HEAD`.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-120">All URLs found in the registration resource support the HTTP methods `GET` and `HEAD`.</span></span>

## <a name="search-for-packages"></a><span data-ttu-id="dfb9b-121">Suchen Sie nach Pakete</span><span class="sxs-lookup"><span data-stu-id="dfb9b-121">Search for packages</span></span>

<span data-ttu-id="dfb9b-122">Die Such-API ermöglicht einem Client Abfrage für eine Seite der Pakete, die eine Abfrage für die angegebenen Suchkriterien entsprechen.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-122">The search API allows a client to query for a page of packages matching a specified search query.</span></span> <span data-ttu-id="dfb9b-123">Die Interpretation der Suchabfrage (z. B. die Tokenisierung der Suchbegriffe) richtet sich nach der Implementierung, aber der allgemeinen Annahme ist, dass die Suchabfrage verwendet wird, für den Abgleich von Paket-IDs, Titel, Beschreibungen und Tags.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-123">The interpretation of the search query (e.g. the tokenization of the search terms) is determined by the server implementation but the general expectation is that the search query is used for matching package IDs, titles, descriptions, and tags.</span></span> <span data-ttu-id="dfb9b-124">Andere Metadatenfelder Paket möglicherweise ebenfalls berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-124">Other package metadata fields may also be considered.</span></span>

<span data-ttu-id="dfb9b-125">Eine nicht aufgeführte Paket sollte nie in den Suchergebnissen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-125">An unlisted package should never appear in search results.</span></span>

    GET {@id}?q={QUERY}&skip={SKIP}&take={TAKE}&prerelease={PRERELEASE}&semVerLevel={SEMVERLEVEL}

### <a name="request-parameters"></a><span data-ttu-id="dfb9b-126">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="dfb9b-126">Request parameters</span></span>

<span data-ttu-id="dfb9b-127">name</span><span class="sxs-lookup"><span data-stu-id="dfb9b-127">Name</span></span>        | <span data-ttu-id="dfb9b-128">In</span><span class="sxs-lookup"><span data-stu-id="dfb9b-128">In</span></span>     | <span data-ttu-id="dfb9b-129">Typ</span><span class="sxs-lookup"><span data-stu-id="dfb9b-129">Type</span></span>    | <span data-ttu-id="dfb9b-130">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="dfb9b-130">Required</span></span> | <span data-ttu-id="dfb9b-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dfb9b-131">Notes</span></span>
----------- | ------ | ------- | -------- | -----
<span data-ttu-id="dfb9b-132">q</span><span class="sxs-lookup"><span data-stu-id="dfb9b-132">q</span></span>           | <span data-ttu-id="dfb9b-133">URL</span><span class="sxs-lookup"><span data-stu-id="dfb9b-133">URL</span></span>    | <span data-ttu-id="dfb9b-134">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-134">string</span></span>  | <span data-ttu-id="dfb9b-135">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-135">no</span></span>       | <span data-ttu-id="dfb9b-136">Suchbegriffe zur Filter-Pakete</span><span class="sxs-lookup"><span data-stu-id="dfb9b-136">The search terms to used to filter packages</span></span>
<span data-ttu-id="dfb9b-137">überspringen</span><span class="sxs-lookup"><span data-stu-id="dfb9b-137">skip</span></span>        | <span data-ttu-id="dfb9b-138">URL</span><span class="sxs-lookup"><span data-stu-id="dfb9b-138">URL</span></span>    | <span data-ttu-id="dfb9b-139">Ganze Zahl</span><span class="sxs-lookup"><span data-stu-id="dfb9b-139">integer</span></span> | <span data-ttu-id="dfb9b-140">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-140">no</span></span>       | <span data-ttu-id="dfb9b-141">Die Anzahl der Ergebnisse für die Paginierung überspringen</span><span class="sxs-lookup"><span data-stu-id="dfb9b-141">The number of results to skip, for pagination</span></span>
<span data-ttu-id="dfb9b-142">Take</span><span class="sxs-lookup"><span data-stu-id="dfb9b-142">take</span></span>        | <span data-ttu-id="dfb9b-143">URL</span><span class="sxs-lookup"><span data-stu-id="dfb9b-143">URL</span></span>    | <span data-ttu-id="dfb9b-144">Ganze Zahl</span><span class="sxs-lookup"><span data-stu-id="dfb9b-144">integer</span></span> | <span data-ttu-id="dfb9b-145">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-145">no</span></span>       | <span data-ttu-id="dfb9b-146">Die Anzahl der zurückzugebenden Ergebnisseite, für die Paginierung</span><span class="sxs-lookup"><span data-stu-id="dfb9b-146">The number of results to return, for pagination</span></span>
<span data-ttu-id="dfb9b-147">Vorabversion</span><span class="sxs-lookup"><span data-stu-id="dfb9b-147">prerelease</span></span>  | <span data-ttu-id="dfb9b-148">URL</span><span class="sxs-lookup"><span data-stu-id="dfb9b-148">URL</span></span>    | <span data-ttu-id="dfb9b-149">boolean</span><span class="sxs-lookup"><span data-stu-id="dfb9b-149">boolean</span></span> | <span data-ttu-id="dfb9b-150">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-150">no</span></span>       | <span data-ttu-id="dfb9b-151">`true` oder `false` bestimmen, ob enthalten [Vorabversion Pakete](../create-packages/prerelease-packages.md)</span><span class="sxs-lookup"><span data-stu-id="dfb9b-151">`true` or `false` determining whether to include [pre-release packages](../create-packages/prerelease-packages.md)</span></span>
<span data-ttu-id="dfb9b-152">semVerLevel</span><span class="sxs-lookup"><span data-stu-id="dfb9b-152">semVerLevel</span></span> | <span data-ttu-id="dfb9b-153">URL</span><span class="sxs-lookup"><span data-stu-id="dfb9b-153">URL</span></span>    | <span data-ttu-id="dfb9b-154">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-154">string</span></span>  | <span data-ttu-id="dfb9b-155">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-155">no</span></span>       | <span data-ttu-id="dfb9b-156">Eine Versionszeichenfolge SemVer 1.0.0</span><span class="sxs-lookup"><span data-stu-id="dfb9b-156">A SemVer 1.0.0 version string</span></span> 

<span data-ttu-id="dfb9b-157">Die Suchabfrage `q` wird analysiert, die in einer Weise, die durch die Implementierung definiert ist.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-157">The search query `q` is parsed in a manner that is defined by the server implementation.</span></span> <span data-ttu-id="dfb9b-158">NuGet.org unterstützt Standardfilter auf eine [Vielzahl von Feldern](../consume-packages/finding-and-choosing-packages.md#search-syntax).</span><span class="sxs-lookup"><span data-stu-id="dfb9b-158">nuget.org supports basic filtering on a [variety of fields](../consume-packages/finding-and-choosing-packages.md#search-syntax).</span></span> <span data-ttu-id="dfb9b-159">Wenn kein `q` angegeben wird, alle Pakete, innerhalb der Grenzen, die durch überspringen, und ergreifen Sie auferlegt, zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-159">If no `q` is provided, all packages should be returned, within the boundaries imposed by skip and take.</span></span> <span data-ttu-id="dfb9b-160">Dadurch wird die Registerkarte "Durchsuchen" in der NuGet-Visual Studio-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-160">This enables the "Browse" tab in the NuGet Visual Studio experience.</span></span>

<span data-ttu-id="dfb9b-161">Die `skip` Parameter beträgt standardmäßig 0.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-161">The `skip` parameter defaults to 0.</span></span>

<span data-ttu-id="dfb9b-162">Die `take` Parameter muss eine ganze Zahl größer als 0 (null) sein.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-162">The `take` parameter should be an integer greater than zero.</span></span> <span data-ttu-id="dfb9b-163">Die Implementierung der Server kann einen maximalen Wert verursachen.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-163">The server implementation may impose a maximum value.</span></span>

<span data-ttu-id="dfb9b-164">Wenn `prerelease` nicht angegeben wird, Vorabversion Paketen ausgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-164">If `prerelease` is not provided, pre-release packages are excluded.</span></span>

<span data-ttu-id="dfb9b-165">Die `semVerLevel` Query-Parameter wird verwendet, um abonnieren [SemVer 2.0.0 Pakete](https://github.com/NuGet/Home/wiki/SemVer2-support-for-nuget.org-%28server-side%29#identifying-semver-v200-packages).</span><span class="sxs-lookup"><span data-stu-id="dfb9b-165">The `semVerLevel` query parameter is used to opt-in to [SemVer 2.0.0 packages](https://github.com/NuGet/Home/wiki/SemVer2-support-for-nuget.org-%28server-side%29#identifying-semver-v200-packages).</span></span>
<span data-ttu-id="dfb9b-166">Wenn dieser Parameter ausgeschlossen ist, werden nur Pakete mit SemVer 1.0.0 kompatible Versionen zurückgegeben (mit der [standard NuGet Versioning](../reference/package-versioning.md) Vorsichtsmaßnahmen, z. B. Versionszeichenfolgen mit 4 Einheiten für ganze Zahl).</span><span class="sxs-lookup"><span data-stu-id="dfb9b-166">If this query parameter is excluded, only packages with SemVer 1.0.0 compatible versions will be returned (with the [standard NuGet versioning](../reference/package-versioning.md) caveats, such as version strings with 4 integer pieces).</span></span>
<span data-ttu-id="dfb9b-167">Wenn `semVerLevel=2.0.0` angegeben wird, SemVer 1.0.0 und SemVer 2.0.0 kompatibel Pakete zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-167">If `semVerLevel=2.0.0` is provided, both SemVer 1.0.0 and SemVer 2.0.0 compatible packages will be returned.</span></span> <span data-ttu-id="dfb9b-168">Finden Sie unter der [SemVer 2.0.0-Unterstützung für nuget.org](https://github.com/NuGet/Home/wiki/SemVer2-support-for-nuget.org-%28server-side%29) für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-168">See the [SemVer 2.0.0 support for nuget.org](https://github.com/NuGet/Home/wiki/SemVer2-support-for-nuget.org-%28server-side%29) for more information.</span></span>

### <a name="response"></a><span data-ttu-id="dfb9b-169">Antwort</span><span class="sxs-lookup"><span data-stu-id="dfb9b-169">Response</span></span>

<span data-ttu-id="dfb9b-170">Die Antwort ist, enthält bis zu JSON-Dokument `take` Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-170">The response is JSON document containing up to `take` search results.</span></span> <span data-ttu-id="dfb9b-171">Suchergebnisse werden nach Paket-ID gruppiert.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-171">Search results are grouped by package ID.</span></span>

<span data-ttu-id="dfb9b-172">Der Stamm-JSON-Objekt hat die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="dfb9b-172">The root JSON object has the following properties:</span></span>

<span data-ttu-id="dfb9b-173">name</span><span class="sxs-lookup"><span data-stu-id="dfb9b-173">Name</span></span>      | <span data-ttu-id="dfb9b-174">Typ</span><span class="sxs-lookup"><span data-stu-id="dfb9b-174">Type</span></span>             | <span data-ttu-id="dfb9b-175">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="dfb9b-175">Required</span></span> | <span data-ttu-id="dfb9b-176">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dfb9b-176">Notes</span></span>
--------- | ---------------- | -------- | -----
<span data-ttu-id="dfb9b-177">totalHits</span><span class="sxs-lookup"><span data-stu-id="dfb9b-177">totalHits</span></span> | <span data-ttu-id="dfb9b-178">Ganze Zahl</span><span class="sxs-lookup"><span data-stu-id="dfb9b-178">integer</span></span>          | <span data-ttu-id="dfb9b-179">ja</span><span class="sxs-lookup"><span data-stu-id="dfb9b-179">yes</span></span>      | <span data-ttu-id="dfb9b-180">Die Gesamtzahl der Übereinstimmungen, Basiseigenschaft `skip` und `take`</span><span class="sxs-lookup"><span data-stu-id="dfb9b-180">The total number of matches, disregarding `skip` and `take`</span></span>
<span data-ttu-id="dfb9b-181">Daten</span><span class="sxs-lookup"><span data-stu-id="dfb9b-181">data</span></span>      | <span data-ttu-id="dfb9b-182">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="dfb9b-182">array of objects</span></span> | <span data-ttu-id="dfb9b-183">ja</span><span class="sxs-lookup"><span data-stu-id="dfb9b-183">yes</span></span>      | <span data-ttu-id="dfb9b-184">Die Suchergebnisse abgeglichen, die von der Anforderung</span><span class="sxs-lookup"><span data-stu-id="dfb9b-184">The search results matched by the request</span></span>

### <a name="search-result"></a><span data-ttu-id="dfb9b-185">Suchergebnis</span><span class="sxs-lookup"><span data-stu-id="dfb9b-185">Search result</span></span>

<span data-ttu-id="dfb9b-186">Jedes Element in der `data` Array ist ein JSON-Objekt, bestehend aus einer Gruppe von Paketversionen, die gemeinsame Nutzung der gleichen Paket-ID.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-186">Each item in the `data` array is a JSON object comprised of a group of package versions sharing the same package ID.</span></span>
<span data-ttu-id="dfb9b-187">Das Objekt hat die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="dfb9b-187">The object has the following properties:</span></span>

<span data-ttu-id="dfb9b-188">name</span><span class="sxs-lookup"><span data-stu-id="dfb9b-188">Name</span></span>           | <span data-ttu-id="dfb9b-189">Typ</span><span class="sxs-lookup"><span data-stu-id="dfb9b-189">Type</span></span>                       | <span data-ttu-id="dfb9b-190">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="dfb9b-190">Required</span></span> | <span data-ttu-id="dfb9b-191">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dfb9b-191">Notes</span></span>
-------------- | -------------------------- | -------- | -----
<span data-ttu-id="dfb9b-192">ID</span><span class="sxs-lookup"><span data-stu-id="dfb9b-192">id</span></span>             | <span data-ttu-id="dfb9b-193">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-193">string</span></span>                     | <span data-ttu-id="dfb9b-194">ja</span><span class="sxs-lookup"><span data-stu-id="dfb9b-194">yes</span></span>      | <span data-ttu-id="dfb9b-195">Die ID des übereinstimmenden Pakets</span><span class="sxs-lookup"><span data-stu-id="dfb9b-195">The ID of the matched package</span></span>
<span data-ttu-id="dfb9b-196">Version</span><span class="sxs-lookup"><span data-stu-id="dfb9b-196">version</span></span>        | <span data-ttu-id="dfb9b-197">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-197">string</span></span>                     | <span data-ttu-id="dfb9b-198">ja</span><span class="sxs-lookup"><span data-stu-id="dfb9b-198">yes</span></span>      | <span data-ttu-id="dfb9b-199">Die vollständige SemVer 2.0.0 Versionszeichenfolge des Pakets (konnte die Build-Metadaten enthalten)</span><span class="sxs-lookup"><span data-stu-id="dfb9b-199">The full SemVer 2.0.0 version string of the package (could contain build metadata)</span></span>
<span data-ttu-id="dfb9b-200">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="dfb9b-200">description</span></span>    | <span data-ttu-id="dfb9b-201">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-201">string</span></span>                     | <span data-ttu-id="dfb9b-202">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-202">no</span></span>       | 
<span data-ttu-id="dfb9b-203">Versionen</span><span class="sxs-lookup"><span data-stu-id="dfb9b-203">versions</span></span>       | <span data-ttu-id="dfb9b-204">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="dfb9b-204">array of objects</span></span>           | <span data-ttu-id="dfb9b-205">ja</span><span class="sxs-lookup"><span data-stu-id="dfb9b-205">yes</span></span>      | <span data-ttu-id="dfb9b-206">Alle Versionen der übereinstimmenden Paket die `prerelease` Parameter</span><span class="sxs-lookup"><span data-stu-id="dfb9b-206">All of the versions of the package matching the `prerelease` parameter</span></span>
<span data-ttu-id="dfb9b-207">authors</span><span class="sxs-lookup"><span data-stu-id="dfb9b-207">authors</span></span>        | <span data-ttu-id="dfb9b-208">Zeichenfolge oder ein Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="dfb9b-208">string or array of strings</span></span> | <span data-ttu-id="dfb9b-209">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-209">no</span></span>       | 
<span data-ttu-id="dfb9b-210">iconUrl</span><span class="sxs-lookup"><span data-stu-id="dfb9b-210">iconUrl</span></span>        | <span data-ttu-id="dfb9b-211">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-211">string</span></span>                     | <span data-ttu-id="dfb9b-212">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-212">no</span></span>       | 
<span data-ttu-id="dfb9b-213">licenseUrl</span><span class="sxs-lookup"><span data-stu-id="dfb9b-213">licenseUrl</span></span>     | <span data-ttu-id="dfb9b-214">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-214">string</span></span>                     | <span data-ttu-id="dfb9b-215">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-215">no</span></span>       | 
<span data-ttu-id="dfb9b-216">owners</span><span class="sxs-lookup"><span data-stu-id="dfb9b-216">owners</span></span>         | <span data-ttu-id="dfb9b-217">Zeichenfolge oder ein Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="dfb9b-217">string or array of strings</span></span> | <span data-ttu-id="dfb9b-218">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-218">no</span></span>       | 
<span data-ttu-id="dfb9b-219">projectUrl</span><span class="sxs-lookup"><span data-stu-id="dfb9b-219">projectUrl</span></span>     | <span data-ttu-id="dfb9b-220">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-220">string</span></span>                     | <span data-ttu-id="dfb9b-221">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-221">no</span></span>       | 
<span data-ttu-id="dfb9b-222">Registrierung</span><span class="sxs-lookup"><span data-stu-id="dfb9b-222">registration</span></span>   | <span data-ttu-id="dfb9b-223">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-223">string</span></span>                     | <span data-ttu-id="dfb9b-224">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-224">no</span></span>       | <span data-ttu-id="dfb9b-225">Die absolute URL an die zugeordnete [Registrierung Index](registration-base-url-resource.md#registration-index)</span><span class="sxs-lookup"><span data-stu-id="dfb9b-225">The absolute URL to the associated [registration index](registration-base-url-resource.md#registration-index)</span></span>
<span data-ttu-id="dfb9b-226">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="dfb9b-226">summary</span></span>        | <span data-ttu-id="dfb9b-227">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-227">string</span></span>                     | <span data-ttu-id="dfb9b-228">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-228">no</span></span>       | 
<span data-ttu-id="dfb9b-229">Tags</span><span class="sxs-lookup"><span data-stu-id="dfb9b-229">tags</span></span>           | <span data-ttu-id="dfb9b-230">Zeichenfolge oder ein Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="dfb9b-230">string or array of strings</span></span> | <span data-ttu-id="dfb9b-231">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-231">no</span></span>       | 
<span data-ttu-id="dfb9b-232">Titel</span><span class="sxs-lookup"><span data-stu-id="dfb9b-232">title</span></span>          | <span data-ttu-id="dfb9b-233">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-233">string</span></span>                     | <span data-ttu-id="dfb9b-234">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-234">no</span></span>       | 
<span data-ttu-id="dfb9b-235">totalDownloads</span><span class="sxs-lookup"><span data-stu-id="dfb9b-235">totalDownloads</span></span> | <span data-ttu-id="dfb9b-236">Ganze Zahl</span><span class="sxs-lookup"><span data-stu-id="dfb9b-236">integer</span></span>                    | <span data-ttu-id="dfb9b-237">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-237">no</span></span>       | <span data-ttu-id="dfb9b-238">Dieser Wert abgeleitet werden kann, durch die Summe der Downloads in den `versions` Array</span><span class="sxs-lookup"><span data-stu-id="dfb9b-238">This value can be inferred by the sum of downloads in the `versions` array</span></span>
<span data-ttu-id="dfb9b-239">Überprüft</span><span class="sxs-lookup"><span data-stu-id="dfb9b-239">verified</span></span>       | <span data-ttu-id="dfb9b-240">boolean</span><span class="sxs-lookup"><span data-stu-id="dfb9b-240">boolean</span></span>                    | <span data-ttu-id="dfb9b-241">Nein</span><span class="sxs-lookup"><span data-stu-id="dfb9b-241">no</span></span>       | <span data-ttu-id="dfb9b-242">Gibt an, ob das Paket ist JSON-Typ Boolean [überprüft](../reference/id-prefix-reservation.md)</span><span class="sxs-lookup"><span data-stu-id="dfb9b-242">A JSON boolean indicating whether the package is [verified](../reference/id-prefix-reservation.md)</span></span>

<span data-ttu-id="dfb9b-243">Auf nuget.org ist ein überprüfter Paket eines, das eine Paket-ID entsprechen ein reserviertes ID-Präfix wurde und im Besitz einer reservierten Namespace-Besitzer an.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-243">On nuget.org, a verified package is one which has a package ID matching a reserved ID prefix and owned by one of the reserved namespace's owners.</span></span> <span data-ttu-id="dfb9b-244">Weitere Informationen finden Sie unter der [Dokumentation zur ID-Präfix Reservierung](../reference/id-prefix-reservation.md).</span><span class="sxs-lookup"><span data-stu-id="dfb9b-244">For more information, see the [documentation about ID prefix reservation](../reference/id-prefix-reservation.md).</span></span>

<span data-ttu-id="dfb9b-245">Die Metadaten in die Suche-Ergebnisobjekt enthaltenen stammt aus der aktuellen Paketversion.</span><span class="sxs-lookup"><span data-stu-id="dfb9b-245">The metadata contained in the search result object is taken from the latest package version.</span></span> <span data-ttu-id="dfb9b-246">Jedes Element in der `versions` Array ist ein JSON-Objekt mit den folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="dfb9b-246">Each item in the `versions` array is a JSON object with the following properties:</span></span>

<span data-ttu-id="dfb9b-247">name</span><span class="sxs-lookup"><span data-stu-id="dfb9b-247">Name</span></span>      | <span data-ttu-id="dfb9b-248">Typ</span><span class="sxs-lookup"><span data-stu-id="dfb9b-248">Type</span></span>    | <span data-ttu-id="dfb9b-249">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="dfb9b-249">Required</span></span> | <span data-ttu-id="dfb9b-250">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dfb9b-250">Notes</span></span>
--------- | ------- | -------- | -----
@id       | <span data-ttu-id="dfb9b-251">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-251">string</span></span>  | <span data-ttu-id="dfb9b-252">ja</span><span class="sxs-lookup"><span data-stu-id="dfb9b-252">yes</span></span>      | <span data-ttu-id="dfb9b-253">Die absolute URL an die zugeordnete [Registrierung Blattebene](registration-base-url-resource.md#registration-leaf)</span><span class="sxs-lookup"><span data-stu-id="dfb9b-253">The absolute URL to the associated [registration leaf](registration-base-url-resource.md#registration-leaf)</span></span>
<span data-ttu-id="dfb9b-254">Version</span><span class="sxs-lookup"><span data-stu-id="dfb9b-254">version</span></span>   | <span data-ttu-id="dfb9b-255">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="dfb9b-255">string</span></span>  | <span data-ttu-id="dfb9b-256">ja</span><span class="sxs-lookup"><span data-stu-id="dfb9b-256">yes</span></span>      | <span data-ttu-id="dfb9b-257">Die vollständige SemVer 2.0.0 Versionszeichenfolge des Pakets (konnte die Build-Metadaten enthalten)</span><span class="sxs-lookup"><span data-stu-id="dfb9b-257">The full SemVer 2.0.0 version string of the package (could contain build metadata)</span></span>
<span data-ttu-id="dfb9b-258">Downloads</span><span class="sxs-lookup"><span data-stu-id="dfb9b-258">downloads</span></span> | <span data-ttu-id="dfb9b-259">Ganze Zahl</span><span class="sxs-lookup"><span data-stu-id="dfb9b-259">integer</span></span> | <span data-ttu-id="dfb9b-260">ja</span><span class="sxs-lookup"><span data-stu-id="dfb9b-260">yes</span></span>      | <span data-ttu-id="dfb9b-261">Die Anzahl der Downloads für diese bestimmte Paketversion</span><span class="sxs-lookup"><span data-stu-id="dfb9b-261">The number of downloads for this specific package version</span></span>

### <a name="sample-request"></a><span data-ttu-id="dfb9b-262">Beispielanforderung</span><span class="sxs-lookup"><span data-stu-id="dfb9b-262">Sample request</span></span>

    GET https://api-v2v3search-0.nuget.org/query?q=NuGet.Versioning&prerelease=false

### <a name="sample-response"></a><span data-ttu-id="dfb9b-263">Beispielantwort</span><span class="sxs-lookup"><span data-stu-id="dfb9b-263">Sample response</span></span>

[!code-JSON [search-result.json](./_data/search-result.json)]