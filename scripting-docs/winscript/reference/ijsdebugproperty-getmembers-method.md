---
title: "IJsDebugProperty::GetMembers-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProperty.GetMembers
apilocation: jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProperty::GetMembers-Methode
Ruft die Member dieses Objekts ab.  
  
## Syntax  
  
```  
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### Parameter  
 `members`  
 \[in\] Flags, um anzugeben, was in den Memberinformationen enthalten ist.  
  
 `ppEnum`  
 \[out\] Die Member des Objekts.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugProperty\-Schnittstelle](../../winscript/reference/ijsdebugproperty-interface.md)