---
title: Visualisieren und Anzeigen von Daten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 40f06ee57c5c889c2004dbd5b85e269bfd0841ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959583"
---
# <a name="visualizing-and-viewing-data"></a>Visualisieren und Anzeigen von Daten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typschnellansichten und benutzerdefinierten Viewern Darstellung der Daten in einer Weise, die schnell für Entwickler relevant ist. Die ausdrucksauswertung (EE) kann Drittanbieter-Typ-Schnellansichten unterstützen als auch einen eigenen benutzerdefinierten Viewer angeben.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Bestimmt, wie viele typschnellansichten und benutzerdefinierten Viewern den Typ des Objekts zugeordnet, durch den Aufruf sind der [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) Methode. Wenn Sie mindestens einen typschnellansicht oder in benutzerdefinierten Viewer verfügbar ist, ruft Visual Studio die [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methode zum Abrufen einer Liste dieser Schnellansichten und-Viewer (tatsächlich eine Liste der `CLSID`s, die implementiert die Schnellansichten und Viewer) und präsentiert diese dem Benutzer.  
  
## <a name="supporting-type-visualizers"></a>Typ-Schnellansichten unterstützen  
 Es gibt eine Reihe von Schnittstellen, die die EE implementieren müssen, um Typ-Schnellansichten unterstützen. Diese Schnittstellen können in zwei große Kategorien untergliedert werden: die Liste der Typ-Schnellansichten und solche, die Zugriff auf die Eigenschaftendaten.  
  
### <a name="listing-type-visualizers"></a>Typ-Schnellansichten auflisten  
 Die EE unterstützt Auflisten der Typ-Schnellansichten in seiner Implementierung von `IDebugProperty3::GetCustomViewerCount` und `IDebugProperty3::GetCustomViewerList`. Diese Methoden übergeben, den Aufruf an die entsprechenden Methoden [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 Die [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) durch Aufruf von [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Diese Methode erfordert die [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) -Schnittstelle, die aus abgerufen werden die [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle zu übergeben, um [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` erfordert außerdem die [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) und [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) Schnittstellen, die übergeben wurden `IDebugParsedExpression::EvaluateSync`. Die endgültige Benutzeroberfläche, die zum Erstellen der `IEEVisualizerService` Schnittstelle ist die [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) -Schnittstelle, die die EE implementiert. Diese Schnittstelle ermöglicht Änderungen an die Eigenschaft, die Schnellansicht angezeigt wird. Alle Daten in gekapselt ein [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle, die auch von der EE implementiert wird.  
  
### <a name="accessing-property-data"></a>Zugreifen auf Daten  
 Zugreifen auf die Daten erfolgt über die [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Schnittstelle. Um diese Schnittstelle abzurufen, ruft Visual Studio [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf der, der abzurufende Eigenschaftenobjekt die [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) Schnittstelle (auf das gleiche Objekt, das implementiert implementiert die [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle) und ruft dann die [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) Methode zum Abrufen der `IPropertyProxyEESide` Schnittstelle.  
  
 Alle Daten zu übergeben, in und aus der `IPropertyProxyEESide` Schnittstelle gekapselt ist, der [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) Schnittstelle. Diese Schnittstelle stellt ein Array von Bytes und wird von Visual Studio und die EE implementiert. Wenn Daten für eine Eigenschaft geändert werden, erstellt Visual Studio ein `IEEDataStorage` Objekt, das die neuen Daten und ruft [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) mit diesem Datenobjekt, um ein neues erhalten `IEEDataStorage` Objekt, das wiederum die an [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) zum Aktualisieren von Daten von der Eigenschaft. `IPropertyProxyEESide::CreateReplacementObject` ermöglicht die EE, eine eigene Klasse zu instanziieren, die implementiert die `IEEDataStorage` Schnittstelle.  
  
## <a name="supporting-custom-viewers"></a>Unterstützung von benutzerdefinierten Viewern  
 Das Flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` festgelegt ist, der `dwAttrib` Feld der [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur (zurückgegeben durch einen Aufruf von [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) um anzugeben, dass das Objekt einen benutzerdefinierten Viewer verknüpft ist mit ihm. Wenn dieses Flag festgelegt ist, ruft Visual Studio die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle aus der [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle. dabei wird [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
 Wenn der Benutzer einen benutzerdefinierten Viewer auswählt, wird Visual Studio instanziiert den benutzerdefinierten Viewer, die mithilfe des anzeigenden Benutzers `CLSID` vom die `IDebugProperty3::GetCustomViewerList` Methode. Visual Studio ruft dann [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) auf den Wert für dem Benutzer anzuzeigen.  
  
 In der Regel `IDebugCustomViewer::DisplayValue` stellt eine schreibgeschützte Ansicht der Daten. Um Änderungen an den Daten zu ermöglichen, muss die EE eine benutzerdefinierte Schnittstelle implementieren, die sich verändernden Daten auf ein Objekt unterstützt werden. Die `IDebugCustomViewer::DisplayValue` Methode, die diese benutzerdefinierte Schnittstelle verwendet, um das Ändern von Daten unterstützt. Die Methode sucht die benutzerdefinierte Schnittstelle, auf die `IDebugProperty2` Schnittstelle als übergeben, die `pDebugProperty` Argument.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Unterstützen von Schnellansichten und benutzerdefinierten Viewern eingeben  
 Ein EE unterstützen sowohl typschnellansichten und benutzerdefinierten Viewern in die [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methoden. Zuerst fügt die EE die Anzahl der benutzerdefinierten Viewer, die er bereitstellt, die den Rückgabewert von der [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Methode. Zweitens: die EE fügt die `CLSID`s der Liste zurückgegeben werden, indem Sie einen eigenen benutzerdefinierten Viewer die [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
