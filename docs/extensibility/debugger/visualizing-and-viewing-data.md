---
title: Visualisieren und Anzeigen von Daten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebaa07c8fe70e1842334b0bf7c28eb7491fd9c44
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="visualizing-and-viewing-data"></a>Visualisieren und Anzeigen von Daten
Typ-Schnellansichten und benutzerdefinierten Viewer Darstellung der Daten in einer Weise, die schnell ein Entwickler von Bedeutung ist. Die ausdrucksauswertung (EE) kann Drittanbieter-Typ-Schnellansichten unterstützen als auch einen eigenen benutzerdefinierten Viewer angeben.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bestimmt, wie viele Typ-Schnellansichten und benutzerdefinierten Viewer den Typ des Objekts zugeordnet, durch Aufrufen sind der [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) Methode. Wenn Sie mindestens einen Typ Schnellansicht oder in benutzerdefinierten Viewer verfügbar ist, ruft Visual Studio die [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methode zum Abrufen einer Liste von Schnellansichten und -Viewer (tatsächlich eine Liste der `CLSID`s, die implementieren die Schnellansichten und -Viewer) und stellt sie dem Benutzer.  
  
## <a name="supporting-type-visualizers"></a>Typ-Schnellansichten unterstützen  
 Es gibt eine Anzahl von Schnittstellen, die die EE implementieren muss, um die Typ-Schnellansichten unterstützen. Diese Schnittstellen können in zwei große Kategorien unterteilt: die Liste der Typ-Schnellansichten auch solche, die Zugriff auf die Eigenschaftendaten.  
  
### <a name="listing-type-visualizers"></a>Typ-Schnellansichten auflisten  
 Die EE unterstützt die Typ-Schnellansichten in seiner Implementierung von auflisten `IDebugProperty3::GetCustomViewerCount` und `IDebugProperty3::GetCustomViewerList`. Diese Methoden übergeben, den Aufruf an die entsprechenden Methoden [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 Die [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) durch Aufruf von [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Diese Methode erfordert die [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) -Schnittstelle, die von der abgerufen wird die [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle übergeben, um [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` erfordert außerdem die [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) und [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) Schnittstellen, die an Sie übergeben wurden `IDebugParsedExpression::EvaluateSync`. Die endgültige Benutzeroberfläche zum Erstellen erforderlich die `IEEVisualizerService` Schnittstelle ist die [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) -Schnittstelle, die die EE implementiert. Diese Schnittstelle ermöglicht Änderungen an die Eigenschaft visualisierte vorgenommen werden müssen. Alle Eigenschaftendaten in gekapselt ist ein [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle, die auch von der EE implementiert wird.  
  
### <a name="accessing-property-data"></a>Datenzugriff-Eigenschaft  
 Zugreifen auf die Daten erfolgt über die [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Schnittstelle. Um diese Schnittstelle abzurufen, ruft Visual Studio [QueryInterface](/cpp/atl/queryinterface) auf das Eigenschaftenobjekt abgerufen der [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) Schnittstelle (auf das gleiche Objekt, das implementiert implementiert die [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) Interface) und ruft dann die [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) Methode zum Abrufen der `IPropertyProxyEESide` Schnittstelle.  
  
 Alle Daten zu übergeben, in und aus der `IPropertyProxyEESide` Schnittstelle gekapselt ist, der [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) Schnittstelle. Diese Schnittstelle stellt ein Array von Bytes dar und wird von Visual Studio und die EE implementiert. Wenn eine Eigenschaft Daten geändert werden, erstellt Visual Studio eine `IEEDataStorage` Objekt, das den neuen Daten und ruft [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) mit dieses Datenobjekt, um ein neues erhalten `IEEDataStorage` -Objekt, das wiederum ist übergeben an [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) zum Aktualisieren von Daten für die Eigenschaft. `IPropertyProxyEESide::CreateReplacementObject` ermöglicht die EE eine eigene Klasse instanziieren, das implementiert die `IEEDataStorage` Schnittstelle.  
  
## <a name="supporting-custom-viewers"></a>Unterstützung von benutzerdefinierten Viewer  
 Das Flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` wird festgelegt, der `dwAttrib` -Feld der der [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur (zurückgegeben durch einen Aufruf von [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)), um anzugeben, dass das Objekt einen benutzerdefinierten Viewer verknüpft sind mit ihm. Wenn dieses Flag festgelegt ist, ruft Visual Studio die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle aus dem [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle mit [QueryInterface](/cpp/atl/queryinterface).  
  
 Wenn der Benutzer einen benutzerdefinierten Viewer auswählt, wird Visual Studio instanziiert den benutzerdefinierten Viewer, die mit dem Viewer `CLSID` bereitgestellt werden, indem Sie die `IDebugProperty3::GetCustomViewerList` Methode. Visual Studio ruft dann [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) auf den Wert für dem Benutzer anzuzeigen.  
  
 In der Regel `IDebugCustomViewer::DisplayValue` stellt eine schreibgeschützte Ansicht der Daten. Um Änderungen an den Daten zu ermöglichen, muss die EE eine benutzerdefinierte Schnittstelle implementieren, die Daten auf ein Eigenschaftenobjekt unterstützt. Die `IDebugCustomViewer::DisplayValue` Methode mithilfe dieser benutzerdefinierten Schnittstelle unterstützen, die Daten ändern. Die Methode für die benutzerdefinierte Schnittstelle sieht, auf die `IDebugProperty2` Schnittstelle als übergeben der `pDebugProperty` Argument.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Schnellansichten und benutzerdefinierten Viewer geben unterstützen  
 Typ-Schnellansichten und benutzerdefinierten Viewern in eine EE unterstützen die [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methoden. Zuerst fügt die EE die Anzahl der benutzerdefinierten Viewer, die es bereitstellt, den Rückgabewert von der [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Methode. Zweitens die EE fügt die `CLSID`s von eigenen benutzerdefinierten Viewer auf die zurückgegebene Liste der [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugging-Aufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)