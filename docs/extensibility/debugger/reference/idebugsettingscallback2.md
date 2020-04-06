---
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c85b54f92970dca5d712b827019300f850b03cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719942"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Ermöglicht Debug-Modulen das Remotelesen von Metrikeinstellungen.

## <a name="syntax"></a>Syntax

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Diese Schnittstelle wird durch den Ereignisrückruf des Sitzungsdebug-Managers implementiert und von Debugmodulen verwendet. Es könnte auch lokal anstelle von Dbgmetric[d].lib verwendet werden.

## <a name="methods"></a>Methoden
Die folgende Tabelle zeigt `IDebugSettingsCallback2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Zählt die verfügbaren Ausdrucksauswertungen auf, die die Sprach- und Kreditorenbezeichner erhalten.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Ruft ein lokales Objekt des Ausdrucksauswertungsobjekts ab, das die Metrik enthält.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Ruft einen Wert ab, der der angegebenen Metrik des Ausdrucksauswertungswerts entspricht.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Ruft die Metrikdatei für ausdrucksauswertungswerter unter Angabe des Namens oder der Metrik ab.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Ruft den eindeutigen Bezeichner für eine Ausdrucksauswertungsmetrik mit dem Namen ab.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Ruft die Wertzeichenfolge einer Ausdrucksauswertungsmetrik mit ihrem Namen ab.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Ruft den Wert einer Metrik ab, die ihren Namen angegeben hat.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Ruft den eindeutigen Bezeichner einer Metrik ab, die ihren Namen angegeben hat.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Ruft die Wertzeichenfolge der Metrik ab, die ihren Namen angegeben hat.|

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: Msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Funktion, die ein **IDebugSettingsCallback2-Objekt** als Parameter verwendet.

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
