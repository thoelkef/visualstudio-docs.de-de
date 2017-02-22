---
title: "Visualisieren und Anzeigen von Daten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK], Anzeigen von Daten"
  - "Debuggen [Debugging-SDK], die Visualisierung von Daten"
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Visualisieren und Anzeigen von Daten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Geben Sie vorhandene Daten der Schnellansichten und der benutzerdefinierten Viewer auf eine Weise ein, die dem Entwickler schnell sinnvoll ist.  Die Ausdrucksauswertung \(EE\) kann schnellansichten Typ von Drittanbietern unterstützen, sowie seine eigenen benutzerdefinierten Viewer angeben.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bestimmt, wie viele Typ schnellansichten und benutzerdefinierten Viewer mit dem Typ zugeordnet werden, indem die [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)\-Methode aufruft.  Wenn mindestens eine schnellansicht Typ oder verfügbaren benutzerdefinierten Viewer wird, ruft Visual Studio die [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)\-Methode auf, um eine Liste der Schnellansichten and Viewer abzurufen \(tatsächlich eine Liste von `CLSID`s, das die Schnellansichten sowie die Viewer implementieren\) und stellt sie dem Benutzer dar.  
  
## Typ\-Schnellansichten unterstützen  
 Es gibt mehrere Schnittstellen, die die EE Typ implementieren muss, um schnellansichten zu unterstützen.  Diese Schnittstellen können in zwei große Kategorien aufgegliedert werden: Typ der die schnellansichten auflisten und die, die die Eigenschaftendaten zugreifen.  
  
### Typ\-Schnellansichten auflisten  
 Die EE unterstützt das Auflisten der Typ schnellansichten in seiner Implementierung von `IDebugProperty3::GetCustomViewerCount` und `IDebugProperty3::GetCustomViewerList`.  Diese Methoden führen den Aufruf der entsprechenden Methoden [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) wird abgerufen, indem [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)aufruft.  Diese Methode muss die [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)\-Schnittstelle, die von der [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)\-Schnittstelle abgerufen wird, die [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)übergeben wird.  `IEEVisualizerServiceProvider::CreateVisualizerService` erfordert außerdem die [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) und Schnittstellen, die `IDebugParsedExpression::EvaluateSync`übergeben wurden.  Die endgültige Schnittstelle, die `IEEVisualizerService`\-Schnittstelle zu erstellen, die erforderlich ist, ist die [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)\-Schnittstelle, die die EE implementiert.  Diese Schnittstelle ermöglicht die Eigenschaft festgelegt werden soll, Änderungen, visualisiert wird.  Alle Eigenschaftendaten wird in einer Schnittstelle [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) gekapselt, die auch von der EE implementiert wird.  
  
### Zugreifen auf Eigenschaft\-Bezugspunkte  
 Eigenschaftendaten zuzugreifen kann über die [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)\-Schnittstelle.  Zum Abrufen dieser Schnittstelle ruft Visual Studio\-Aufrufe [QueryInterface](/visual-cpp/atl/queryinterface) für das Eigenschaftenobjekt in der [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)\-Schnittstelle abzurufen \(implementiert im gleichen Objekt, das die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)\-Schnittstelle implementiert\) und dann die [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) zum Abrufen der Methode auf `IPropertyProxyEESide`\-Schnittstelle.  
  
 Alle Daten, die in die und aus `IPropertyProxyEESide`\-Schnittstelle Bereichs übergeben werden, wird in der [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)\-Schnittstelle gekapselt.  Diese Schnittstelle stellt ein Bytearray dar und wird vom Visual Studio und der EE implementiert.  Wenn die Daten einer Eigenschaft geändert werden soll, erstellt Visual Studio ein `IEEDataStorage`\-Objekt, das die neuen Daten enthält, und ruft [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) diesem Datenobjekt, um ein neues `IEEDataStorage`\-Objekt an, das wiederum auf [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) übergeben wird, um die Daten der Eigenschaft zu aktualisieren.  `IPropertyProxyEESide::CreateReplacementObject` kann die EE, um eine eigene Klasse zu instanziieren, die die `IEEDataStorage`\-Schnittstelle implementiert.  
  
## Unterstützung von benutzerdefinierten Viewer  
 Das Flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` wird auf dem `dwAttrib` Feld der [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur zurückgegeben wird \(durch einen Aufruf von [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\) festgelegt, um anzugeben, dass das Objekt einen benutzerdefinierten Viewer verfügt, der mit ihm zugeordnet ist.  Wenn dieses Flag festgelegt ist, ruft Visual Studio die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)\-Schnittstelle aus der [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle mit [QueryInterface](/visual-cpp/atl/queryinterface).  
  
 Wenn der Benutzer einen benutzerdefinierten Viewer wählt, instanziiert Visual Studio den benutzerdefinierten Viewer mit `CLSID` des Viewers, das von der `IDebugProperty3::GetCustomViewerList`\-Methode angegeben ist.  Visual Studio ruft dann [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) an, um den Wert für den Benutzer anzuzeigen.  
  
 Normalerweise stellt `IDebugCustomViewer::DisplayValue` eine schreibgeschützte Ansicht der Daten dar.  Um Änderungen an den Daten zu ermöglichen, muss die EE eine benutzerdefinierte Schnittstelle implementieren die das Ändern von Daten für ein Eigenschaftenobjekt unterstützt.  Die `IDebugCustomViewer::DisplayValue`\-Methode verwendet diese benutzerdefinierte Schnittstelle, um die Änderung der Daten zu unterstützen.  Die Methode sucht nach der benutzerdefinierten Schnittstelle für die `IDebugProperty2`\-Schnittstelle `pDebugProperty` das als ein Argument übergeben wird.  
  
## Typ\-Schnellansichten und benutzerdefinierten Viewer unterstützen  
 Eine EE Typ kann schnellansichten und benutzerdefinierten Viewer in [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)\-Methoden unterstützen.  Zuerst fügt die EE die Anzahl von benutzerdefinierten Viewern hinzu, die den Wert angibt, der von der [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)\-Methode zurückgegeben wird.  Anschließend fügt die EE das `CLSID`s seiner eigenen benutzerdefinierten Viewer zur Liste an, die von der [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)\-Methode zurückgegeben wird.  
  
## Siehe auch  
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)