---
title: IDebugSettingsCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54724d3e7652df6f7b5b61099136286257fca954
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Ermöglicht das Debuggen Module zum Lesen von metrikeinstellungen Remote.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird durch den Ereignisrückruf des Debug-Sitzungsmanagers implementiert und von Debugmodule genutzt. Es kann auch lokal statt Dbgmetric [d] .lib verwendet werden.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugSettingsCallback2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Listet die verfügbaren ausdruckauswertung erhält die Sprache und Lieferanten-IDs an.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Ruft ein lokales Objekt Ausdrucksauswertungsfehler Ausdruck erhält die Metrik ab.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Ruft einen Wert, der die angegebene Metrik für die Auswertung eines Ausdrucks entspricht.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Ruft die Metrik Datei Ausdrucksauswertungsfehler Ausdruck erhält den Namen oder die Metrik ab.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Ruft den eindeutigen Bezeichner für eine Expression Evaluator Metrik angegebenen Namen ab.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Ruft den Wert ein Expression Evaluator Metrik angegebenen Namen ab.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Ruft den Wert einer Metrik mit dem angegebenen Namen ab.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Ruft den eindeutigen Bezeichner einer Metrik mit dem angegebenen Namen ab.|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Ruft den Wert für die Metrik mit dem angegebenen Namen ab.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Funktion, übernimmt ein **IDebugSettingsCallback2** -Objekt als Parameter.  
  
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