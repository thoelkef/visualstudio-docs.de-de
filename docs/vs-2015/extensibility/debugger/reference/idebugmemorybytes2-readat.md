---
title: 'IDebugMemoryBytes2:: Read at | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f10dc6e9e00e2b7f66722f3c89b74bb14e45fdbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180584"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Liest eine Byte Sequenz, beginnend an einem angegebenen Speicherort.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStartContext`  
 in Das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekt, das angibt, wo mit dem Lesen von Bytes begonnen wird  
  
 `dwCount`  
 in Die Anzahl der zu lesenden Bytes. Gibt auch die Länge des `rgbMemory` Arrays an.  
  
 `rgbMemory`  
 [in, out] Array mit den tatsächlich gelesenen Bytes.  
  
 `pdwRead`  
 vorgenommen Gibt die Anzahl von zusammenhängenden Bytes zurück, die tatsächlich gelesen werden.  
  
 `pdwUnreadable`  
 [in, out] Gibt die Anzahl der nicht lesbaren Bytes zurück. Kann ein NULL-Wert sein, wenn der Client nicht an der Anzahl der nicht lesbaren Bytes interessiert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn 100 Bytes angefordert werden und die ersten 50 lesbar sind, die nächsten 20 nicht lesbar sind und die verbleibenden 30 lesbar sind, gibt diese Methode Folgendes zurück:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 In diesem Fall `*pdwRead + *pdwUnreadable < dwCount` muss der Aufrufer einen zusätzlichen Aufruf durchführen, um die verbleibenden 30 Bytes des ursprünglich angeforderten 100 zu lesen, und das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Objekt, das im- `pStartContext` Parameter übergeben wird, muss um 70 erweitert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
