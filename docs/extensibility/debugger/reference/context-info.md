---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737567"
---
# <a name="context_info"></a>CONTEXT_INFO
Diese Struktur beschreibt einen Speicherkontext oder Codekontext.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Kombination von Flags aus der CONTEXT_INFO_FIELDS-Enumeration, die angibt, welche Felder ausgefüllt<strong>werden.</strong> [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)

`bstrModuleUrl`\
Der Name des Moduls, in dem sich der Kontext befindet.

`bstrFunction`\
Der Funktionsname, in dem sich der Kontext befindet.

`posFunctionOffset`\
Eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die den Zeilen- und Spaltenversatz der Funktion identifiziert, die dem Codekontext zugeordnet ist.

`bstrAddress`\
Die Adresse im Code, an der sich der angegebene Kontext befindet.

`bstrAddressOffset`\
Der Offset der Adresse im Code, in dem sich der angegebene Kontext befindet.

`bstrAddressAbsolute`\
Die absolute Adresse im Speicher, an der sich der angegebene Kontext befindet.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von einem Aufruf der [GetInfo-Methode](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) zurückgegeben.

Eine typische Verwendung für diese Struktur **Memory** wird in Unterstützung eines Speicherdebugfensters verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
