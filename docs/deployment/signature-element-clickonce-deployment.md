---
title: '&lt;Signatur&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ffcc04808916d8ef31fb77cab72f54c1e22e924c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 Signieren ein Bereitstellungsmanifest mithilfe eines Umschlags-Signatur ist optional, jedoch empfohlen. Weitere Informationen zum Signieren von XML-Dateien finden Sie unter der World Wide Web Consortium Empfehlung, "XML Signature Syntax and Processing" beschriebenen [http://www.w3.org/TR/xmldsig-core/](http://www.w3.org/TR/xmldsig-core/).  
  
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