---
title: IDebugCustomViewer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fb70365304883abe99a87cfec5e78bbed89f2dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107539"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Diese Schnittstelle ermöglicht eine ausdrucksauswertung (EE) zum Anzeigen der Wert einer Eigenschaft in dem Format erforderlich ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein EE implementiert diese Schnittstelle, um den Wert einer Eigenschaft in einem benutzerdefinierten Format anzuzeigen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von COM `CoCreateInstance` Funktion instanziiert diese Schnittstelle. Die `CLSID` übergeben `CoCreateInstance` aus der Registrierung abgerufen wird. Ein Aufruf von [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Ruft die Position in der Registrierung ab. Details als auch das Beispiel finden Sie unter "Hinweise".  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Führt alle von Ihnen gewünschten zum Anzeigen eines bestimmten Werts erforderlich ist.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird verwendet, wenn der Wert einer Eigenschaft normales angezeigt werden kann – z. B. mit einer Datentabelle oder anderen komplexen Eigenschaft. Ein benutzerdefinierter Viewer, dargestellt durch die `IDebugCustomViewer` -Schnittstelle, unterscheidet sich von einer Schnellansicht Typ, der ein externes Programm zum Anzeigen von Daten eines bestimmten Typs unabhängig von der EE ist. Die EE implementiert einen benutzerdefinierten Viewer, der für diese EE spezifisch ist. Der Benutzer wählt den Typ der Schnellansicht zu verwenden, z. B. eine Schnellansicht Typ oder einem benutzerdefinierten Viewer. Finden Sie unter [Visualizing und Anzeige von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) Weitere Informationen zu diesem Vorgang.  
  
 Ein benutzerdefinierter Viewer auf die gleiche Weise wie eine EE registriert, und erfordert daher eine Sprach-GUID und einem Lieferanten GUID. Die genaue Metrik (oder der Name des Registrierungseintrags) wird nur für die EE bezeichnet. Diese Metrik wird zurückgegeben, der [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) -Struktur, die wiederum von einem Aufruf zurückgegebene [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). In der Metrik gespeicherte Wert ist die `CLSID` , das an COM übergeben wird `CoCreateInstance` -Funktion (siehe Beispiel).  
  
 Die [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Funktion `SetEEMetric`, kann verwendet werden, um einen benutzerdefinierten Viewer registrieren. Finden Sie im Registrierungsabschnitt "Ausdruckauswertung" `Debugging SDK Helpers` für den spezifischen Registrierungszeichenfolgen-Schlüssel muss ein benutzerdefinierter Viewer. Beachten Sie, dass ein benutzerdefinierter Viewer nur eine Metrik (die durch die EE Implementierer definiert wird), benötigt während eine ausdrucksauswertung mehrere vordefinierte Metriken erfordert.  
  
 In der Regel wird ein benutzerdefinierter Viewer stellt eine schreibgeschützte Ansicht der Daten, da die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle bereitgestellt, um [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) verfügt über keine Methoden zum Ändern der Eigenschaft Wert außer als Zeichenfolge. Damit ändern beliebige Datenblöcke unterstützt wird, implementiert die EE eine benutzerdefinierte Schnittstelle für das gleiche Objekt, das implementiert die `IDebugProperty3` Schnittstelle. Diese benutzerdefinierte Schnittstelle würde, geben Sie dann die Methoden zum Ändern eines beliebigen Blocks von Daten erforderlich sind.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie den ersten benutzerdefinierten Viewer aus einer Eigenschaft abzurufen, wenn diese Eigenschaft jeder benutzerdefinierte Viewer verfügt.  
  
```cpp  
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
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)