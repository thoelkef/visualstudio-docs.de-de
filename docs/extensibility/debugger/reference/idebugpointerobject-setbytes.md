---
title: "IDebugPointerObject::SetBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::SetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::SetBytes-Methode"
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Wert fest, der von einer Reihe von nachfolgenden Bytes dargestellt wird.  
  
## Syntax  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### Parameter  
 `dwStart`  
 \[in\]  Ein Offset in Bytes vom Anfang des Objekts selbst auf.  
  
 `dwCount`  
 \[in\]  Die Anzahl der Bytes, die festgelegt werden soll.  
  
 `pBytes`  
 \[in\]  Ein Bytearray, das den neuen Wert darstellt.  Dieser Wert wird im Objekt gespeichert, wobei beim angegebenen Offset begonnen wird.  
  
 `pdwBytes`  
 \[out\]  Gibt die Anzahl der Bytes, die tatsächlich festgelegt zurückgegeben.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird verwendet, wenn der Zeiger, die durch dieses [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) dargestellt zu einem Typ oder einem einfachen Array von Typen verweist \(d. h. ein Array, das über eine einfache Bytefolge dargestellt werden kann\).  Dieses `IDebugPointerObject`\-Objekt kann kein NULL\-Verweis ist \(es muss eine Adresse im Arbeitsspeicher verweisen\) sein.  
  
## Siehe auch  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)