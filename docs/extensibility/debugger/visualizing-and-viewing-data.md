---
title: Visualisieren und Anzeigen von Daten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 3f2317abd4bfaf6ebf8151812cf15541a1c94ecf
ms.lasthandoff: 04/05/2017

---
# <a name="visualizing-and-viewing-data"></a>Visualisieren und Anzeigen von Daten
Typ-Schnellansichten und benutzerdefinierten Viewer Darstellung der Daten in einer Weise, die schnell ein Entwickler von Bedeutung ist. Die ausdrucksauswertung (EE) kann Drittanbieter-Typ-Schnellansichten unterstützen als auch einen eigenen benutzerdefinierten Viewer angeben.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Bestimmt, wie viele Typ-Schnellansichten und benutzerdefinierten Viewer den Typ des Objekts zugeordnet, durch Aufrufen sind der [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) Methode. Wenn Sie mindestens einen Typ Schnellansicht oder in benutzerdefinierten Viewer verfügbar ist, ruft Visual Studio die [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methode zum Abrufen einer Liste von Schnellansichten und -Viewer (tatsächlich eine Liste der `CLSID`s, die den Schnellansichten und Viewern implementieren) und stellt sie dem Benutzer.  
  
## <a name="supporting-type-visualizers"></a>Typ-Schnellansichten unterstützen  
 Es gibt eine Anzahl von Schnittstellen, die die EE implementieren muss, um die Typ-Schnellansichten unterstützen. Diese Schnittstellen können in zwei große Kategorien unterteilt: die Liste der Typ-Schnellansichten auch solche, die Zugriff auf die Eigenschaftendaten.  
  
### <a name="listing-type-visualizers"></a>Typ-Schnellansichten auflisten  
 Die EE unterstützt die Typ-Schnellansichten in seiner Implementierung von auflisten `IDebugProperty3::GetCustomViewerCount` und `IDebugProperty3::GetCustomViewerList`. Diese Methoden übergeben, den Aufruf an die entsprechenden Methoden [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 Die [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) durch Aufruf von [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Diese Methode erfordert die [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) -Schnittstelle, die von der abgerufen wird die [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle übergeben, um [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`erfordert außerdem die [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) und [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) Schnittstellen, die an Sie übergeben wurden `IDebugParsedExpression::EvaluateSync`. Die endgültige Benutzeroberfläche zum Erstellen erforderlich die `IEEVisualizerService` Schnittstelle ist die [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) -Schnittstelle, die die EE implementiert. Diese Schnittstelle ermöglicht Änderungen an die Eigenschaft visualisierte vorgenommen werden müssen. Alle Eigenschaftendaten in gekapselt ist ein [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle, die auch von der EE implementiert wird.  
  
### <a name="accessing-property-data"></a>Datenzugriff-Eigenschaft  
 Zugreifen auf die Daten erfolgt über die [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Schnittstelle. Um diese Schnittstelle abzurufen, ruft Visual Studio [QueryInterface](/cpp/atl/queryinterface) auf das Eigenschaftenobjekt abgerufen der [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) Schnittstelle (auf das gleiche Objekt, das implementiert implementiert die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle) und ruft dann die [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) Methode zum Abrufen der `IPropertyProxyEESide` Schnittstelle.  
  
 Alle Daten zu übergeben, in und aus der `IPropertyProxyEESide` Schnittstelle gekapselt ist, der [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) Schnittstelle. Diese Schnittstelle stellt ein Array von Bytes dar und wird von Visual Studio und die EE implementiert. Wenn Daten für eine Eigenschaft geändert werden, erstellt Visual Studio eine `IEEDataStorage` Objekt, das den neuen Daten und ruft [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) mit dieses Datenobjekt, um ein neues erhalten `IEEDataStorage` -Objekt, das wiederum an [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) zum Aktualisieren von Daten für die Eigenschaft. `IPropertyProxyEESide::CreateReplacementObject`ermöglicht die EE eine eigene Klasse instanziieren, das implementiert die `IEEDataStorage` Schnittstelle.  
  
## <a name="supporting-custom-viewers"></a>Unterstützung von benutzerdefinierten Viewer  
 Das Flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` wird festgelegt, die `dwAttrib` Feld der [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur (zurückgegeben durch einen Aufruf von [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) um anzugeben, dass das Objekt mit einen benutzerdefinierten Viewer zugeordnet hat. Wenn dieses Flag festgelegt ist, ruft Visual Studio die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle aus dem [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle mit [QueryInterface](/cpp/atl/queryinterface).  
  
 Wenn der Benutzer einen benutzerdefinierten Viewer auswählt, wird Visual Studio instanziiert den benutzerdefinierten Viewer, die mit dem Viewer `CLSID` bereitgestellt werden, indem Sie die `IDebugProperty3::GetCustomViewerList` Methode. Visual Studio ruft dann [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) auf den Wert für dem Benutzer anzuzeigen.  
  
 In der Regel `IDebugCustomViewer::DisplayValue` stellt eine schreibgeschützte Ansicht der Daten. Um Änderungen an den Daten zu ermöglichen, muss die EE eine benutzerdefinierte Schnittstelle implementieren, die Daten auf ein Eigenschaftenobjekt unterstützt. Die `IDebugCustomViewer::DisplayValue` Methode mithilfe dieser benutzerdefinierten Schnittstelle unterstützen, die Daten ändern. Die Methode für die benutzerdefinierte Schnittstelle sieht, auf die `IDebugProperty2` Schnittstelle als übergeben der `pDebugProperty` Argument.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Schnellansichten und benutzerdefinierten Viewer geben unterstützen  
 Typ-Schnellansichten und benutzerdefinierten Viewern in eine EE unterstützen die [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methoden. Zuerst fügt die EE die Anzahl der benutzerdefinierten Viewer, die es bereitstellt, den Rückgabewert von der [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Methode. Zweitens die EE fügt die `CLSID`s von eigenen benutzerdefinierten Viewer auf die zurückgegebene Liste der [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugging-Aufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
