---
title: Bereitstellungsmanifeste für Office-Projektmappen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], deployment manifests
- deployment manifests [Office development in Visual Studio]
- manifests [Office development in Visual Studio], deployment
- Office development in Visual Studio, deployment manifests
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8e2b45ac44cafd757aaa4ff96c97995c88ab10ed
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835382"
---
# <a name="deployment-manifests-for-office-solutions"></a>Bereitstellungsmanifeste für Office-Projektmappen
  Ein Bereitstellungsmanifest ist eine XML-Datei, die beschreibt die bereitstellungseinstellungen für die einer Office-Projektmappe, und die aktuelle Anwendungsversion identifiziert.

 Die Office-Entwicklung in Visual Studio verwendet die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] definierte die [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) Verweis.

## <a name="remarks"></a>Hinweise
 Für Office-Projektmappen, die Bereitstellungsmanifestdatei identifiziert die aktuelle Version und anderer bereitstellungseinstellungen. Er verweist auf das Anwendungsmanifest und die aktuelle Version der Projektmappe und alle Dateien innerhalb der Projektmappe beschreibt.

## <a name="file-name-syntax"></a>Die Syntax für Dateinamen
 Der Name einer Bereitstellungsmanifestdatei muss mit enden die *".VSTO"* Erweiterung. Obwohl es ein Standard ist [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Bereitstellungsmanifest, die Erweiterung, die zum Aktivieren der Visual Studio-Tools für Office-Laufzeit zum Verarbeiten der Datei unterscheidet sich.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht ein Bereitstellungsmanifest für eine Visual Studio-Tools für Office-Projektmappe.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly
  xsi:schemaLocation=
    "urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig="http://www.w3.org/2000/09/xmldsig#"
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <assemblyIdentity
    name="ContosoOfficeSolutions.vsto"
    version="1.0.0.0"
    publicKeyToken="25d0f3ca94156f1f"
    language="neutral"
    processorArchitecture="msil"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <description
    asmv2:publisher="Microsoft"
    asmv2:product="ContosoOfficeSolutions"
    xmlns="urn:schemas-microsoft-com:asm.v1" />
  <deployment install="false" mapFileExtensions="true" />
  <dependency>
    <dependentAssembly
      dependencyType="install"
      codebase="ContosoOfficeSolutions.dll.manifest"
      size="13545">
      <assemblyIdentity
        name="ContosoOfficeSolutions.dll"
        version="1.0.0.0"
        publicKeyToken="25d0f3ca94156f1f"
        language="neutral"
        processorArchitecture="msil"
        type="win32" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm=
            "urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm=
          "http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>PoY</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
  <publisherIdentity name="name" issuerKeyHash="003" />
<Signature
  Id="StrongNameSignature"
  xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
      "http://www.w3.org/2001/10/xml-exc-c14n#" />
  <SignatureMethod Algorithm=
    "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
          "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
        <Transform Algorithm=
          "http://www.w3.org/2001/10/xml-exc-c14n#" />
      </Transforms>
      <DigestMethod Algorithm=
        "http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>5oz</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>nNG</SignatureValue>
  <KeyInfo Id="StrongNameKeyInfo">
    <KeyValue>
      <RSAKeyValue>
        <Modulus>ufI</Modulus>
        <Exponent>AQAB</Exponent>
      </RSAKeyValue>
    </KeyValue>
    <msrel:RelData
      xmlns:msrel=
        "http://schemas.microsoft.com/windows/rel/2005/reldata">
      <r:license
        xmlns:r="urn:mpeg:mpeg21:2003:01-REL-R-NS"
        xmlns:as=
          "http://schemas.microsoft.com/windows/pki/2005/Authenticode">
        <r:grant>
          <as:ManifestInformation
            Hash="099"
            Description=""
            Url="">
            <as:assemblyIdentity
              name="ContosoOfficeSolutions.vsto"
              version="1.0.0.0"
              publicKeyToken="25d0f3ca94156f1f"
              language="neutral"
              processorArchitecture="msil"
              xmlns="urn:schemas-microsoft-com:asm.v1" />
          </as:ManifestInformation>
          <as:SignedBy />
          <as:AuthenticodePublisher>
            <as:X509SubjectName>CN=DDNET\BAAdmin</as:X509SubjectName>
          </as:AuthenticodePublisher>
        </r:grant>
        <r:issuer>
          <Signature
            Id="AuthenticodeSignature"
            xmlns="http://www.w3.org/2000/09/xmldsig#">
            <SignedInfo>
              <CanonicalizationMethod
                Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
              <SignatureMethod
                Algorithm=
                  "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
              <Reference URI="">
                <Transforms>
                  <Transform Algorithm=
                    "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
                  <Transform Algorithm=
                    "http://www.w3.org/2001/10/xml-exc-c14n#" />
                </Transforms>
                <DigestMethod
                  Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
                <DigestValue>iAd</DigestValue>
              </Reference>
            </SignedInfo>
            <SignatureValue>HL9</SignatureValue>
            <KeyInfo>
              <KeyValue>
                <RSAKeyValue>
                  <Modulus>ufI</Modulus>
                  <Exponent>AQAB</Exponent>
                </RSAKeyValue>
              </KeyValue>
              <X509Data>
                <X509Certificate>MII</X509Certificate>
              </X509Data>
            </KeyInfo>
          </Signature>
        </r:issuer>
      </r:license>
    </msrel:RelData>
  </KeyInfo>
</Signature>
</asmv1:assembly>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)