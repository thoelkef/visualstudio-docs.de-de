---
title: "GetVstoSolutionMetadata-Funktion"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: e8195838-fb9f-42b2-bb76-7ae3753f7751
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# GetVstoSolutionMetadata-Funktion
  Dies wird API\-Unterstützung die Office\-Infrastruktur und nicht vorgesehen, direkt aus dem Code verwendet werden.  
  
## Syntax  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|Verwenden Sie nicht.|  
|*ppSolutionInfo*|Verwenden Sie nicht.|  
  
## Rückgabewert  
 Wenn die Funktion folgt, gibt sie **S\_OK** zurück.  Wenn die Funktion fehlschlägt, gibt sie einen Fehlercode zurück.  
  
  