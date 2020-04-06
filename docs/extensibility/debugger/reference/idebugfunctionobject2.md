---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4150480d2e6686992d78727b6fed817da270145
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728430"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt eine Funktion dar und erweitert die [IDebugFunctionObject-Schnittstelle.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Ausdrucksevaluator (EE) implementiert diese Schnittstelle, um eine Funktion darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Methoden dieser Schnittstelle verschieben die von **IDebugFunctionObject** auf folgende Weise:

- Die **IDebugEvaluate-Methode** nimmt Flags an.

- Die **CreateObject-Methode** nimmt Flags und ein Timeout an.

- Die **CreateStringObjectWithLength-Methode** hat eine Länge.

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Erstellt ein Objekt, das einen Konstruktor mit angegebenen Auswertungsflageinstellungen und einem Timeoutwert verwendet.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Erstellt ein Zeichenfolgenobjekt mit der angegebenen Länge.|
|[Auswerten](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Ruft die Funktion auf und gibt den resultierenden Wert als Objekt zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
