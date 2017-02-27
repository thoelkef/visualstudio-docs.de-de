---
title: "&lt;publisherIdentity&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "publisherIdentity Element [ClickOnce deployment manifest], introduction"
  - "required element for signed manifests [ClickOnce], publisherIdentity Element"
  - "publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;publisherIdentity&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält Informationen zum Herausgeber, der dieses Bereitstellungsmanifest signiert hat.  
  
## Syntax  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## Elemente und Attribute  
 Das `publisherIdentity`\-Element ist für signierte Manifeste erforderlich.  In der folgenden Tabelle werden die Attribute aufgeführt, die vom `publisherIdentity`\-Element unterstützt werden.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`name`|Erforderlich.  Beschreibt die Identität der Partei, die diese Anwendung veröffentlicht hat.|  
|`issuerKeyHash`|Erforderlich.  Enthält den SHA\-1\-Hash für den öffentlichen Schlüssel des Zertifikatausstellers.|  
  
#### Parameter  
  
## Eigenschaftswert\/Rückgabewert  
  
## Ausnahmen  
  
## Hinweise  
  
## Anforderungen  
  
## Unterüberschrift