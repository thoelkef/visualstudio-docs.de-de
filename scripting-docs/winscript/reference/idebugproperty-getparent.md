---
title: "IDebugProperty::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetParent"
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetParent
Ruft die Elemente Eigenschaft einer Eigenschaft ab.  
  
## Syntax  
  
```  
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### Parameter  
 `ppParent`  
 \[out\] Gibt die `IDebugProperty`\-Schnittstelle zurück, die das übergeordnete Element der Eigenschaft darstellt.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)