---
title: Parameeflags | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
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
 Übergeben als Parameter an [die Methoden "](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) [Parametertext](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) " und "Analyse".

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
