---
title: METADATA_ADDRESS_RETVAL | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ff96d5ca9d292d9e2952b9a2e5e1f628b54d43b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746349"
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
Diese Struktur stellt einen Rückgabewert aus einer Methode oder Funktion dar.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Member
 `tokMethod`\
 Die ID der Methode, die, der dieser Rückgabewert ist.

 `dwCorType`\
 Der Basistyp des Rückgabewerts. Dies ist ein Wert aus der `CorElementType` Enumeration, die in der Datei ".NET Framework SDK" corhdr.h "definiert.

 `dwSigSize`\
 Die Größe der Rückgabewert-Signatur (gespeichert in `rgSig`).

 `rgSig`\
 Ein Array von Bytes, die die Signatur des Rückgabewerts bilden.

## <a name="remarks"></a>Hinweise
 Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Kontostruktur, wenn die `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur nastaven NA hodnotu `ADDRESS_KIND_RETVAL` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) die Enumeration).

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)