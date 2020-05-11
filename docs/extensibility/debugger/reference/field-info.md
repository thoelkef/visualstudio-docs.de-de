---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e2089746adecc583d04176afca18ad19826ea53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736896"
---
# <a name="field_info"></a>FIELD_INFO
Diese Struktur beschreibt eine lokale Variable, einen Parameter oder ein anderes Feld.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Kombination von [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Flags aus der FIELD_INFO_FIELDS-Enumeration, die angibt, welche Elemente ausgefüllt werden.

`bstrFullName`\
Der vollständige Name des Felds.

`bstrName`\
Der kurze Name des Felds.

`bstrType`\
Der Typ des Felds.

`dwModifiers`\
Eine Kombination von [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Flags aus der FIELD_MODIFIERS-Enumeration, die das Feld beschreibt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird an die [GetInfo-Methode](../../../extensibility/debugger/reference/idebugfield-getinfo.md) übergeben, bei der sie ausgefüllt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
