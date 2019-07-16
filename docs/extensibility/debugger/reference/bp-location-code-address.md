---
title: BP_LOCATION_CODE_ADDRESS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 51137b5a5a69c80ecd7129d4c645f63b5805d27d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319127"
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
Beschreibt den Speicherort eines Haltepunkts an einer Adresse im Code.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Member
`bstrContext`\
Der Kontext des Haltepunkts, in der Regel eine Methode oder Funktion Namen wie für eine Aufrufliste.

`bstrModuleUrl`\
Die URL des Moduls, das den Breakpoint enthält.

`bstrFunction`\
Der Name der Funktion, die den Haltepunkt enthält.

`bstrAddress`\
Die Adresse des Breakpoints, die durch eine ausdrucksauswertung, bindet, bindet es an analysiert wird ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekt.

## <a name="remarks"></a>Hinweise
Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
