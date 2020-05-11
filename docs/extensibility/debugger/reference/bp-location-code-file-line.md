---
title: BP_LOCATION_CODE_FILE_LINE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: e338c3b24ade2cf7663b77abea64f58425d3a068
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738016"
---
# <a name="bp_location_code_file_line"></a>BP_LOCATION_CODE_FILE_LINE
Enthält die Daten für den Speicherort eines Haltepunkts in einer bestimmten Zeile in einer Codequelldatei.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>Member
`bstrContext`\
Der Kontext des Haltepunkts, in der Regel ein Methoden- oder Funktionsname, wie er in einer Aufrufliste angezeigt wird.

`pDocPos`\
Das [IDebugDocumentPosition2-Objekt,](../../../extensibility/debugger/reference/idebugdocumentposition2.md) das die Dokumentposition des Haltepunkts darstellt.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Gewerkschaft.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
