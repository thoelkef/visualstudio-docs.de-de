---
title: "GetAutoInsertExtensions-Methode | Microsoft Docs"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetAutoInsertExtensions-Methode
  Ruft Informationen über die Apps für Office ab, die während des Debuggens automatisch eingefügt werden sollen.  
  
 Diese Methode ist für eine spätere Verwendung vorgesehen.  
  
## Syntax  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*psaExtensionNames*|Die Erweiterungsnamen der Apps für Office.|  
  
## Rückgabewert  
 Ein HRESULT\-Wert, der angibt, ob die Methode erfolgreich ausgeführt wurde.  
  
## Hinweise  
 Jede App, damit Office eingefügt werden kann Office\-Anwendungserweiterungsname als zurückgegeben wird, der zu einem Wert unter HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\WEF\\Developer entspricht.  Der Host muss diese Werte in der Registrierung nachschlagen und Verbesserungen dann automatisch einfügen.  
  
  