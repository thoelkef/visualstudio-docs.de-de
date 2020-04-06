---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737968"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Wird zum Festlegen von Datenhaltepunkten verwendet, die auf einer Zeichenfolge basieren, die der Benutzer aus der integrierten Entwicklungsumgebung (IDE) eingeben kann.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Member
`pThread`\
Das [IDebugThread2-Objekt,](../../../extensibility/debugger/reference/idebugthread2.md) das den Thread darstellt, auf dem der Haltepunkt auftritt.

`bstrContext`\
Der Kontext des Haltepunkts innerhalb des Codes, in der Regel ein Methoden- oder Funktionsname, wie er in einer Aufrufliste angezeigt wird.

`bstrDataExpr`\
Die Datenzeichenfolge, die der Benutzer eingibt, um den Haltepunkt festzulegen.

`dwNumElements`\
Die Anzahl der Elemente in der Datenzeichenfolge, in der der Haltepunkt auftritt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Gewerkschaft.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
