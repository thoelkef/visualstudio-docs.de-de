---
title: '&lt;Signatur&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5637bad77e2d4e09d6d04007f0e0da3ed8af68df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signatur&gt; Element (ClickOnce-Bereitstellung)
Enthält die notwendigen Informationen, um dieses Bereitstellungsmanifest digital zu signieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Hinweise  
 Signieren ein Bereitstellungsmanifest mithilfe eines Umschlags-Signatur ist optional, jedoch empfohlen. Weitere Informationen zum Signieren von XML-Dateien finden Sie unter der World Wide Web Consortium Empfehlung, "XML Signature Syntax and Processing" beschriebenen [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Wenn Sie das Manifest signieren möchten, müssen die Hashes für alle Dateien angegeben werden. Ein Manifest mit Dateien, die nicht gehasht kann nicht signiert werden, da Benutzer den Inhalt von nicht gehashten Format vorliegen Dateien überprüft werden können.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht eine `Signature` Element in einem Bereitstellungsmanifest verwendet eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung.  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)