---
title: "IDebugPropertyField::GetPropertySetter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField::GetPropertySetter"
helpviewer_keywords: 
  - "IDebugPropertyField::GetPropertySetter-Methode"
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPropertyField::GetPropertySetter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Methode ab, die die Eigenschaft festlegt.  
  
## Syntax  
  
```cpp#  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```c#  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### Parameter  
 `ppField`  
 \[out\]  Gibt ein [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)\-Objekt zurück, das die Methode darstellt, für die die Eigenschaft festgelegt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Um die Methode abzurufen, die die Eigenschaft abruft, rufen Sie die [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)