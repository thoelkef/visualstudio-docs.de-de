---
title: 'IEnumDebugCodeContexts2:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Next
helpviewer_keywords:
- IEnumDebugCodeContexts2::Next
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6e54b44d9e0ece42b65bf12412d6906158bc7fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717291"
---
# <a name="ienumdebugcodecontexts2next"></a>IEnumDebugCodeContexts2::Next
Gibt den nächsten Satz von Elementen aus der Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Next(
   ULONG                celt,
   IDebugCodeContext2** rgelt,
   ULONG*               pceltFetched
);
```

```csharp
int Next(
   uint                 celt,
   IDebugCodeContext2[] rgelt,
   ref uint             pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe des `rgelt` Arrays an.

`rgelt`\
[in, out] Array von [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Elementen, die ausgefüllt werden sollen.

`pceltFetched`\
vorgenommen Gibt die Anzahl der Elemente zurück, die tatsächlich in zurückgegeben werden `rgelt` .

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden kann. andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
