---
title: "IDebugPointerObject::Dereference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::Dereference"
helpviewer_keywords: 
  - "IDebugPointerObject::Dereference-Methode"
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Objekt ab, auf das verwiesen wird.  
  
## Syntax  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### Parameter  
 `dwIndex`  
 \[in\]  Ein einfacher Byteoffset vom Anfang des Objekts selbst auf.  
  
 `ppObject`  
 \[out\]  Gibt ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt zurück, das das Objekt darstellt, das mit Offset \(falls vorhanden\) angezeigt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  Gibt E\_FAIL zurück, wenn dieses Objekt sich nicht auf ein anderes Objekt verweist.  
  
## Hinweise  
 Das Objekt kann sich auf ein komplexerer oder primitive Typen wie eine Klasse oder Struktur sein.  
  
## Siehe auch  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)