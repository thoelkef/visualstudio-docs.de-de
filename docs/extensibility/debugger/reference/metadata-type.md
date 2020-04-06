---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714290"
---
# <a name="metadata_type"></a>METADATA_TYPE
Diese Struktur gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parameter
 `ulAppDomainID`\
 ID der Anwendung, aus der das Symbol stammt. Dies wird verwendet, um eine Instanz der Anwendung eindeutig zu identifizieren.

 `guidModule`\
 Die GUID des Moduls, das dieses Feld enthält.

 `tokClass`\
 Die Metadatentoken-ID dieses Typs.

 [C++] `_mdToken` ist `typedef` ein für eine `int`32-Bit .

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird als Teil der Union in der [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur angezeigt, wenn das `dwKind` Feld `TYPE_INFO` der Struktur auf `TYPE_KIND_METADATA` (ein Wert aus der [dwTYPE_KIND-Enumeration)](../../../extensibility/debugger/reference/dwtype-kind.md) festgelegt ist.

 Der `tokClass` Wert ist ein Metadatentoken, das einen Typ eindeutig identifiziert. Weitere Informationen zum Interpretieren der oberen Bits der Metadatentoken-ID finden Sie in der `CorTokenType` Enumeration in der Datei corhdr.h im .NET Framework SDK.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
