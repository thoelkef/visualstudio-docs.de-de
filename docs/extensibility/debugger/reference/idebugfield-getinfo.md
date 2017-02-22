---
title: "IDebugField::GetInfo | Microsoft Docs"
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
  - "IDebugField::GetInfo"
helpviewer_keywords: 
  - "IDebugField::GetInfo-Methode"
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft anzeigbare Informationen über das Feld ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### Parameter  
 `dwFields`  
 \[in\]  Eine Kombination von [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Konstanten, die die anzuzeigende Informationen auswählt.  Wenn das Feld ein Symbol darstellt, ist dies i. d. R. der Symbolname und \- Typ.  
  
 `pFieldInfo`  
 \[out\]  Gibt die Informationen in der angegebenen [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)