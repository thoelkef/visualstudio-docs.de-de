---
title: REFERENCE_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ce6ad17aa32b98fd28914c422a49bd8bcc14b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713655"
---
# <a name="reference_type"></a>REFERENCE_TYPE
Gibt den Verweistyp an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
typedef DWORD REFERENCE_TYPE;
```

```csharp
public enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
```

## <a name="fields"></a>Felder
 `REF_TYPE_WEAK`\
 Gibt einen schwachen Verweis an. Kann nicht mit kombiniert werden `REF_TYPE_STRONG` .

 `REF_TYPE_STRONG`\
 Gibt einen starken Verweis an. Kann nicht mit kombiniert werden `REF_TYPE_WEAK` .

## <a name="remarks"></a>Bemerkungen
 Wird als `dwRefType` Member der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) -Struktur verwendet.

 Übergeben als Parameter an [die Methode "](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) " der Methode "" von "".

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
