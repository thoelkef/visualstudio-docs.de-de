---
title: IDebugProgramPublisher2::SetDebuggerPresent | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: faa7263c3f5fa86a77c94271dec1b429d2f00543
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713463"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Teilt dem Verleger für die Anwendung mit, dass ein Debugger vorhanden ist und ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetDebuggerPresent(
   BOOL fDebuggerPresent
);
```

```csharp
int SetDebuggerPresent(
   int fDebuggerPresent
);
```

#### <a name="parameters"></a>Parameter
 `fDebuggerPresent`

 [in] Ungleich 0 (`TRUE`), wenn ein Debugger vorhanden ist, NULL (`FALSE`) ist dies nicht.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Das Vorhandensein oder fehlen eines Debuggers wird wiedergegeben, in der vom zurückgegebenen Daten die [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) Methode: Es zurückgegebene Wert festgelegt oder gelöscht, die von einem vorherigen Aufruf von der `SetDebuggerPresent` Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)