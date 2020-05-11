---
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f281ceb1f305c5774fedbf725f2e6a9481d073d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736595"
---
# <a name="idebugaddress"></a>IDebugAddress
Diese Schnittstelle stellt die Adresse eines Elements dar. Sie wird vom Symbolhandler zurückgegeben.

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle, um eine Adresse eines Objekts darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Viele Methoden auf vielen Schnittstellen geben diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Ruft eine [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur ab, die ein Objekt und dessen Speicherort beschreibt.|

## <a name="remarks"></a>Bemerkungen
 Der Symbolanbieter gibt diese Schnittstelle zurück, um ein Objekt und seine Position innerhalb eines bestimmten Bereichs (z. B. Funktion, Methode oder Klasse) darzustellen. Diese Schnittstelle wird von verschiedenen Methoden des Symbolanbieters und Ausdrucksevaluators zurückgegeben und an diese übergeben. Normalerweise ist der Symbolanbieter die einzige Entität, die den Inhalt dieser Schnittstelle interpretieren muss.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
