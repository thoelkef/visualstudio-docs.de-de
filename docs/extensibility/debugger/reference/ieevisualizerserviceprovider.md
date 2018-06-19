---
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564251aa26bf21157e4f3792095190ede23703c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122417"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle ermöglicht Zugriff auf eine Methode, die einen schnellansichtsdienst erstellen kann; dies zum Behandeln der Schnellansicht Aufgaben für die IDE verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um ein Dienstobjekt Schnellansicht erstellen wiederum dient zum Angeben der Klassen-IDs (`CLSID`s) des Typ-Schnellansichten Visual Studio-IDE.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ruft die ausdrucksauswertung (EE) [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) beim Abrufen dieser Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Erstellt die schnellansichtsdienst|  
  
## <a name="remarks"></a>Hinweise  
 Die `IEEVisualizerServiceProvider` während der Implementierung der Schnittstelle ermittelt [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Der schnellansichtsdienst, erstellt diese Schnittstelle, wird verwendet, zum Bereitstellen von Funktionen zu einer [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle, die die EE für die Implementierung verantwortlich ist. Die EE ist auch für die Durchführung einer [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Schnittstelle, die Typ-Schnellansichten anzeigen und Ändern eines Eigenschaftswerts ermöglicht.  
  
 Finden Sie unter [Visualizing und Anzeige von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) ausführliche Informationen über diese Schnittstellen wie interagieren.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)