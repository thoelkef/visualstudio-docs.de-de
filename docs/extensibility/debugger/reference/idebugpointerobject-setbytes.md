---
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9bab2459d2de40fdc3ea44fe7e5e92c138a5f006
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Legt den Wert von einer Reihe von aufeinander folgenden Bytes gezeigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwStart`  
 [in] Ein Offset in Bytes vom Beginn des Objekts, auf die gezeigt wird.  
  
 `dwCount`  
 [in] Die Anzahl der Bytes fest.  
  
 `pBytes`  
 [in] Ein Array von Bytes, die den neuen Wert darstellt. Dieser Wert wird in das Objekt, beginnend am angegebenen Offset gespeichert.  
  
 `pdwBytes`  
 [out] Gibt die Anzahl der Bytes findet das eigentliche festlegen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, wenn der Zeiger, dargestellt durch diese [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) verweist auf einen primitiven Typ oder ein einfaches Array mit Grundtypen (d. h. ein Array, das durch eine einfache Folge von Bytes dargestellt werden können). Dies `IDebugPointerObject` Objekt handelt es sich nicht um einen null-Verweis (es muss auf eine Adresse im Arbeitsspeicher zeigen).  
  
## <a name="see-also"></a>Siehe auch  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)