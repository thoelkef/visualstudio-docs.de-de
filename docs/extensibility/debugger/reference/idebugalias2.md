---
title: IDebugAlias2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abd220cd8c67318981fda79d3be8a0014ab61de1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321724"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Stellt einen numerischen Alias für eine Variable dar und ermöglicht eine ausdrucksauswertung (EE), um die Anwendungsdomäne für den Alias zu erhalten.

## <a name="syntax"></a>Syntax

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von der verwalteten Debug-Engine (DE) implementiert.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) Schnittstelle, die diese Schnittstelle implementiert, die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Ruft den Bezeichner für die Anwendungsdomäne ab.|

## <a name="remarks"></a>Hinweise
 Ein Alias ist eine Dezimalzahl in Form einer Zeichenfolge gefolgt von dem #-Zeichen ein, z. B. 1001#.

## <a name="requirements"></a>Anforderungen
 Header: EE.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll