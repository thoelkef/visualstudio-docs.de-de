---
title: "IDebugExpressionContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2"
helpviewer_keywords: 
  - "IDebugExpressionContext2-Schnittstelle"
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Kontext für die Ausdrucksauswertung dar  
  
## Syntax  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um einen Kontext darstellt, in dem ein Ausdruck ausgewertet werden kann.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt die diese Schnittstelle zurück.  Diese Schnittstelle ist nur verfügbar, wenn das Programm, das gedebuggt wird, angehalten wurde und ein Stapelrahmen verfügbar ist.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugExpressionContext2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Ruft den Namen des Auswertungskontexts ab.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analysiert einen textbasierten Ausdruck für die Auswertung.|  
  
## Hinweise  
 Ein Auswertungs Elementkontext kann für einen Bereich für das Ausführen von Ausdrucksauswertung angesehen werden.  
  
 Wenn ein Programm angehalten wurde, erhält der Debug\- Manager der Sitzung \(SDM\) ein Stapelrahmen von DE mit einem Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  Das SDM ruft dann [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um die `IDebugExpressionContext2`\-Schnittstelle abzurufen.  Dies wird bei einem Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) befolgt, um eine [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)\-Schnittstelle zu erstellen, die den analysierten Ausdruck darstellt, der ausgewertet werden kann.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)