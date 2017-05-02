---
title: "IPerPropertyBrowsing2::SetPredefinedValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.SetPredefinedValue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::SetPredefinedValue"
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::SetPredefinedValue
Legt den Wert der Eigenschaft fest, die von `dispID` angegeben wird.  Der vordefinierte Wert wird durch das Token `dwCookie.` identifiziert  
  
## Syntax  
  
```  
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### Parameter  
 `dispid`  
 \[in\] Dispatchbezeichner in der Eigenschaft, für die ein vordefinierter Wert festgelegt wird.  
  
 `dwCookie`  
 \[in\] Token, das den festzulegende Wert identifiziert.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IPerPropertyBrowsing2\-Schnittstelle](../../winscript/reference/iperpropertybrowsing2-interface-1.md)