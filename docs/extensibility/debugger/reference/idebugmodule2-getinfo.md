---
title: "IDebugModule2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::GetInfo"
helpviewer_keywords: 
  - "GetInfo-Methode"
  - "IDebugModule2::GetInfo-Methode"
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft Informationen über dieses Modul ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### Parameter  
 `dwFields`  
 \[in\]  Eine Kombination von Flags aus der [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)\-Enumeration, die angeben, welche Felder aus `pInfo` ergänzt werden sollen.  
  
 `pInfo`  
 \[in, out\]  Eine [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur, die mit einer Beschreibung des Moduls gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur enthält den Namen des Moduls, das im **Module** Fenster angezeigt wird.  
  
## Siehe auch  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)