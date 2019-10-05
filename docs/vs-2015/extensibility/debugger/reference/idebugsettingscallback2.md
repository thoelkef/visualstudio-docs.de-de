---
title: IDebugSettingsCallback2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3e962c00d6c9230cab765ed56e7607cbfd91765
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153143"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
```cpp#  
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
