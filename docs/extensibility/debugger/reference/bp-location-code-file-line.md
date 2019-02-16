---
title: BP_LOCATION_CODE_FILE_LINE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ab7a0b226b7a8fac779e5c5109700a37e60d9d0
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315702"
---
# <a name="bplocationcodefileline"></a>BP_LOCATION_CODE_FILE_LINE
Enthält die Daten für den Speicherort eines Haltepunkts an einer bestimmten Zeile in einer Code-Quelldatei.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>Member
`bstrContext`  
Der Kontext des Haltepunkts, in der Regel eine Methode oder Funktion Namen wie für eine Aufrufliste.

`pDocPos`  
Die [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) -Objekt, die Dokumentposition des Haltepunkts darstellt.

## <a name="remarks"></a>Hinweise
Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
