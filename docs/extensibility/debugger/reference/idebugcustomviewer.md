---
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732414"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Diese Schnittstelle ermöglicht es einem Ausdrucksevaluator (EE), den Wert einer Eigenschaft in jedem erforderlichen Format anzuzeigen.

## <a name="syntax"></a>Syntax

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein EE implementiert diese Schnittstelle, um den Wert einer Eigenschaft in einem benutzerdefinierten Format anzuzeigen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
Ein Aufruf der `CoCreateInstance` COM-Funktion instanziiert diese Schnittstelle. Die `CLSID` übergebene datei `CoCreateInstance` wird aus der Registrierung abgerufen. Ein Aufruf von [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) ruft den Speicherort in der Registrierung ab. Weitere Informationen finden Sie unter Hinweise sowie im Beispiel.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Tut alles, was erforderlich ist, um einen bestimmten Wert anzuzeigen.|

## <a name="remarks"></a>Bemerkungen
Diese Schnittstelle wird verwendet, wenn der Wert einer Eigenschaft nicht auf normale Weise angezeigt werden kann, z. B. mit einer Datentabelle oder einem anderen komplexen Eigenschaftstyp. Ein benutzerdefinierter Viewer, `IDebugCustomViewer` wie er von der Schnittstelle dargestellt wird, unterscheidet sich von einer Typvisualisierung, bei der es sich um ein externes Programm zum Anzeigen von Daten eines bestimmten Typs unabhängig vom EE handelt. Der EE implementiert einen benutzerdefinierten Viewer, der für diesen EE spezifisch ist. Ein Benutzer wählt aus, welcher Visualisierungstyp verwendet werden soll, sei es eine Typvisualisierung oder ein benutzerdefinierter Viewer. Weitere Informationen zu diesem Prozess finden Sie unter [Visualisieren und Anzeigen von Daten.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

Ein benutzerdefinierter Viewer wird auf die gleiche Weise wie ein EE registriert und erfordert daher eine Sprach-GUID und eine Hersteller-GUID. Die genaue Metrik (oder der Name des Registrierungseintrags) ist nur dem EE bekannt. Diese Metrik wird in der [DEBUG_CUSTOM_VIEWER-Struktur](../../../extensibility/debugger/reference/debug-custom-viewer.md) zurückgegeben, die wiederum durch einen Aufruf von [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)zurückgegeben wird. Der in der Metrik `CLSID` gespeicherte Wert ist `CoCreateInstance` der, der an die Com-Funktion übergeben wird (siehe Beispiel).

Die [SDK-Hilfsfunktion "Debugging"](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric`kann zum Registrieren eines benutzerdefinierten Viewers verwendet werden. Die Registrierungsschlüssel, die ein benutzerdefinierter Viewer benötigt, finden Sie im Registrierungsabschnitt `Debugging SDK Helpers` "Expression Evaluators" von. Beachten Sie, dass ein benutzerdefinierter Viewer nur eine Metrik benötigt (die vom EE-Implementierer definiert wird), während ein Ausdrucksauswertungswert mehrere vordefinierte Metriken erfordert.

Normalerweise bietet ein benutzerdefinierter Viewer eine schreibgeschützte Ansicht der Daten, da die [IDebugProperty3-Schnittstelle,](../../../extensibility/debugger/reference/idebugproperty3.md) die [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) bereitstellt, keine Methoden zum Ändern des Eigenschaftswerts außer als Zeichenfolge enthält. Um das Ändern beliebiger Datenblöcke zu unterstützen, implementiert der EE eine `IDebugProperty3` benutzerdefinierte Schnittstelle für dasselbe Objekt, das die Schnittstelle implementiert. Diese benutzerdefinierte Schnittstelle würde dann die Methoden bereitstellen, die zum Ändern eines beliebigen Datenblocks erforderlich sind.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt, wie Sie den ersten benutzerdefinierten Viewer aus einer Eigenschaft abrufen, wenn diese Eigenschaft über benutzerdefinierte Viewer verfügt.

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

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
