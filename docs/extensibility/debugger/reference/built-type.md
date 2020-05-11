---
title: BUILT_TYPE | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737699"
---
# <a name="built_type"></a>BUILT_TYPE
Diese Struktur gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wird.

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
ID der Anwendung, aus der das Symbol stammt. Dies wird verwendet, um eine Instanz der Anwendung eindeutig zu identifizieren.

`guidModule`\
Die GUID des Moduls, das dieses Feld enthält.

`pUnderlyingField`\
Ein [IDebugField-Objekt,](../../../extensibility/debugger/reference/idebugfield.md) das das zugrunde liegende Feld identifiziert, das diesem erstellten Feld zugeordnet ist.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur angezeigt, wenn das `dwKind` Feld `TYPE_INFO` der Struktur auf `TYPE_KIND_BUILT` (ein Wert aus der [dwTYPE_KIND-Enumeration)](../../../extensibility/debugger/reference/dwtype-kind.md) festgelegt ist.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
