---
title: REFERENCE_COMPARE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2aa9e7c608c4aabdbb808629112b922a5ed3322e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713729"
---
# <a name="reference_compare"></a>REFERENCE_COMPARE
Gibt den Typ des Vergleichs für Verweise an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
typedef DWORD REFERENCE_COMPARE;
```

```csharp
public enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
```

## <a name="fields"></a>Felder
 `REF_COMPARE_EQUAL`\
 Gibt einen Gleichheits Vergleich an.

 `REF_COMPARE_LESS_THAN`\
 Gibt einen kleiner-als-Vergleich an.

 `REF_COMPARE_GREATER_THAN`\
 Gibt einen größer-als-Vergleich an.

## <a name="remarks"></a>Bemerkungen
 Als Argument an die [Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md) -Methode übergebenen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Vergleichen](../../../extensibility/debugger/reference/idebugreference2-compare.md)
