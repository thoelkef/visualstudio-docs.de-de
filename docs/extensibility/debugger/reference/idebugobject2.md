---
title: IDebugObject2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3f027fd08c38433d5f1357e56d90df96e223854
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317263"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle bietet zusätzliche Informationen zu einem Objekt.

## <a name="syntax"></a>Syntax

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die ausdrucksauswertung implementiert diese Schnittstelle, um Unterstützung für Aliase und den Zugriff auf Informationen über das Objekt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann diese Schnittstelle abrufen, indem Sie mithilfe von [QueryInterface](/cpp/atl/queryinterface). Darüber hinaus [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) dieser Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden für die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle, die `IDebugObject2` -Schnittstelle implementiert die folgenden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ruft ab, das Feld oder eine Variable (sofern vorhanden), die von diesem Objekt dargestellte Eigenschaft sichern.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ruft das verwaltetem Code-Objekt, das den Wert dieses Objekts darstellt.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Erstellt eine eindeutige ID für dieses Objekt fest oder gibt einen vorhandenen Alias.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ruft den Alias, der dieses Objekt zugeordnete ab, sofern vorhanden.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ruft den Typ dieses Objekts.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Bestimmt, ob dieses Objekt die Daten des Benutzers darstellt.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Bestimmt, ob der Status von bearbeiten und Fortfahren nicht mehr gültig ist.<br /><br /> Eine benutzerdefinierte ausdrucksauswertung diese Methode nicht implementiert (es sollte immer zurückgeben `E_NOTIMPL`).|

## <a name="remarks"></a>Hinweise
 Finden Sie unter [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) ausführliche Informationen zu Aliasen.

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)