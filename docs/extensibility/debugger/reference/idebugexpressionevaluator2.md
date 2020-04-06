---
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7041456bf0f3ae7930a73399d43dbf7cac6b3b32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729142"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt eine erweiterte Version eines Ausdrucksevaluators (EE) dar.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einem Ausdrucksevaluator implementiert.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden auf der [IDebugExpressionEvaluator-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Getservice](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Ruft ein Dienstobjekt mit seinem eindeutigen Bezeichner ab.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Lädt die vom angegebenen Symbolanbieter benannten Module vorab.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Ermöglicht dem Ausdrucksevaluator (EE), die Rückrufschnittstelle anzugeben, die das Debuggermodul (DE) zum Lesen von Metrikeinstellungen verwendet.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Legt den Pfad zur Common Language Runtime (CLR) fest, die im Debugger geladen wird.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Ermöglicht einem Debugmodul, während der Initialisierung einen Rückruf an den Ausdrucksevaluator zu übergeben.|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Beendet und bereinigt den Ausdrucksbewerter.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
