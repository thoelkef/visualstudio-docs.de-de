---
title: "&lt;Signature&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Signature> element [ClickOnce deployment manifest]"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Signature&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält die erforderlichen Informationen, um dieses Bereitstellungsmanifest digital zu signieren.  
  
## Syntax  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## Hinweise  
 Das Signieren eines Bereitstellungsmanifests, das eine Envelope\-Signatur verwendet, ist optional, jedoch empfohlen.  Weitere Informationen zum Signieren von XML\-Dateien finden Sie in der Empfehlung des World Wide Web Consortium "XML\-Signature Syntax and Processing", die unter [http:\/\/www.w3.org\/TR\/xmldsig\-core\/](http://www.w3.org/TR/xmldsig-core/) beschrieben ist \(nur auf Englisch verfügbar\).  
  
 Wenn Sie das Manifest signieren möchten, müssen Hashs für alle Dateien bereitgestellt werden.  Ein Manifest mit Dateien, die nicht gehasht sind, kann nicht signiert werden, da die Benutzer die Inhalte nicht gehashter Dateien nicht überprüfen können.  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `Signature`\-Element in einem Bereitstellungsmanifest, das in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung verwendet wird, veranschaulicht.  
  
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
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)