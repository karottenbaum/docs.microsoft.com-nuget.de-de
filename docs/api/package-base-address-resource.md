---
title: Paketinhalt, NuGet-API
description: Die Basisadresse des Pakets ist eine einfache Schnittstelle zum Abrufen der des Pakets selbst.
author: joelverhagen
ms.author: jver
manager: skofman
ms.date: 10/26/2017
ms.topic: reference
ms.reviewer: kraigb
ms.openlocfilehash: a6ac40368f30d33f35d4ca0b6cc18ce4bd6efee5
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="package-content"></a><span data-ttu-id="ecc1b-103">Paketinhalt</span><span class="sxs-lookup"><span data-stu-id="ecc1b-103">Package Content</span></span>

<span data-ttu-id="ecc1b-104">Es ist möglich, generieren eine URL für ein beliebiges Paket Inhalte (der .nupkg-Datei) mithilfe der V3-API abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-104">It is possible to generate a URL to fetch an arbitrary package's content (the .nupkg file) using the V3 API.</span></span> <span data-ttu-id="ecc1b-105">Die Ressource für das Abrufen von Paketinhalt verwendet die `PackageBaseAddress` Ressource gefunden, der [Dienst Index](service-index.md).</span><span class="sxs-lookup"><span data-stu-id="ecc1b-105">The resource used for fetching package content is the `PackageBaseAddress` resource found in the [service index](service-index.md).</span></span> <span data-ttu-id="ecc1b-106">Diese Ressource ermöglicht auch die Ermittlung aller Versionen eines Pakets aufgeführt oder nicht aufgeführte.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-106">This resource also enables discovery of all versions of a package, listed or unlisted.</span></span>

<span data-ttu-id="ecc1b-107">Diese Ressource wird häufig als entweder die "Paket Basisadresse" oder "Flatfile-Container" bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-107">This resource is commonly referred to as either the "package base address" or as the "flat container".</span></span>

## <a name="versioning"></a><span data-ttu-id="ecc1b-108">Versionskontrolle</span><span class="sxs-lookup"><span data-stu-id="ecc1b-108">Versioning</span></span>

<span data-ttu-id="ecc1b-109">Die folgenden `@type` Wert wird verwendet:</span><span class="sxs-lookup"><span data-stu-id="ecc1b-109">The following `@type` value is used:</span></span>

<span data-ttu-id="ecc1b-110">@type-Wert</span><span class="sxs-lookup"><span data-stu-id="ecc1b-110">@type value</span></span>              | <span data-ttu-id="ecc1b-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ecc1b-111">Notes</span></span>
------------------------ | -----
<span data-ttu-id="ecc1b-112">PackageBaseAddress/3.0.0</span><span class="sxs-lookup"><span data-stu-id="ecc1b-112">PackageBaseAddress/3.0.0</span></span> | <span data-ttu-id="ecc1b-113">Die erste Version</span><span class="sxs-lookup"><span data-stu-id="ecc1b-113">The initial release</span></span>

## <a name="base-url"></a><span data-ttu-id="ecc1b-114">Basis-URL</span><span class="sxs-lookup"><span data-stu-id="ecc1b-114">Base URL</span></span>

<span data-ttu-id="ecc1b-115">Die base-URL für die folgenden APIs ist der Wert der `@id` Eigenschaft, die zuvor erwähnten zur Ressource zugeordnete `@type` Wert.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-115">The base URL for the following APIs is the value of the `@id` property associated with the aforementioned resource `@type` value.</span></span> <span data-ttu-id="ecc1b-116">Im folgenden Dokument Platzhalter für die Basis-URL `{@id}` verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-116">In the following document, the placeholder base URL `{@id}` will be used.</span></span>

## <a name="http-methods"></a><span data-ttu-id="ecc1b-117">HTTP-Methoden</span><span class="sxs-lookup"><span data-stu-id="ecc1b-117">HTTP methods</span></span>

