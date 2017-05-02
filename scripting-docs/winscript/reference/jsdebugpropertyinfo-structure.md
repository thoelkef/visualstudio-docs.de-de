---
title: "JsDebugPropertyInfo-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsDebugPropertyInfo-Struktur
Gibt Informationen über eine Eigenschaft an.  
  
## Syntax  
  
```  
typedef struct tagJsDebugPropertyInfo  
{  
   BSTR name;  
   BSTR type;  
   BSTR value;  
   BSTR fullName;  
   JS_PROPERTY_ATTRIBUTES attr;  
} JsDebugPropertyInfo;  
```  
  
## Member  
 `name`  
 Der Name der Eigenschaft.  
  
 `type`  
 Der Typ der Eigenschaft.  
  
 `value`  
 Der Wert der Eigenschaft.  
  
 `fullName`  
 Der vollständige Name der Eigenschaft.  
  
 `attr`  
 Eine Enumeration, die die Eigenschaftsattribute darstellt.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [Windows Script\-Schnittstellenverweis](../../winscript/reference/windows-script-interfaces-reference.md)