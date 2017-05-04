---
title: "JS_PROPERTY_MEMBERS-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_MEMBERS
apilocation: jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JS_PROPERTY_MEMBERS-Enumeration
Flags, um den Typ der Informationen anzugeben, die in einer Anforderung für Member eines Objekts zurückzugeben sind.  
  
## Syntax  
  
```  
enum JS_PROPERTY_MEMBERS  
{  
   JS_PROPERTY_MEMBERS_ALL = 0,  
   JS_PROPERTY_MEMBERS_ARGUMENTS = 1  
} JS_PROPERTY_MEMBERS;  
```  
  
## Member  
  
### Werte  
  
|Name|Beschreibung|  
|----------|------------------|  
|`JS_PROPERTY_MEMBERS_ALL`|Stellt eine Anforderung, alle Member aufzulisten, dar.|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|Stellt eine Anforderung, nur Argumente aufzulisten, dar.|  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [Windows Script\-Schnittstellenverweis](../../winscript/reference/windows-script-interfaces-reference.md)