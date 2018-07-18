---
title: IDebugMemoryContext2::Add | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad55b81c1c4126efd69779e929521cfb94235ccc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111933"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Fügt den angegebenen Wert für den aktuellen Kontext aus, und gibt einen neuen Kontext zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCount`  
 [in] Der Wert, den aktuellen Kontext hinzugefügt werden soll.  
  
 `ppMemCxt`  
 [out] Gibt eine neue [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Speicherkontext ist eine Adresse an, damit beim Hinzufügen eines Werts in eine Adresse erzeugt eine neue Adresse, die eine neue Context-Schnittstelle erforderlich sind.  
  
 Diese Methode muss immer einen neuen Kontext erzeugen, auch wenn die resultierende Adresse außerhalb des Speicherbereichs, der diesem Kontext zugeordnet ist. Die einzige Ausnahme hierbei ist, wenn keine "Erinnerung" für den neuen Kontext zugewiesen werden kann oder wenn `ppMemCxt` ist ein null-Wert (Dies ist ein Fehler).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)