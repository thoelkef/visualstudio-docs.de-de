---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727830"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ermöglicht einem Ausdrucksevaluator (EE), eine Meldung im Ausgabefenster des Debuggers anzuzeigen.

## <a name="syntax"></a>Syntax

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Dieser Rückruf wird vom verwalteten Debugmodul implementiert.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Es kann von einem Ausdrucksevaluator verwendet werden, um die Ausgabe an das Ausgabefenster des Debuggers zu senden.

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Sendet die angegebene Nachrichtenzeichenfolge an das Ausgabefenster des Debuggers.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
