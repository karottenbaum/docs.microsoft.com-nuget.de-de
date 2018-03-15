---
title: NuGet-CLI-Anmelde-Befehl | Microsoft Docs
author: dtivel
ms.author: dtivel
manager: doronm
ms.date: 03/06/2018
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Referenz für den nuget.exe Anmelde-Befehl"
keywords: NuGet-Anmelde-Verweis, Anmelde-Befehl
ms.reviewer:
- karann
- rmpablos
ms.openlocfilehash: f600a0830472703f40ef62f1b1538c53671703a9
ms.sourcegitcommit: 74c21b406302288c158e8ae26057132b12960be8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="sign-command-nuget-cli"></a><span data-ttu-id="ef425-104">Anmelde-Befehl (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="ef425-104">sign command (NuGet CLI)</span></span>

<span data-ttu-id="ef425-105">**Gilt für:** Erstellen von Paketen &bullet; **unterstützte Versionen:** 4.6 +</span><span class="sxs-lookup"><span data-stu-id="ef425-105">**Applies to:** package creation &bullet; **Supported versions:** 4.6+</span></span>

<span data-ttu-id="ef425-106">Signiert alle Pakete, die mit dem ersten Argument mit einem Zertifikat übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="ef425-106">Signs all the packages matching the first argument with a certificate.</span></span> <span data-ttu-id="ef425-107">Das Zertifikat mit dem privaten Schlüssel kann aus einer Datei oder aus einem Zertifikat in keinem Zertifikatspeicher installiert werden, indem einen Antragstellernamen oder Fingerabdruck eines abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="ef425-107">The certificate with the private key can be obtained from a file or from a certificate installed in a certificate store by providing a subject name or a thumbprint.</span></span>

<span data-ttu-id="ef425-108">Paketsignierung ist noch nicht unter Mono oder auf nicht-Windows-Plattformen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ef425-108">Package signing is not yet supported under Mono or on non-Windows platforms.</span></span>

## <a name="usage"></a><span data-ttu-id="ef425-109">Verwendung</span><span class="sxs-lookup"><span data-stu-id="ef425-109">Usage</span></span>

```cli
nuget sign <package(s)> [options]
```

<span data-ttu-id="ef425-110">wobei `<package(s)>` enthält eine oder mehrere `.nupkg` Dateien.</span><span class="sxs-lookup"><span data-stu-id="ef425-110">where `<package(s)>` is one or more `.nupkg` files.</span></span>

## <a name="options"></a><span data-ttu-id="ef425-111">Optionen</span><span class="sxs-lookup"><span data-stu-id="ef425-111">Options</span></span>

| <span data-ttu-id="ef425-112">Option</span><span class="sxs-lookup"><span data-stu-id="ef425-112">Option</span></span> | <span data-ttu-id="ef425-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ef425-113">Description</span></span> |
| --- | --- |
| <span data-ttu-id="ef425-114">CertificateFingerprint</span><span class="sxs-lookup"><span data-stu-id="ef425-114">CertificateFingerprint</span></span> | <span data-ttu-id="ef425-115">Gibt den SHA-1-Fingerabdruck des Zertifikats verwendet, um einen lokalen Zertifikatspeicher für das Zertifikat zu suchen.</span><span class="sxs-lookup"><span data-stu-id="ef425-115">Specifies the SHA-1 fingerprint of the certificate used to search a local certificate store for the certificate.</span></span> |
| <span data-ttu-id="ef425-116">CertificatePassword</span><span class="sxs-lookup"><span data-stu-id="ef425-116">CertificatePassword</span></span> | <span data-ttu-id="ef425-117">Gibt das Kennwort des Zertifikats an, bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="ef425-117">Specifies the certificate password, if needed.</span></span> <span data-ttu-id="ef425-118">Wenn ein Zertifikat kennwortgeschützt ist, jedoch kein Kennwort bereitgestellt wird, der Befehl wird nach einem Kennwort Fragen zur Laufzeit, es sei denn, die - Option nicht interaktiven übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="ef425-118">If a certificate is password protected but no password is provided, the command will prompt for a password at run time, unless the -NonInteractive option is passed.</span></span> |
| <span data-ttu-id="ef425-119">CertificatePath</span><span class="sxs-lookup"><span data-stu-id="ef425-119">CertificatePath</span></span> | <span data-ttu-id="ef425-120">Gibt den Dateipfad für das Zertifikat zum Signieren des Pakets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ef425-120">Specifies the file path to the certificate to be used in signing the package.</span></span> |
| <span data-ttu-id="ef425-121">CertificateStoreLocation</span><span class="sxs-lookup"><span data-stu-id="ef425-121">CertificateStoreLocation</span></span> | <span data-ttu-id="ef425-122">Gibt den Namen der dem x. 509-Zertifikat Store verwenden, für das Zertifikat gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="ef425-122">Specifies the name of the X.509 certificate store use to search for the certificate.</span></span> <span data-ttu-id="ef425-123">Der Standardwert ist "CurrentUser", die vom aktuellen Benutzer verwendete x. 509-Zertifikatspeicher.</span><span class="sxs-lookup"><span data-stu-id="ef425-123">Defaults to "CurrentUser", the X.509 certificate store used by the current user.</span></span> <span data-ttu-id="ef425-124">Diese Option sollte verwendet werden, wenn Sie das Zertifikat über - %certificatesubjectname oder CertificateFingerprint - Optionen angeben.</span><span class="sxs-lookup"><span data-stu-id="ef425-124">This option should be used when specifying the certificate via -CertificateSubjectName or -CertificateFingerprint options.</span></span> |
| <span data-ttu-id="ef425-125">CertificateStoreName</span><span class="sxs-lookup"><span data-stu-id="ef425-125">CertificateStoreName</span></span> | <span data-ttu-id="ef425-126">Gibt den Namen des x. 509-Zertifikatspeichers zu verwenden, um für das Zertifikat zu suchen.</span><span class="sxs-lookup"><span data-stu-id="ef425-126">Specifies the name of the X.509 certificate store to use to search for the certificate.</span></span> <span data-ttu-id="ef425-127">Der Standardwert ist "My", dem x. 509-Zertifikatspeicher für persönliche Zertifikate.</span><span class="sxs-lookup"><span data-stu-id="ef425-127">Defaults to "My", the X.509 certificate store for personal certificates.</span></span> <span data-ttu-id="ef425-128">Diese Option sollte verwendet werden, wenn Sie das Zertifikat über - %certificatesubjectname oder CertificateFingerprint - Optionen angeben.</span><span class="sxs-lookup"><span data-stu-id="ef425-128">This option should be used when specifying the certificate via -CertificateSubjectName or -CertificateFingerprint options.</span></span> |
| <span data-ttu-id="ef425-129">CertificateSubjectName</span><span class="sxs-lookup"><span data-stu-id="ef425-129">CertificateSubjectName</span></span> | <span data-ttu-id="ef425-130">Gibt den Antragstellernamen des Zertifikats verwendet, um einen lokalen Zertifikatspeicher für das Zertifikat zu suchen.</span><span class="sxs-lookup"><span data-stu-id="ef425-130">Specifies the subject name of the certificate used to search a local certificate store for the certificate.</span></span>  <span data-ttu-id="ef425-131">Die Suche wird ein Zeichenfolgenvergleich mit dem bereitgestellten Wert, der alle Zertifikate mit dem Antragstellernamen, enthält die Zeichenfolge, unabhängig von der anderen Werte für den Antragsteller findet.</span><span class="sxs-lookup"><span data-stu-id="ef425-131">The search is a case-insensitive string comparison using the supplied value, which will find all certificates with the subject name containing that string, regardless of other subject values.</span></span>  <span data-ttu-id="ef425-132">Der Zertifikatspeicher kann durch - Zertifikatspeichername und CertificateStoreLocation - Optionen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="ef425-132">The certificate store can be specified by -CertificateStoreName and -CertificateStoreLocation options.</span></span> |
| <span data-ttu-id="ef425-133">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="ef425-133">ConfigFile</span></span> | <span data-ttu-id="ef425-134">Die NuGet-Konfigurationsdatei angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ef425-134">The NuGet configuration file to apply.</span></span> <span data-ttu-id="ef425-135">Wenn nicht angegeben, `%AppData%\NuGet\NuGet.Config` (Windows) oder `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ef425-135">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="ef425-136">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="ef425-136">ForceEnglishOutput</span></span> | <span data-ttu-id="ef425-137">Erzwingt, dass nuget.exe über eine invariante Kultur Englisch-basierte ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ef425-137">Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="ef425-138">HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ef425-138">HashAlgorithm</span></span> | <span data-ttu-id="ef425-139">Der Hashalgorithmus zum Signieren des Pakets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ef425-139">Hash algorithm to be used to sign the package.</span></span> <span data-ttu-id="ef425-140">Der Standardwert ist SHA256.</span><span class="sxs-lookup"><span data-stu-id="ef425-140">Defaults to SHA256.</span></span> |
| <span data-ttu-id="ef425-141">Hilfe</span><span class="sxs-lookup"><span data-stu-id="ef425-141">Help</span></span> | <span data-ttu-id="ef425-142">Zeigt die Hilfe Informationen für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="ef425-142">Displays help information for the command.</span></span> |
| <span data-ttu-id="ef425-143">NonInteractive</span><span class="sxs-lookup"><span data-stu-id="ef425-143">NonInteractive</span></span> | <span data-ttu-id="ef425-144">Unterdrückt aufforderungen für Benutzereingaben oder Bestätigungen an.</span><span class="sxs-lookup"><span data-stu-id="ef425-144">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="ef425-145">OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="ef425-145">OutputDirectory</span></span> | <span data-ttu-id="ef425-146">Gibt das Verzeichnis, in dem das signierte Paket gespeichert werden soll.</span><span class="sxs-lookup"><span data-stu-id="ef425-146">Specifies the directory where the signed package should be saved.</span></span> <span data-ttu-id="ef425-147">Standardmäßig wird das ursprüngliche Paket durch das signierte Paket überschrieben.</span><span class="sxs-lookup"><span data-stu-id="ef425-147">By default the original package is overwritten by the signed package.</span></span> |
| <span data-ttu-id="ef425-148">Overwrite</span><span class="sxs-lookup"><span data-stu-id="ef425-148">Overwrite</span></span> | <span data-ttu-id="ef425-149">Schalter, um anzugeben, ob die aktuelle Signatur überschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="ef425-149">Switch to indicate if the current signature should be overwritten.</span></span> <span data-ttu-id="ef425-150">Standardmäßig wird der Befehl fehl, wenn das Paket bereits über eine Signatur verfügt.</span><span class="sxs-lookup"><span data-stu-id="ef425-150">By default the command will fail if the package already has a signature.</span></span> |
| <span data-ttu-id="ef425-151">Timestamper</span><span class="sxs-lookup"><span data-stu-id="ef425-151">Timestamper</span></span> | <span data-ttu-id="ef425-152">Die URL zu einer RFC 3161-Zeitstempelserver.</span><span class="sxs-lookup"><span data-stu-id="ef425-152">URL to an RFC 3161 timestamping server.</span></span> |
| <span data-ttu-id="ef425-153">TimestampHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ef425-153">TimestampHashAlgorithm</span></span> | <span data-ttu-id="ef425-154">Der Hashalgorithmus, der vom RFC 3161-Zeitstempelserver verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ef425-154">Hash algorithm to be used by the RFC 3161 timestamp server.</span></span> <span data-ttu-id="ef425-155">Der Standardwert ist SHA256.</span><span class="sxs-lookup"><span data-stu-id="ef425-155">Defaults to SHA256.</span></span> |
| <span data-ttu-id="ef425-156">Ausführlichkeit</span><span class="sxs-lookup"><span data-stu-id="ef425-156">Verbosity</span></span> | <span data-ttu-id="ef425-157">Gibt die Anzahl der Details in der Ausgabe angezeigt: *normalen*, *stillen*, *ausführliche*.</span><span class="sxs-lookup"><span data-stu-id="ef425-157">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

## <a name="examples"></a><span data-ttu-id="ef425-158">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ef425-158">Examples</span></span>

```cli
nuget sign MyPackage.nupkg -Timestamper http://timestamp.test

nuget sign .\..\MyPackage.nupkg -Timestamper http://timestamp.test -OutputDirectory .\..\Signed
```