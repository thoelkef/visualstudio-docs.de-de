---
title: PARSEFLAGS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7192483b4f2ce88235fc5e8d48f1d51ef71b442f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913006"
---
# <a name="parseflags"></a>PARSEFLAGS
Gibt an, wie einen Ausdruck zu analysieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Member  
 PARSE_EXPRESSION  
 Gibt an, dass der Ausdruck keine Anweisung ist.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Gibt an, dass der Ausdruck analysiert (und später ausgewertet werden) als eine Adresse.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Gibt an, dass während der Entwurfszeit der Ausdruck analysiert wird (d. h. bei ein Designer geöffnet ist).  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Parameter an die [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) und [analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) Methoden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Auslesen](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)