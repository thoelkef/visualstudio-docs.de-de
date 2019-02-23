---
title: IDebugArrayObject2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89130c43e38bc53e0efeb93325df94e7076d9ef1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691955"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt ein verwaltetes Array-Objekt dar und ermöglicht eine ausdrucksauswertung (EE), um zu bestimmen, den Basisindex (untere Grenzen) für das Array.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Dies wird von der verwalteten Debug-Engine (DE) implementiert.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Ruft den Basis-Indizes (untere Grenzen) für jeden Index in Anbetracht der Anzahl der Dimensionen im Array ab.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Bestimmt, ob das Array Basis Indizes (untere Grenzen) definiert hat.|

## <a name="remarks"></a>Hinweise
 Eine ausdrucksauswertung verwendet diese Schnittstelle zum Darstellen von verwalteten Arrays in eine Analysestruktur.

## <a name="requirements"></a>Anforderungen
 Header: EE.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll