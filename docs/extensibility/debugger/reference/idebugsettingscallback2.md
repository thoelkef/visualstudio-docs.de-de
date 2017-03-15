---
title: "IDebugSettingsCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2-Schnittstelle"
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Aktiviert Debuggen von Modulen, um metrische Einstellungen remote zu lesen.  
  
## Syntax  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von den Rückruf Ereignis Debuggen des Managers der Sitzung implementiert und Module Debuggen von genutzt.  Er kann anstelle Dbgmetric \[d\] .lib außerdem lokal verwendet werden.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugSettingsCallback2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Listet die verfügbaren Sprach\- und Anbieter die Ausdrucksauswertung angegebenen Bezeichner.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Ruft ein lokales angegebenes Objekt des Ausdrucksauswerters die Metrik ab.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Ruft einen Wert ab, der der angegebenen Metriken des Ausdrucksauswerters entspricht.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Ruft das metrische angegebene Datei des Ausdrucksauswerters der Name oder die Metrik ab.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Ruft den eindeutigen Bezeichner für ein metrisches angegebenes des Ausdrucksauswerters ihr Name ab.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Ruft die Zeichenfolge des Werts von einem metrischen angegebenen des Ausdrucksauswerters Name ab.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Ruft den Wert eines metrischen angegebene Name ab.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Ruft den eindeutigen Bezeichner für einen metrischen angegebene Name ab.|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Ruft die Zeichenfolge des Werts von metrischen angegebene Name ab.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Beispiel  
 Im folgenden Beispiel wird eine Funktion veranschaulicht, die ein Objekt **IDebugSettingsCallback2** als Parameter akzeptiert.  
  
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