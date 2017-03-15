---
title: "IDebugPointerObject::GetBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerObject::GetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::GetBytes-Methode"
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Wert selbst wird als Folge von aufeinander folgenden in Bytes ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### Parameter  
 `dwStart`  
 \[in\]  Ein Offset in Bytes vom Anfang des Objekts selbst auf.  
  
 `dwCount`  
 \[in\]  Die Anzahl der abzurufenden Bytes.  
  
 `pBytes`  
 \[in, out\]  Ein Array, das mit dem Wert als Folge von aufeinander folgenden Bytes gefüllt wird, beginnend beim angegebenen Offset aus dem Objekt selbst wird.  
  
 `pdwBytes`  
 \[out\]  Gibt die Anzahl der Bytes, die tatsächlich abgerufenen zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird verwendet, wenn der Zeiger, die durch dieses [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) dargestellt zu einem Typ oder einem einfachen Array von Typen verweist \(d. h. ein Array, das über eine einfache Bytefolge dargestellt werden kann\).  
  
## Siehe auch  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)