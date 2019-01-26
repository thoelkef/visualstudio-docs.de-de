---
title: IDebugSettingsCallback2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 24dd668c2a5877ab3fb674e4a8f46454b9f12e30
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55022169"
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