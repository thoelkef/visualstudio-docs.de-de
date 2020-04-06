---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736228"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt ein verwaltetes Arrayobjekt dar und ermöglicht es einem Ausdrucksevaluator (EE), den Basisindex (untere Grenzen) für das Array zu bestimmen.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Dies wird vom Managed Debug Engine (DE) implementiert.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden auf der [IDebugArrayObject-Schnittstelle](../../../extensibility/debugger/reference/idebugarrayobject.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Ruft die Basisindizes (untere Grenzen) für jeden Index ab, wenn die Anzahl der Dimensionen im Array angegeben wird.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Legt fest, ob für das Array Basisindizes (untere Grenzen) definiert sind.|

## <a name="remarks"></a>Bemerkungen
 Ein Ausdrucksauswertungsgeber verwendet diese Schnittstelle, um verwaltete Arrays in einer Analysestruktur darzustellen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
