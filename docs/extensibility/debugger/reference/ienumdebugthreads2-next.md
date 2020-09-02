---
title: 'IEnumDebugThreads2:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Next
helpviewer_keywords:
- IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc6c493c211da3dc69e25b20c0a79b4dcabd1ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715163"
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
Gibt den nächsten Satz von Elementen aus der Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugThread2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugThread2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe des `rgelt` Arrays an.

`rgelt`\
[in, out] Array von [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Elementen, die ausgefüllt werden sollen.

`pceltFetched`\
vorgenommen Gibt die Anzahl der Elemente zurück, die tatsächlich in zurückgegeben werden `rgelt` .

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden kann. andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
