---
title: BUILT_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737699"
---
# <a name="built_type"></a>BUILT_TYPE
Diese Struktur gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wurde.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Member
`ulAppDomainID`\
Die ID der Anwendung, von der das Symbol stammt. Hiermit wird eine Instanz der Anwendung eindeutig identifiziert.

`guidModule`\
Der GUID des Moduls, das dieses Feld enthält.

`pUnderlyingField`\
Ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das das zugrunde liegende Feld identifiziert, das diesem erstellten Feld zugeordnet ist.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) -Struktur angezeigt, wenn das- `dwKind` Feld der- `TYPE_INFO` Struktur auf festgelegt ist `TYPE_KIND_BUILT` (ein Wert aus der [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Enumeration).

## <a name="requirements"></a>Requirements (Anforderungen)
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
