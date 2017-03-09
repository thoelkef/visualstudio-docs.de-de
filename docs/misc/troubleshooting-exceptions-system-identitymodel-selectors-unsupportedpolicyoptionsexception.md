---
title: "Problembehandlung bei Ausnahmen: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.IdentityModel.Selectors.UnsupportedPolicyOptionsException-Ausnahme"
  - "UnsupportedPolicyOptionsException-Ausnahme"
ms.assetid: 1151127d-81a1-4d87-8462-924ab9d1ee01
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException
Eine <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>\-Ausnahme gibt an, dass dem System eine Richtlinie hinzugefügt wurde, die nicht unterstützte Optionen enthält. Folgende Beschränkungen können unter anderem diese Fehler verursachen:  
  
 Ein Empfänger hat ein Token vom lokalen Sicherheitstokendienst angefordert und hierfür http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self als Tokenaussteller angegeben. Eine der in der Richtlinie angegebenen Anforderungen wird jedoch vom lokalen CardSpace\-Sicherheitstokendienst nicht unterstützt. Weitere Informationen finden Sie unter [Eine technische Referenz für das Informationskarten\-Profil V1.0](http://go.microsoft.com/fwlink/?LinkId=102401). Nachstehend finden Sie Beispiele für nicht unterstützte Optionen:  
  
-   Ein vom Empfänger angeforderter Anspruch ist nicht in der Liste der unterstützten Ansprüche enthalten, die im Abschnitt [Unterstützte Umwandlungstypen](http://go.microsoft.com/fwlink/?LinkId=102402) unter "Eine technische Referenz für das Informationskarten\-Profil V1.0" aufgeführt sind.  
  
-   Der Tokentyp unterscheidet sich von dem Typ für SAML 1.0 oder 1.1.  
  
-   Schlüssel für Nicht\-SSL\-Sites sind nicht symmetrisch.  
  
-   Der KeyWrapAlgorithm unterscheidet sich vom Standardalgorithmus.  
  
-   Die Richtlinie enthält ein nicht unterstütztes Element. Die folgenden Elemente werden unterstützt:  
  
    -   EncryptionAlgorithm  
  
    -   CanonicalizationAlgorithm  
  
    -   SignWith  
  
    -   TokenType  
  
    -   ClaimsElement  
  
    -   KeyType  
  
    -   KeySize  
  
    -   EncryptWith  
  
    -   RequestType  
  
    -   SecondaryParameters  
  
    -   KeyWrapAlgorithm  
  
-   wst:RequestType ist nicht vom Typ Issue.  
  
-   Die Schlüsselgröße für asymmetrische Schlüsseltypen ist nicht 2048.  
  
## Siehe auch  
 <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)