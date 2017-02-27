---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypeFromTypeDef"
  - "IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef"
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen angegebenen Typ das Token ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetTypeFromTypeDef(  
   ULONG32       ulAppDomainID,  
   GUID          guidModule,  
   _mdToken      tokClass,  
   IDebugField** ppType  
);  
```  
  
```c#  
int GetTypeFromTypeDef(  
   uint            ulAppDomainID,  
   Guid            guidModule,  
   int             tokClass,  
   out IDebugField ppType  
);  
```  
  
#### Parameter  
 `ulAppDomainID`  
 \[in\]  Bezeichner der Anwendungsdomäne.  
  
 `guidModule`  
 \[in\]  Eindeutiger Bezeichner des Moduls.  
  
 `tokClass`  
 \[in\]  Token, das den Typ darstellt.  
  
 `ppType`  
 \[out\]  Gibt ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt zurück, das den Typ enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)