---
title: "IDebugMethodField::GetThis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetThis"
helpviewer_keywords: 
  - "IDebugMethodField::GetThis-Methode"
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Zeiger `this` \(`Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]\) des Objekts ab, das die Methode enthält.  
  
## Syntax  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### Parameter  
 `ppClass`  
 \[out\]  Gibt ein Objekt zurück, das den [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) „this“ \- Zeiger darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 In objektorientierten Sprachen gibt es normalerweise keinen impliziten Zeiger auf die aktuelle Instanziierung einer Klasse.  Dies wird auch als `this` in C\#\/C\+\+ und als `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  
  
## Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)