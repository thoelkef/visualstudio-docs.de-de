---
title: "EnsureVSTOComponent-Funktion"
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
ms.assetid: e101fcd5-37a2-4b8c-b9ac-a84624298736
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# EnsureVSTOComponent-Funktion
  Dies wird API\-Unterstützung die Office\-Infrastruktur und nicht vorgesehen, direkt aus dem Code verwendet werden.  
  
## Syntax  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*pProject*|Verwenden Sie nicht.|  
  
## Rückgabewert  
 Wenn die Funktion folgt, gibt sie **S\_OK** zurück.  Wenn die Funktion fehlschlägt, gibt sie einen Fehlercode zurück.  
  
  