---
title: FRAMEINFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1209036bced88cffb3681be0ceedd28942714419
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344465"
---
# <a name="frameinfo"></a>FRAMEINFO
Beschreibt einen Stapelrahmen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Member
`m_dwValidFields`\
Eine Kombination von Flags aus der [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Enumeration, der angibt, welche Felder ausgefüllt werden.

`m_bstrFuncName`\
Der Funktionsname, die dem Stapelrahmen zugeordnet wird.

`m_bstrReturnType`\
Der Rückgabetyp, die dem Stapelrahmen zugeordnet.

`m_bstrArgs`\
Die Argumente der Funktion, die dem Stapelrahmen zugeordnet werden soll.

`m_bstrLanguage`\
Die Sprache, in der die Funktion implementiert wird.

`m_bstrModule`\
Der Modulname, die dem Stapelrahmen zugeordnet wird.

`m_addrMin`\
Die minimale physischen Stapel-Adresse.

`m_addrMAX`\
Die maximale physischen Stapel-Adresse.

`m_pFrame`\
Die [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Objekt, das diesen Stapelrahmen darstellt.

`m_pFrame`\
Die [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Objekt, das Modul darstellt, die diesen Stapelrahmen enthält.

`m_fHasDebugInfo`\
Ungleich 0 (`TRUE`) ob Debuginformationen im angegebenen Bereich vorhanden ist.

`m_fHasDebugInfo`\
Ungleich 0 (`TRUE`) Wenn der Stapelrahmen Code zugeordnet ist, die nicht mehr gültig ist.

`m_fHasDebugInfo`\
Ungleich 0 (`TRUE`), wenn die Stapelrahmen von sitzungsbasierter Debug-Manager (SDM) versehen ist.

## <a name="remarks"></a>Hinweise
Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) Methode gefüllt werden soll. Diese Struktur befindet sich in einer Liste, der in enthalten ist auch die [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Schnittstelle, die wiederum von einem Aufruf zurückgegeben wird das [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
