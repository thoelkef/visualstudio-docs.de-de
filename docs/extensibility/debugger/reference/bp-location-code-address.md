---
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: c215630e522adabdbd285e00d4bcd87cae22a931
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738037"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
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
Der Kontext des Haltepunkts, in der Regel ein Methoden- oder Funktionsname, wie er in einer Aufrufliste angezeigt wird.

`bstrModuleUrl`\
Die URL des Moduls, das den Haltepunkt enthält.

`bstrFunction`\
Der Name der Funktion, die den Haltepunkt enthält.

`bstrAddress`\
Die Adresse des Haltepunkts, der von einem Ausdrucksevaluator analysiert wird, um ihn an ein [IDebugAddress-Objekt](../../../extensibility/debugger/reference/idebugaddress.md) zu binden.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Gewerkschaft.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
