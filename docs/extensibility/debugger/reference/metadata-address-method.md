---
title: METADATA_ADDRESS_METHOD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc3dd7a34e4f9a3e1b933781aeaf4e18cad7ec17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714452"
---
# <a name="metadata_address_method"></a>METADATA_ADDRESS_METHOD
Diese Struktur stellt die Adresse einer Methode einer Klasse dar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>Member
 `tokMethod`\
 Die ID der Methode.

 [C++] `_mdToken` ist `typedef` ein für eine `int`32-Bit .

 `dwOffset`\
 Der Offset vom Klassenstart zu dieser Methode (kann den Offset in die vtable darstellen).

 `dwVersion`\
 Die Version der Methode (dieser Wert ist für den Symbolanbieter eindeutig).

## <a name="remarks"></a>Bemerkungen
 Diese Struktur ist Teil der Union in `dwKind` der `DEBUG_ADDRESS_UNION` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, `ADDRESS_KIND_METHOD` wenn das Feld der Struktur auf (ein Wert aus der ADDRESS_KIND-Enumeration) festgelegt ist. [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
