---
title: FRAMEINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736784"
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
Eine Kombination von [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Flags aus der FRAMEINFO_FLAGS-Enumeration, die angibt, welche Felder ausgefüllt werden.

`m_bstrFuncName`\
Der dem Stapelrahmen zugeordnete Funktionsname.

`m_bstrReturnType`\
Der dem Stapelrahmen zugeordnete Rückgabetyp.

`m_bstrArgs`\
Die Argumente für die Funktion, die dem Stapelrahmen zugeordnet ist.

`m_bstrLanguage`\
Die Sprache, in der die Funktion implementiert wird.

`m_bstrModule`\
Der Modulname, der dem Stapelrahmen zugeordnet ist.

`m_addrMin`\
Die minimale physische Stapeladresse.

`m_addrMAX`\
Die maximale physische Stapeladresse.

`m_pFrame`\
Das [IDebugStackFrame2-Objekt,](../../../extensibility/debugger/reference/idebugstackframe2.md) das diesen Stapelrahmen darstellt.

`m_pModule`\
Das [IDebugModule2-Objekt,](../../../extensibility/debugger/reference/idebugmodule2.md) das das Modul darstellt, das diesen Stapelrahmen enthält.

`m_fHasDebugInfo`\
Ungleich Null`TRUE`( ), wenn Debuginformationen im angegebenen Frame vorhanden sind.

`m_fStaleCode`\
Nicht-Null`TRUE`( ), wenn der Stapelrahmen Code zugeordnet ist, der nicht mehr gültig ist.

`m_fAnnotatedFrame`\
Nicht-Null`TRUE`( ), wenn der Stapelrahmen vom Sitzungsdebug-Manager (SDM) mit Anmerkungen benotet wird.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird an die [GetInfo-Methode](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) übergeben, die ausgefüllt werden soll. Diese Struktur ist auch in einer Liste enthalten, die in der [IEnumDebugFrameInfo2-Schnittstelle](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) enthalten ist, die wiederum von einem Aufruf an die [EnumFrameInfo-Methode](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
