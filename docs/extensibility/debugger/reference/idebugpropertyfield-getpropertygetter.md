---
title: "IDebugPropertyField::GetPropertyGetter | Microsoft Docs"
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
  - "IDebugPropertyField::GetPropertyGetter"
helpviewer_keywords: 
  - "IDebugPropertyField::GetPropertyGetter-Methode"
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPropertyField::GetPropertyGetter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Methode ab, mit der die Eigenschaft abgerufen werden soll.  
  
## Syntax  
  
```cpp#  
HRESULT GetPropertyGetter(   
   IDebugMethodField** ppField  
);  
```  
  
```cpp#  
int GetPropertyGetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### Parameter  
 `ppField`  
 \[out\]  Gibt ein [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)\-Objekt zurück, das die Methode darstellt, für die die Eigenschaft abgerufen werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Um die Methode abrufen, die die Eigenschaft festlegt, [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) Aufruf der Methode.  
  
## Siehe auch  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)