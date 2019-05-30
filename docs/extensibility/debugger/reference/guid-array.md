---
title: GUID_ARRAY | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d53413ee56700fe39470d3bbc3229f4b8b668373
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317532"
---
# <a name="guidarray"></a>GUID_ARRAY
Ein Array von eindeutigen Bezeichnern für verfügbare Debug-Engines beschreibt.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>Member
`dwCount`\
Die Anzahl von eindeutigen Bezeichnern im Array.

`Members`\
Array, das eindeutige Bezeichner enthält.

## <a name="remarks"></a>Hinweise
Diese Struktur wird zurückgegeben, durch die [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: Msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
