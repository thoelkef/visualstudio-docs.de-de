---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726075"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt zusätzliche Informationen zu einem Objekt bereit.

## <a name="syntax"></a>Syntax

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Ausdrucksauswertungsgeber implementiert diese Schnittstelle, um Unterstützung für Aliase und Zugriff auf Informationen über das Objekt zu bieten.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Eine [IDebugObject-Schnittstelle](../../../extensibility/debugger/reference/idebugobject.md) kann diese Schnittstelle mithilfe von [QueryInterface](/cpp/atl/queryinterface)abrufen. Außerdem gibt [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden auf der [IDebugObject-Schnittstelle](../../../extensibility/debugger/reference/idebugobject.md) implementiert die `IDebugObject2` Schnittstelle Folgendes:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ruft das Feld oder die Variable (falls vorhanden) ab, die die eigenschaft, die durch dieses Objekt dargestellt wird, unterstützen.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ruft das verwaltete Codeobjekt ab, das den Wert dieses Objekts darstellt.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Erstellt eine eindeutige ID für dieses Objekt oder gibt einen vorhandenen Alias zurück.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ruft den Alias ab, der diesem Objekt zugeordnet ist, falls vorhanden.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ruft den Typ dieses Objekts ab.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Bestimmt, ob dieses Objekt Benutzerdaten darstellt.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Bestimmt, ob der Status Bearbeiten und Fortsetzen nicht mehr gültig ist.<br /><br /> Ein benutzerdefinierter Ausdrucksauswertungswertimplementierte Methode (sie sollte immer zurückgegeben `E_NOTIMPL`werden).|

## <a name="remarks"></a>Bemerkungen
 Eine Diskussion über Aliase finden Sie unter [IDebugAlias.](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [Getobject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
