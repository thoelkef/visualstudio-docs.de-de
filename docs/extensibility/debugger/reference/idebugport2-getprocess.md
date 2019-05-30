---
title: IDebugPort2::GetProcess | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00579205a2e97d69f3a4305e09fac2146bb78d37
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326789"
---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
Ruft ab den angegebenen Prozess auf einem Port ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProcess( 
   AD_PROCESS_ID    ProcessId,
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess( 
   AD_PROCESS_ID      ProcessId,
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parameter
`ProcessId`\
[in] Ein [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) -Struktur, die Prozess-ID angibt.

`ppProcess`\
[out] Gibt eine [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Objekt, das den Prozess darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)