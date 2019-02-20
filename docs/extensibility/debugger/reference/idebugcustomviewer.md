---
title: IDebugCustomViewer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8594d8848aae4fd69c5ea65eb69005035a6c4527
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413240"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Diese Schnittstelle ermöglicht eine ausdrucksauswertung (EE) den Wert einer Eigenschaft im benötigten Format angezeigt werden.

## <a name="syntax"></a>Syntax

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein EE implementiert diese Schnittstelle, um den Wert einer Eigenschaft in einem benutzerdefinierten Format angezeigt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Ein Aufruf von COM `CoCreateInstance` Funktion instanziiert diese Schnittstelle. Die `CLSID` übergeben `CoCreateInstance` aus der Registrierung abgerufen wird. Ein Aufruf von [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Ruft die Position in der Registrierung. Details als auch für das Beispiel finden Sie unter "Hinweise".

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Diese Schnittstelle implementiert die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Führt den zum Anzeigen eines bestimmten Werts erforderlich ist.|

## <a name="remarks"></a>Hinweise
Diese Schnittstelle wird verwendet, wenn der Wert einer Eigenschaft, die normale Art und Weise angezeigt werden kann, z. B. mit einer Tabelle oder einen anderen Typ der komplexen Eigenschaft. Ein benutzerdefinierter Viewer, dargestellt durch die `IDebugCustomViewer` Schnittstelle, unterscheidet sich von einer typschnellansicht, ein externes Programm zum Anzeigen von Daten eines bestimmten Typs unabhängig von der EE handelt. Die EE implementiert einen benutzerdefinierten Viewer, der für diese EE spezifisch ist. Der Benutzer wählt den Typ der Schnellansicht verwenden, sei es eine typschnellansicht oder einem benutzerdefinierten Viewer. Finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) für Informationen zu diesem Prozess.

Ein benutzerdefinierter Viewer in die gleiche Weise wie eine EE registriert ist und aus diesem Grund erfordert eine Sprachen-GUID und eine Anbieter-GUID. Die exakte Metrik (oder der Name des Registrierungseintrags) wird nur für die EE bezeichnet. Mit dieser Metrik wird zurückgegeben, der [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) -Struktur, die wiederum von einem Aufruf zurückgegeben wird [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). In der Metrik gespeicherte Wert ist die `CLSID` COM übergebene `CoCreateInstance` funktionieren (siehe Beispiel).

Die [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Funktion `SetEEMetric`, kann verwendet werden, um einen benutzerdefinierten Viewer zu registrieren. Finden Sie im Registrierungsabschnitt "Ausdrucksauswertungen" `Debugging SDK Helpers` für den spezifischen Registrierungszeichenfolgen-Schlüssel muss ein benutzerdefinierter Viewer. Beachten Sie, dass ein benutzerdefinierter Viewer nur eine Metrik (definiert durch die EE Implementierung), benötigt während eine ausdrucksauswertung mehrere vordefinierte Metriken erfordert.

In der Regel ein benutzerdefinierter Viewer stellt eine schreibgeschützte Ansicht der Daten, da die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle bereitgestellt, um [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) verfügt über keine Methoden zum Ändern der Wert der Eigenschaft mit Ausnahme von als Zeichenfolge. Um ändern beliebiger Datenblöcke zu unterstützen, implementiert die EE eine benutzerdefinierte Schnittstelle für das gleiche Objekt, das implementiert die `IDebugProperty3` Schnittstelle. Diese benutzerdefinierte Schnittstelle würde, geben Sie dann die Methoden, die erforderlich sind, um ein beliebiger Speicherblock, der Daten zu ändern.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie Sie den ersten benutzerdefinierten Viewer aus einer Eigenschaft zu erhalten, wenn diese Eigenschaft jeder benutzerdefinierte Viewer verfügt.

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
[Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)  
[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)  
[SDK-Hilfsprogramme für das Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)  
[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
