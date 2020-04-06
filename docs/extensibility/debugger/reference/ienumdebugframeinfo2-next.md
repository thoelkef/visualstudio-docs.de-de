---
title: IEnumDebugFrameInfo2::Weiter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Next
helpviewer_keywords:
- IEnumDebugFrameInfo2::Next
ms.assetid: 64a64eeb-5dea-4119-8a22-03771015d1e5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a5fe15c46066fdbc94b0b7f005ef7a06e1f10cc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716701"
---
# <a name="ienumdebugframeinfo2next"></a>IEnumDebugFrameInfo2::Next
Gibt den nächsten Satz von Elementen aus der Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Next(
   ULONG       celt,
   FRAMEINFO** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   FRAMEINFO[] rgelt,
   ref uint    pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale `rgelt` Größe des Arrays an.

`rgelt`\
[in, out] Array von [FRAMEINFO-Elementen,](../../../extensibility/debugger/reference/frameinfo.md) die ausgefüllt werden sollen.

`pceltFetched`\
[out] Gibt die Anzahl der `rgelt`tatsächlich in zurückgegebenen Elemente zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden konnte. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
