---
title: "IDebugProperty::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.SetValueAsString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::SetValueAsString"
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::SetValueAsString
Legt den Wert einer Eigenschaft aus einer angegebenen Zeichenfolge fest.  
  
## Syntax  
  
```  
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINT nRadix,  
);  
```  
  
#### Parameter  
 `pszValue`  
 \[in\] Der Wert festgelegt werden.  
  
 `nRadix`  
 \[in\] Wenn verwendet werden, Basis, alle numerischen Informationen interpretiert werden.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)