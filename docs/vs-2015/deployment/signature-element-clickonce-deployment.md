---
title: '&lt;Signatur&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b1f829971a1e5a5d62c95c1f81fb75375f7cc74e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521698"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signatur&gt; -Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ &lt;Signatur&gt; -Element (ClickOnce-Bereitstellung)](https://docs.microsoft.com/visualstudio/deployment/signature-element-clickonce-deployment).  
  
Enthält die notwendigen Informationen, um dieses Bereitstellungsmanifest digital zu signieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Hinweise  
 Signieren ein Bereitstellungsmanifest mithilfe eines Signatur-Envelope ist optional, jedoch empfohlen. Weitere Informationen zum Signieren von XML-Dateien finden Sie unter die Empfehlung des World Wide Web Consortium "XML Signature Syntax and Processing" die am beschrieben [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Wenn Sie das Manifest signieren möchten, müssen die Hashes für alle Dateien angegeben werden. Ein Manifest mit Dateien, die nicht hinzugefügt werden kann nicht signiert werden, da der Benutzer den Inhalt nicht gehashten Format vorliegen Dateien nicht überprüfen können.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, eine `Signature` Element in einem Bereitstellungsmanifest verwendet eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung.  
  
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



