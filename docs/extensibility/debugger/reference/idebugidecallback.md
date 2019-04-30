---
title: IDebugIDECallback | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdbc1cc5a8f7534f2ee11699d67b4128796602c6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413987"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ermöglicht eine ausdrucksauswertung (EE), um eine Meldung im Ausgabefenster des Debuggers anzuzeigen.

## <a name="syntax"></a>Syntax

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Dieser Rückruf wird durch die verwalteten Debug-Engine implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Sie können durch eine ausdrucksauswertung, die zum Senden der Ausgabe an das debuggerausgabefenster genutzt werden.

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Sendet die angegebenen Meldungszeichenfolge Ausgabefenster des Debuggers.|

## <a name="requirements"></a>Anforderungen
 Header: EE.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll