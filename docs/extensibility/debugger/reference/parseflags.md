---
title: PARSEFLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ba1933d1b63f9af863b115972f3ecf1dfc4346
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913715"
---
# <a name="parseflags"></a>PARSEFLAGS
Gibt an, wie einen Ausdruck zu analysieren.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="members"></a>Member
 PARSE_EXPRESSION gibt an, dass der Ausdruck keine Anweisung ist.

 PARSE_FUNCTION_AS_ADDRESS gibt an, der Ausdruck analysiert (und später ausgewertet werden) als eine Adresse.

 PARSE_DESIGN_TIME_EXPR_EVAL gibt an, dass während der Entwurfszeit der Ausdruck analysiert wird (d. h. bei ein Designer geöffnet ist).

## <a name="remarks"></a>Hinweise
 Übergeben als Parameter an die [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) und [analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) Methoden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Auslesen](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)