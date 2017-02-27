---
title: "IDebugCustomViewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer"
helpviewer_keywords: 
  - "IDebugCustomViewer-Schnittstelle"
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht einem Ausdrucksauswertung \(EE\), um einen Eigenschaftswert in anzuzeigen, welche Format erforderlich ist.  
  
## Syntax  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## Hinweise für Implementierer  
 Eine EE implementiert diese Schnittstelle, um den Wert einer Eigenschaft in einem benutzerdefinierten Format anzeigen.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von `CoCreateInstance`\-Funktion COM instanziiert diese Schnittstelle.  `CLSID` , das `CoCreateInstance` übergeben wird, wird von der Registrierung abgerufen.  Ein Aufruf von [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) erhält der Position in der Registrierung.  Siehe Hinweise zur Details sowie das Beispiel.  
  
## Methoden in die Vtable\-Reihenfolge  
 Diese Schnittstelle implementiert die folgende Weise:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Hat, was erforderlich ist, um einen angegebenen Wert anzuzeigen.|  
  
## Hinweise  
 Diese Schnittstelle wird verwendet, wenn der Wert einer Eigenschaft über keine normal Mittel\-für Beispiel mit einer Datentabelle oder einem anderen komplexen Eigenschaftentyp angezeigt werden kann.  Ein benutzerdefinierter Viewer, wie durch die `IDebugCustomViewer`\-Schnittstelle dargestellt, ist eine schnellansicht Typ unterscheiden, die ein externes Programm zum Anzeigen von Daten eines bestimmten Typs unabhängig von der EE ist.  Die EE implementiert einen benutzerdefinierten Viewer, der auf diese EE spezifisch sind.  Ein Benutzer wählt aus, der Typ, sei es sich um eine schnellansicht Typ oder einen benutzerdefinierten Viewer verwenden der Schnellansicht.  [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) finden Sie Einzelheiten über diesen Prozess.  
  
 Ein benutzerdefinierter Viewer wird auf die gleiche Weise wie eine EE registriert und daher eine Sprache GUID und einen Anbieter GUID erfordert.  Die genaue Metriken \(oder der Name des Registrierungseintrags\) bekannt ist nur in der EE.  Diese Metrik ist in der [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Struktur zurückgegeben, die wiederum durch einen Aufruf von [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)zurückgegeben wurde.  Der Wert, der in der Metriken gespeichert ist, wird `CLSID` , die `CoCreateInstance`\-Funktion COM übergeben wird \(siehe Beispiel\).  
  
 Die [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)`SetEEMetric`Funktion kann verwendet werden, um einen benutzerdefinierten Viewer zu registrieren.  Weitere Informationen finden Sie im Abschnitt „Ausdrucksauswertung“ Registrierung von `Debugging SDK Helpers` für die bestimmten Registrierungsschlüssel, die einen benutzerdefinierten Viewer erfordert.  Beachten Sie, dass ein benutzerdefinierter Viewer nur eine Metrik erfordert \(die durch die Implementierung der EE definiert ist\), während der Ausdrucksauswertung eine Reihe vordefinierter Metriken erfordert.  
  
 Normalerweise stellt einen benutzerdefinierten Viewer eine schreibgeschützte Ansicht der Daten, da die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)\-Schnittstelle, die [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) angegeben wird, keine Methoden zum Ändern des Werts der Eigenschaft außer als Zeichenfolge aufweist.  Zum Ändern von Blöcken, beliebige Daten zu unterstützen, implementiert die EE eine benutzerdefinierte Schnittstelle für dasselbe Objekt, das die `IDebugProperty3`\-Schnittstelle implementiert.  Diese benutzerdefinierte Schnittstelle würde dann die Methoden bereitstellen, die benötigt wurden, um einen beliebigen Block Daten zu ändern.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Beispiel  
 Dieses Beispiel zeigt, wie Sie den ersten benutzerdefinierten Viewer aus einer Eigenschaft abruft, wenn diese Eigenschaft über benutzerdefinierten Viewer verfügt.  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)