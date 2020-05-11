---
title: Visualisieren und Anzeigen von Daten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712374"
---
# <a name="visualizing-and-viewing-data"></a>Visualisieren und Anzeigen von Daten
Typvisualisierer und benutzerdefinierte Viewer stellen Daten auf eine Weise dar, die für einen Entwickler schnell von Bedeutung ist. Der Ausdrucksevaluator (EE) kann Visualizer von Drittanbietern unterstützen und eigene benutzerdefinierte Viewer bereitstellen.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bestimmt, wie viele Typvisualisierer und benutzerdefinierte Viewer dem Objekttyp zugeordnet sind, indem die [GetCustomViewerCount-Methode](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) aufgerufen wird. Wenn mindestens eine Typvisualisierung oder ein benutzerdefinierter Viewer verfügbar ist, ruft Visual Studio die [GetCustomViewerList-Methode](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) auf, um eine Liste dieser Visualizer und Viewer (tatsächlich eine Liste von s, die die Visualizer und Viewer implementiert) abzurufen und dem Benutzer zu präsentieren.

## <a name="supporting-type-visualizers"></a>Unterstützung von Typvisualisierern
 Es gibt eine Reihe von Schnittstellen, die der EE implementieren muss, um Typvisualisierer zu unterstützen. Diese Schnittstellen können in zwei große Kategorien unterteilt werden: Schnittstellen, die die Typvisualisierer und Schnittstellen auflisten, die auf die Eigenschaftendaten zugreifen.

### <a name="listing-type-visualizers"></a>Auflistung von Typ-Visualisierungen
 Der EE unterstützt die Auflistung der Typvisualisierer in seiner Implementierung von `IDebugProperty3::GetCustomViewerCount` und `IDebugProperty3::GetCustomViewerList`. Diese Methoden übergeben den Aufruf an die entsprechenden Methoden [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 Der [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) wird durch Aufrufen von [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)abgerufen. Diese Methode erfordert die [IDebugBinder3-Schnittstelle,](../../extensibility/debugger/reference/idebugbinder3.md) die von der [IDebugBinder-Schnittstelle](../../extensibility/debugger/reference/idebugbinder.md) abgerufen wird, die an [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)übergeben wird. `IEEVisualizerServiceProvider::CreateVisualizerService`erfordert auch die [Schnittstellen IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) und [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) die an `IDebugParsedExpression::EvaluateSync`übergeben wurden. Die letzte Schnittstelle, `IEEVisualizerService` die zum Erstellen der Schnittstelle erforderlich ist, ist die [IEEVisualizerDataProvider-Schnittstelle,](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) die von der EE implementiert wird. Mit dieser Schnittstelle können Änderungen an der zu visualisierenden Eigenschaft vorgenommen werden. Alle Eigenschaftsdaten werden in einer [IDebugObject-Schnittstelle](../../extensibility/debugger/reference/idebugobject.md) gekapselt, die ebenfalls vom EE implementiert wird.

### <a name="accessing-property-data"></a>Zugriff auf Eigenschaftsdaten
 Der Zugriff auf Eigenschaftsdaten erfolgt über die [IPropertyProxyEESide-Schnittstelle.](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Um diese Schnittstelle zu erhalten, ruft Visual Studio [QueryInterface](/cpp/atl/queryinterface) für das Eigenschaftsobjekt auf, um die [IPropertyProxyProvider-Schnittstelle](../../extensibility/debugger/reference/ipropertyproxyprovider.md) abruft (die für `IPropertyProxyEESide` dasselbe Objekt implementiert wird, das die [IDebugProperty3-Schnittstelle](../../extensibility/debugger/reference/idebugproperty3.md) implementiert), und ruft dann die [GetPropertyProxy-Methode](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) auf, um die Schnittstelle abzufragen.

 Alle Daten, die an `IPropertyProxyEESide` und aus der Schnittstelle übergeben werden, werden in der [IEEDataStorage-Schnittstelle](../../extensibility/debugger/reference/ieedatastorage.md) gekapselt. Diese Schnittstelle stellt ein Array von Bytes dar und wird sowohl von Visual Studio als auch von der EE implementiert. Wenn die Daten einer Eigenschaft geändert werden sollen, erstellt Visual Studio `IEEDataStorage` ein Objekt, das die neuen Daten enthält, und ruft [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) mit diesem Datenobjekt auf, um ein neues `IEEDataStorage` Objekt zu erhalten, das wiederum an [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) übergeben wird, um die Daten der Eigenschaft zu aktualisieren. `IPropertyProxyEESide::CreateReplacementObject`ermöglicht es dem EE, seine eigene Klasse `IEEDataStorage` zu instanziieren, die die Schnittstelle implementiert.

## <a name="supporting-custom-viewers"></a>Unterstützung von benutzerdefinierten Viewern
 Das `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` Flag wird `dwAttrib` im Feld der [DEBUG_PROPERTY_INFO-Struktur](../../extensibility/debugger/reference/debug-property-info.md) (die durch einen Aufruf von [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)zurückgegeben wird ) gesetzt, um anzuzeigen, dass dem Objekt ein benutzerdefinierter Viewer zugeordnet ist. Wenn dieses Flag festgelegt ist, ruft Visual Studio die [IDebugProperty3-Schnittstelle](../../extensibility/debugger/reference/idebugproperty3.md) mithilfe von [QueryInterface](/cpp/atl/queryinterface)von der [IDebugProperty2-Schnittstelle](../../extensibility/debugger/reference/idebugproperty2.md) ab.

 Wenn der Benutzer einen benutzerdefinierten Viewer auswählt, instanziiert Visual `CLSID` Studio den `IDebugProperty3::GetCustomViewerList` benutzerdefinierten Viewer mithilfe der von der Methode bereitgestellten Viewer. Visual Studio ruft dann [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) auf, um den Wert für den Benutzer anzuzeigen.

 In `IDebugCustomViewer::DisplayValue` der Regel wird eine schreibgeschützte Ansicht der Daten angezeigt. Um Änderungen an den Daten zuzulassen, muss der EE eine benutzerdefinierte Schnittstelle implementieren, die das Ändern von Daten für ein Eigenschaftsobjekt unterstützt. Die `IDebugCustomViewer::DisplayValue` Methode verwendet diese benutzerdefinierte Schnittstelle, um das Ändern der Daten zu unterstützen. Die Methode sucht nach der `IDebugProperty2` benutzerdefinierten Schnittstelle `pDebugProperty` auf der Schnittstelle, die als Argument übergeben wird.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Unterstützung sowohl von Typvisualisierern als auch von benutzerdefinierten Viewern
 Ein EE kann sowohl Typvisualisierer als auch benutzerdefinierte Viewer in den [GetCustomViewerCount-](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList-Methoden](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) unterstützen. Zunächst fügt der EE die Anzahl der benutzerdefinierten Viewer hinzu, die er dem von der [GetCustomViewerCount-Methode](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) zurückgegebenen Wert liefert. Zweitens fügt der EE `CLSID`die s seiner eigenen benutzerdefinierten Viewer an die Liste an, die von der [GetCustomViewerList-Methode](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) zurückgegeben wird.

## <a name="see-also"></a>Weitere Informationen
- [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md)
- [Typvisualisierung und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
