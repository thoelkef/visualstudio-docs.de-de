---
title: FIELD_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b34624672b64d88ca9b080094c5d661494c089cf
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315897"
---
# <a name="fieldinfo"></a>FIELD_INFO
Diese Struktur wird eine lokale Variable, Parameter oder andere Feld beschrieben.

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
dwFields  
Eine Kombination von Flags aus der [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Enumeration, der angibt, welche Elemente ausgefüllt werden.

bstrFullName  
Der vollständige Name des Felds.

bstrName  
Der kurze Name des Felds.

bstrType  
Der Typ des Felds.

dwModifiers  
Eine Kombination von Flags aus der [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) -Enumeration, die das Feld beschreibt.

## <a name="remarks"></a>Hinweise
Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) Methode, in denen es ausgefüllt wird.

## <a name="requirements"></a>Anforderungen
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)  
[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)  
[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
