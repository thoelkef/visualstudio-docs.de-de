---
title: "GetValidCompatibleFramework-Funktion | Microsoft Docs"
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
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# GetValidCompatibleFramework-Funktion
  Dies wird API\-Unterstützung die Office\-Infrastruktur und nicht vorgesehen, direkt aus dem Code verwendet werden.  
  
## Syntax  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Verwenden Sie nicht.|  
|*pbstrValidFrameworkTag*|Verwenden Sie nicht.|  
  
## Rückgabewert  
 Wenn die Funktion folgt, gibt sie **S\_OK** zurück.  Wenn die Funktion fehlschlägt, gibt sie einen Fehlercode zurück.  
  
  