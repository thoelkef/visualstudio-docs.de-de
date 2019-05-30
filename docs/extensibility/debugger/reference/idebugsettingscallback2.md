---
title: IDebugSettingsCallback2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 859522ebdbe231146c73b25c5e4c92fba9809727
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321942"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Ermöglicht das debug-Engines zum Lesen von metrikeinstellungen Remote.

## <a name="syntax"></a>Syntax

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Diese Schnittstelle wird durch den Ereignisrückruf von sitzungsbasierter Debug-Manager implementiert und von Debug-Engines genutzt werden. Er kann auch lokal anstatt Dbgmetric [d]-lib verwendet werden.

## <a name="methods"></a>Methoden
Die folgende Tabelle zeigt die Methoden der `IDebugSettingsCallback2`.

|Methode|Beschreibung|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Listet die verfügbaren ausdrucksauswertungen die Sprache und den Anbieter-IDs angegeben.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Ruft ein lokales Objekt Ausdrucksauswertungsfehler Ausdruck erhält die Metrik ab.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Ruft einen Wert, der die angegebene Metrik von der ausdrucksauswertung entspricht.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Ruft die Expression Evaluator Metrik Datei erhält den Namen oder die Metrik ab.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Ruft den eindeutigen Bezeichner für eine Expression Evaluator-Metrik, die anhand des Namens ab.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Ruft den Wert von einer Expression Evaluator-Metrik anhand des Namens ab.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Ruft den Wert einer Metrik anhand des Namens.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Ruft den eindeutigen Bezeichner für eine Metrik mit dem angegebenen Namen ab.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Ruft den Wert der Metrik anhand des Namens ab.|

## <a name="requirements"></a>Anforderungen
Header: Msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Funktion, verwendet eine **IDebugSettingsCallback2** -Objekt als Parameter.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
