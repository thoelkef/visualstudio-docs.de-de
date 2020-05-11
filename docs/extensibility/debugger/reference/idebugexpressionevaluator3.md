---
title: IDebugExpressionEvaluator3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d25cd8cd4aec351df2a483e930bf469fbc086a68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729113"
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt einen Ausdrucksevaluator (EE) mit einer erweiterten Parserstruktur dar.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2
```

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Version des Parsers übergibt den Symbolanbieter und die Adresse des auswertenden Frames.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden auf der [IDebugExpressionEvaluator2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Konvertiert eine Ausdruckszeichenfolge in einen analysierten Ausdruck, der den Symbolanbieter und die Adresse des auswertenden Frames angibt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