<span data-ttu-id="ecc1b-118">Alle URLs, die bei der Unterstützung der Registrierung-Ressource gefunden, die HTTP-Methoden `GET` und `HEAD`.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-118">All URLs found in the registration resource support the HTTP methods `GET` and `HEAD`.</span></span>

## <a name="enumerate-package-versions"></a><span data-ttu-id="ecc1b-119">Auflisten von Paketversionen</span><span class="sxs-lookup"><span data-stu-id="ecc1b-119">Enumerate package versions</span></span>

<span data-ttu-id="ecc1b-120">Wenn der Client bekannt eine Paket-ID ist und möchte Ermitteln der Paket-Versionen des Pakets die Quelle verfügbar ist, der Client eine vorhersagbare URL zum Aufzählen aller Paketversionen erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-120">If the client knows a package ID and wants to discover which package versions the package source has available, the client can construct a predictable URL to enumerate all package versions.</span></span> <span data-ttu-id="ecc1b-121">Diese Liste ist dafür vorgesehen, "Verzeichnisliste" werden für die unten aufgeführten Content Paket-API.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-121">This list is meant to be a "directory listing" for the package content API mentioned below.</span></span>

> [!Note]
> <span data-ttu-id="ecc1b-122">Diese Liste enthält beide Paketversionen aufgeführt und nicht aufgeführte.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-122">This list contains both listed and unlisted package versions.</span></span>

    GET {@id}/{LOWER_ID}/index.json

### <a name="request-parameters"></a><span data-ttu-id="ecc1b-123">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ecc1b-123">Request parameters</span></span>

<span data-ttu-id="ecc1b-124">name</span><span class="sxs-lookup"><span data-stu-id="ecc1b-124">Name</span></span>     | <span data-ttu-id="ecc1b-125">In</span><span class="sxs-lookup"><span data-stu-id="ecc1b-125">In</span></span>     | <span data-ttu-id="ecc1b-126">Typ</span><span class="sxs-lookup"><span data-stu-id="ecc1b-126">Type</span></span>    | <span data-ttu-id="ecc1b-127">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ecc1b-127">Required</span></span> | <span data-ttu-id="ecc1b-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ecc1b-128">Notes</span></span>
-------- | ------ | ------- | -------- | -----
<span data-ttu-id="ecc1b-129">LOWER_ID</span><span class="sxs-lookup"><span data-stu-id="ecc1b-129">LOWER_ID</span></span> | <span data-ttu-id="ecc1b-130">URL</span><span class="sxs-lookup"><span data-stu-id="ecc1b-130">URL</span></span>    | <span data-ttu-id="ecc1b-131">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ecc1b-131">string</span></span>  | <span data-ttu-id="ecc1b-132">ja</span><span class="sxs-lookup"><span data-stu-id="ecc1b-132">yes</span></span>      | <span data-ttu-id="ecc1b-133">Die Paket-ID Kleinbuchstaben</span><span class="sxs-lookup"><span data-stu-id="ecc1b-133">The package ID, lowercase</span></span>

