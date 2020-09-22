---
title: Ieevisualizerserviceprovider | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9ba7c7216c590f773f1054a1f06cd3412ff6b20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840964"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle ermöglicht den Zugriff auf eine Methode, mit der ein schnell Ansichts Dienst erstellt werden kann, der zum Verarbeiten von Aufgaben für die typschnell Ansicht der IDE verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Visual Studio implementiert, um ein Dienst Objekt für die Schnellansicht zu erstellen, das wiederum zum Bereitstellen von Klassen-IDs `CLSID` vom Typ "schnell Ansichten" an die Visual Studio-IDE verwendet wird.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die Ausdrucks Auswertung (EE) ruft [geteeservice](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) auf, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Erstellt den schnell Ansichts Dienst.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die- `IEEVisualizerServiceProvider` Schnittstelle wird während der Implementierung von [evaluatesync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)abgerufen. Der schnell Ansichts Dienst, der von dieser Schnittstelle erstellt wird, wird verwendet, um Funktionen für eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle bereitzustellen, die für die Implementierung verantwortlich ist. Der EE ist auch dafür verantwortlich, eine [ieevisualizerdataprovider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) -Schnittstelle zu implementieren, die es typvisualisierungen ermöglicht, den Wert einer Eigenschaft anzuzeigen und zu ändern.  
  
 Ausführliche Informationen dazu, wie diese Schnittstellen interagieren, finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucks Bewertungs Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Evaluatesync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Ieevisualizerdataprovider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [Geteeservice](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
