---
title: BP_LOCATION_CODE_STRING | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 2089fde7f063c9c394b3ff065445ca31d45241fc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319014"
---
# <a name="bplocationcodestring"></a>BP_LOCATION_CODE_STRING
Verwendet zum Festlegen von Code Breakpoints, die basierend auf einer Zeichenfolge, die der Benutzer aus der integrierten Entwicklungsumgebung (IDE) eingeben können.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Member
`bstrContext`\
Der Kontext der der Haltepunkt im Code, in der Regel eine Methode oder Funktion Namen wie für eine Aufrufliste.

`bstrCodeExpr`\
Die Zeichenfolge, der in der Benutzer eingibt, um die codehaltepunkt zu beschreiben.

## <a name="remarks"></a>Hinweise
Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
