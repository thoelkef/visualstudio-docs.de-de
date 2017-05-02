---
title: "IJsEnumDebugProperty::Next-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsEnumDebugProperty.Next
apilocation: jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsEnumDebugProperty::Next-Methode
Liest die Eigenschaften für dieses Objekt.  
  
## Syntax  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### Parameter  
 `count`  
 \[in\] Die Anzahl der zu lesenden Eigenschaften.  
  
 `ppDebugProperty`  
 \[out\] Objekt, das den Eigenschaftenbrowser darstellt.  
  
 `pActualCount`  
 \[out\] Die tatsächliche Anzahl von Eigenschaften des Objekts.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IEnumDebugProperty\-Schnittstelle](../../winscript/reference/ijsenumdebugproperty-interface.md)