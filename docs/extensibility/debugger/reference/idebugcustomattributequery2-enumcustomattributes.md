---
title: "IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2::EnumCustomAttributes"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::EnumCustomAttributes"
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttributeQuery2::EnumCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen Enumerator für alle benutzerdefinierten Attribute ab, die an dieses Feld angefügt werden.  
  
## Syntax  
  
```cpp#  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```c#  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)\-Objekt zurück, das die Liste benutzerdefinierter Attribute darstellt. Andernfalls gibt einen NULL\-Wert zurück, wenn keine benutzerdefinierten Attribute vorhanden sind.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK oder S\_FALSE zurück, wenn keine benutzerdefinierten Attribute für dieses Feld wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Feld kann mehrere benutzerdefinierte Attribute verfügen.  
  
## Siehe auch  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)