---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cc70fdd9fe1279e4d419a422b970eb3d3b07c65
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714117"
---
# <a name="parseflags"></a>PARSEFLAGS
Gibt an, wie ein Ausdruck analysiert wird.

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

## <a name="fields"></a>Felder
 `PARSE_EXPRESSION`\
 Gibt an, dass der Ausdruck keine Anweisung ist.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Gibt an, dass der Ausdruck als Adresse analysiert (und später ausgewertet) werden soll.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Gibt an, dass der Ausdruck während der Entwurfszeit analysiert wird (d. h., wenn ein Designer geöffnet ist).

## <a name="remarks"></a>Bemerkungen
 Wird als Parameter an die [ParseText-](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) und [Parse-Methoden](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) übergeben.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