<span data-ttu-id="ecc1b-134">Die `LOWER_ID` Wert ist die gewünschte Paket-ID, die klein gemäß den Vergleichsregeln von implementiert. NET [ `System.String.ToLowerInvariant()` ](/dotnet/api/system.string.tolowerinvariant?view=netstandard-2.0#System_String_ToLowerInvariant) Methode.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-134">The `LOWER_ID` value is the desired package ID lowercased using the rules implemented by .NET's [`System.String.ToLowerInvariant()`](/dotnet/api/system.string.tolowerinvariant?view=netstandard-2.0#System_String_ToLowerInvariant) method.</span></span>

### <a name="response"></a><span data-ttu-id="ecc1b-135">Antwort</span><span class="sxs-lookup"><span data-stu-id="ecc1b-135">Response</span></span>

<span data-ttu-id="ecc1b-136">Wenn die Paketquelle keine Versionen der bereitgestellte Paket-ID verfügt, wird ein Statuscode "404" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-136">If the package source has no versions of the provided package ID, a 404 status code is returned.</span></span>

<span data-ttu-id="ecc1b-137">Wenn die Paketquelle an eine oder mehrere Versionen verfügbar sind, wird ein Statuscode "200" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-137">If the package source has one or more versions, a 200 status code is returned.</span></span> <span data-ttu-id="ecc1b-138">Der Antworttext ist ein JSON-Objekt, wenn Sie die folgende Eigenschaft:</span><span class="sxs-lookup"><span data-stu-id="ecc1b-138">The response body is a JSON object with the following property:</span></span>

<span data-ttu-id="ecc1b-139">name</span><span class="sxs-lookup"><span data-stu-id="ecc1b-139">Name</span></span>     | <span data-ttu-id="ecc1b-140">Typ</span><span class="sxs-lookup"><span data-stu-id="ecc1b-140">Type</span></span>             | <span data-ttu-id="ecc1b-141">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ecc1b-141">Required</span></span> | <span data-ttu-id="ecc1b-142">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ecc1b-142">Notes</span></span>
-------- | ---------------- | -------- | -----
<span data-ttu-id="ecc1b-143">Versionen</span><span class="sxs-lookup"><span data-stu-id="ecc1b-143">versions</span></span> | <span data-ttu-id="ecc1b-144">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="ecc1b-144">array of strings</span></span> | <span data-ttu-id="ecc1b-145">ja</span><span class="sxs-lookup"><span data-stu-id="ecc1b-145">yes</span></span>      | <span data-ttu-id="ecc1b-146">Die Paket-IDs verfügbar</span><span class="sxs-lookup"><span data-stu-id="ecc1b-146">The package IDs available</span></span>

<span data-ttu-id="ecc1b-147">Die Zeichenfolgen in die `versions` Array sind alle klein, [normalisiert NuGet Versionszeichenfolgen](../reference/package-versioning.md#normalized-version-numbers).</span><span class="sxs-lookup"><span data-stu-id="ecc1b-147">The strings in the `versions` array are all lowercased, [normalized NuGet version strings](../reference/package-versioning.md#normalized-version-numbers).</span></span> <span data-ttu-id="ecc1b-148">Die Versionszeichenfolgen enthalten keine Metadaten Build SemVer 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-148">The version strings do not contain any SemVer 2.0.0 build metadata.</span></span>

<span data-ttu-id="ecc1b-149">Das Ziel ist, dass Versionszeichenfolgen, die in diesem Array gefunden wörtlich können, können Sie für verwendet werden die `LOWER_VERSION` Token in die folgenden Endpunkte gefunden.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-149">The intent is that the version strings found in this array can be used verbatim for the `LOWER_VERSION` tokens found in the following endpoints.</span></span>

### <a name="sample-request"></a><span data-ttu-id="ecc1b-150">Beispielanforderung</span><span class="sxs-lookup"><span data-stu-id="ecc1b-150">Sample request</span></span>

    GET https://api.nuget.org/v3-flatcontainer/owin/index.json

### <a name="sample-response"></a><span data-ttu-id="ecc1b-151">Beispielantwort</span><span class="sxs-lookup"><span data-stu-id="ecc1b-151">Sample response</span></span>

[!code-JSON [package-base-address-index.json](./_data/package-base-address-index.json)]

## <a name="download-package-content-nupkg"></a><span data-ttu-id="ecc1b-152">Herunterladen von Paketinhalt (.nupkg)</span><span class="sxs-lookup"><span data-stu-id="ecc1b-152">Download package content (.nupkg)</span></span>

<span data-ttu-id="ecc1b-153">Wenn der Client bekannt, ein Paket-ID und eine Version ist und den Paketinhalt herunterladen möchte, müssen sie nur so erstellen Sie die folgende URL:</span><span class="sxs-lookup"><span data-stu-id="ecc1b-153">If the client knows a package ID and version and wants to download the package content, they only need to construct the following URL:</span></span>

    GET {@id}/{LOWER_ID}/{LOWER_VERSION}/{LOWER_ID}.{LOWER_VERSION}.nupkg

### <a name="request-parameters"></a><span data-ttu-id="ecc1b-154">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ecc1b-154">Request parameters</span></span>

<span data-ttu-id="ecc1b-155">name</span><span class="sxs-lookup"><span data-stu-id="ecc1b-155">Name</span></span>          | <span data-ttu-id="ecc1b-156">In</span><span class="sxs-lookup"><span data-stu-id="ecc1b-156">In</span></span>     | <span data-ttu-id="ecc1b-157">Typ</span><span class="sxs-lookup"><span data-stu-id="ecc1b-157">Type</span></span>   | <span data-ttu-id="ecc1b-158">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ecc1b-158">Required</span></span> | <span data-ttu-id="ecc1b-159">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ecc1b-159">Notes</span></span>
------------- | ------ | ------ | -------- | -----
<span data-ttu-id="ecc1b-160">LOWER_ID</span><span class="sxs-lookup"><span data-stu-id="ecc1b-160">LOWER_ID</span></span>      | <span data-ttu-id="ecc1b-161">URL</span><span class="sxs-lookup"><span data-stu-id="ecc1b-161">URL</span></span>    | <span data-ttu-id="ecc1b-162">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ecc1b-162">string</span></span> | <span data-ttu-id="ecc1b-163">ja</span><span class="sxs-lookup"><span data-stu-id="ecc1b-163">yes</span></span>      | <span data-ttu-id="ecc1b-164">Die Paket-ID Kleinbuchstaben</span><span class="sxs-lookup"><span data-stu-id="ecc1b-164">The package ID, lowercase</span></span>
<span data-ttu-id="ecc1b-165">LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="ecc1b-165">LOWER_VERSION</span></span> | <span data-ttu-id="ecc1b-166">URL</span><span class="sxs-lookup"><span data-stu-id="ecc1b-166">URL</span></span>    | <span data-ttu-id="ecc1b-167">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ecc1b-167">string</span></span> | <span data-ttu-id="ecc1b-168">ja</span><span class="sxs-lookup"><span data-stu-id="ecc1b-168">yes</span></span>      | <span data-ttu-id="ecc1b-169">Die Paketversion normalisiert und klein</span><span class="sxs-lookup"><span data-stu-id="ecc1b-169">The package version, normalized and lowercased</span></span>

<span data-ttu-id="ecc1b-170">Beide `LOWER_ID` und `LOWER_VERSION` sind klein gemäß den Vergleichsregeln von implementiert. NET [ `System.String.ToLowerInvariant()` ](/dotnet/api/system.string.tolowerinvariant?view=netstandard-2.0#System_String_ToLowerInvariant) Methode.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-170">Both `LOWER_ID` and `LOWER_VERSION` are lowercased using the rules implemented by .NET's [`System.String.ToLowerInvariant()`](/dotnet/api/system.string.tolowerinvariant?view=netstandard-2.0#System_String_ToLowerInvariant) method.</span></span>

<span data-ttu-id="ecc1b-171">Die `LOWER_VERSION` ist die gewünschte Paketversion normalisiert mithilfe des NuGet-Version [Normalisierungsregeln](../reference/package-versioning.md#normalized-version-numbers).</span><span class="sxs-lookup"><span data-stu-id="ecc1b-171">The `LOWER_VERSION` is the desired package version normalized using NuGet's version [normalization rules](../reference/package-versioning.md#normalized-version-numbers).</span></span> <span data-ttu-id="ecc1b-172">Dies bedeutet, dass dieser Build-Metadaten, die die SemVer 2.0.0-Spezifikation nicht zulässig ist in diesem Fall ausgeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-172">This means that build metadata that is allowed by the SemVer 2.0.0 specification must be excluded in this case.</span></span>

### <a name="response-body"></a><span data-ttu-id="ecc1b-173">Antworttext</span><span class="sxs-lookup"><span data-stu-id="ecc1b-173">Response body</span></span>

<span data-ttu-id="ecc1b-174">Wenn das Paket auf die Paketquelle vorhanden ist, wird ein Statuscode "200" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-174">If the package exists on the package source, a 200 status code is returned.</span></span> <span data-ttu-id="ecc1b-175">Der Antworttext wird der Inhalt des Pakets selbst sein.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-175">The response body will be the package content itself.</span></span>

<span data-ttu-id="ecc1b-176">Wenn das Paket auf die Paketquelle nicht vorhanden ist, wird ein Statuscode "404" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-176">If the package does not exist on the package source, a 404 status code is returned.</span></span>

### <a name="sample-request"></a><span data-ttu-id="ecc1b-177">Beispielanforderung</span><span class="sxs-lookup"><span data-stu-id="ecc1b-177">Sample request</span></span>

    GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg

### <a name="sample-response"></a><span data-ttu-id="ecc1b-178">Beispielantwort</span><span class="sxs-lookup"><span data-stu-id="ecc1b-178">Sample response</span></span>

<span data-ttu-id="ecc1b-179">Der binäre Datenstrom, der NUPKG für Newtonsoft.Json 9.0.1 darstellt.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-179">The binary stream that is the .nupkg for Newtonsoft.Json 9.0.1.</span></span>

## <a name="download-package-manifest-nuspec"></a><span data-ttu-id="ecc1b-180">Paketmanifest (.nuspec) herunterladen</span><span class="sxs-lookup"><span data-stu-id="ecc1b-180">Download package manifest (.nuspec)</span></span>

<span data-ttu-id="ecc1b-181">Wenn der Client bekannt, ein Paket-ID und eine Version ist und das Paketmanifest herunterladen möchte, müssen sie nur so erstellen Sie die folgende URL:</span><span class="sxs-lookup"><span data-stu-id="ecc1b-181">If the client knows a package ID and version and wants to download the package manifest, they only need to construct the following URL:</span></span>

    GET {@id}/{LOWER_ID}/{LOWER_VERSION}/{LOWER_ID}.nuspec

### <a name="request-parameters"></a><span data-ttu-id="ecc1b-182">Anforderungsparameter</span><span class="sxs-lookup"><span data-stu-id="ecc1b-182">Request parameters</span></span>

<span data-ttu-id="ecc1b-183">name</span><span class="sxs-lookup"><span data-stu-id="ecc1b-183">Name</span></span>          | <span data-ttu-id="ecc1b-184">In</span><span class="sxs-lookup"><span data-stu-id="ecc1b-184">In</span></span>     | <span data-ttu-id="ecc1b-185">Typ</span><span class="sxs-lookup"><span data-stu-id="ecc1b-185">Type</span></span>    | <span data-ttu-id="ecc1b-186">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ecc1b-186">Required</span></span> | <span data-ttu-id="ecc1b-187">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ecc1b-187">Notes</span></span>
------------- | ------ | ------- | -------- | -----
<span data-ttu-id="ecc1b-188">LOWER_ID</span><span class="sxs-lookup"><span data-stu-id="ecc1b-188">LOWER_ID</span></span>      | <span data-ttu-id="ecc1b-189">URL</span><span class="sxs-lookup"><span data-stu-id="ecc1b-189">URL</span></span>    | <span data-ttu-id="ecc1b-190">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ecc1b-190">string</span></span>  | <span data-ttu-id="ecc1b-191">ja</span><span class="sxs-lookup"><span data-stu-id="ecc1b-191">yes</span></span>      | <span data-ttu-id="ecc1b-192">Die Paket-ID Kleinbuchstaben</span><span class="sxs-lookup"><span data-stu-id="ecc1b-192">The package ID, lowercase</span></span>
<span data-ttu-id="ecc1b-193">LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="ecc1b-193">LOWER_VERSION</span></span> | <span data-ttu-id="ecc1b-194">URL</span><span class="sxs-lookup"><span data-stu-id="ecc1b-194">URL</span></span>    | <span data-ttu-id="ecc1b-195">Ganze Zahl</span><span class="sxs-lookup"><span data-stu-id="ecc1b-195">integer</span></span> | <span data-ttu-id="ecc1b-196">ja</span><span class="sxs-lookup"><span data-stu-id="ecc1b-196">yes</span></span>      | <span data-ttu-id="ecc1b-197">Die Paketversion normalisiert und klein</span><span class="sxs-lookup"><span data-stu-id="ecc1b-197">The package version, normalized and lowercased</span></span>

<span data-ttu-id="ecc1b-198">Beide `LOWER_ID` und `LOWER_VERSION` sind klein gemäß den Vergleichsregeln von implementiert. NET [ `System.String.ToLowerInvariant()` ](/dotnet/api/system.string.tolowerinvariant?view=netstandard-2.0#System_String_ToLowerInvariant) Methode.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-198">Both `LOWER_ID` and `LOWER_VERSION` are lowercased using the rules implemented by .NET's [`System.String.ToLowerInvariant()`](/dotnet/api/system.string.tolowerinvariant?view=netstandard-2.0#System_String_ToLowerInvariant) method.</span></span>

<span data-ttu-id="ecc1b-199">Die `LOWER_VERSION` ist die gewünschte Paketversion normalisiert mithilfe des NuGet-Version [Normalisierungsregeln](../reference/package-versioning.md#normalized-version-numbers).</span><span class="sxs-lookup"><span data-stu-id="ecc1b-199">The `LOWER_VERSION` is the desired package version normalized using NuGet's version [normalization rules](../reference/package-versioning.md#normalized-version-numbers).</span></span> <span data-ttu-id="ecc1b-200">Dies bedeutet, dass dieser Build-Metadaten, die die SemVer 2.0.0-Spezifikation nicht zulässig ist in diesem Fall ausgeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-200">This means that build metadata that is allowed by the SemVer 2.0.0 specification must be excluded in this case.</span></span>

### <a name="response-body"></a><span data-ttu-id="ecc1b-201">Antworttext</span><span class="sxs-lookup"><span data-stu-id="ecc1b-201">Response body</span></span>

<span data-ttu-id="ecc1b-202">Wenn das Paket auf die Paketquelle vorhanden ist, wird ein Statuscode "200" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-202">If the package exists on the package source, a 200 status code is returned.</span></span> <span data-ttu-id="ecc1b-203">Der Antworttext werden Paketmanifest, also die .nuspec in die entsprechende .nupkg enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-203">The response body will be the package manifest, which is the .nuspec contained in the corresponding .nupkg.</span></span> <span data-ttu-id="ecc1b-204">Die .nuspec ist ein XML-Dokument.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-204">The .nuspec is an XML document.</span></span>

<span data-ttu-id="ecc1b-205">Wenn das Paket auf die Paketquelle nicht vorhanden ist, wird ein Statuscode "404" zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ecc1b-205">If the package does not exist on the package source, a 404 status code is returned.</span></span>

### <a name="sample-request"></a><span data-ttu-id="ecc1b-206">Beispielanforderung</span><span class="sxs-lookup"><span data-stu-id="ecc1b-206">Sample request</span></span>

    GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/6.0.4/newtonsoft.json.nuspec

### <a name="sample-response"></a><span data-ttu-id="ecc1b-207">Beispielantwort</span><span class="sxs-lookup"><span data-stu-id="ecc1b-207">Sample response</span></span>

[!code-XML [newtonsoft.json.6.0.4.xml](./_data/newtonsoft.json.6.0.4.xml)]