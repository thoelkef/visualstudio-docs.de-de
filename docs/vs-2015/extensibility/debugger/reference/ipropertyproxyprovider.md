---
title: Ipropertyproxyprovider | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39cdc7769765a7680905fca5faa49222bf0a3b6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700046"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Proxy Schnittstelle bereit, um die Daten eines Objekts anzuzeigen und zu ändern.  
  
## <a name="syntax"></a>Syntax  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Ausdrucks Auswertung (EE) implementiert diese Schnittstelle für das gleiche Objekt, das die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle als Teil der EE-Unterstützung von typvisualisierungen implementiert.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für eine `IDebugProperty3` Schnittstelle auf, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Die- `IPropertyProxyProvider` Schnittstelle implementiert die folgende Methode:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Ruft eine eigenschaftenproxyschnittstelle zum Anzeigen von Daten in einem-Objekt ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Obwohl der EE diese Schnittstelle implementiert, wird die Implementierung von [getpropertyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) in der Regel von [getpropertyproxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)verarbeitet. Ausführliche Informationen zum Abrufen der ieevisualizerservice-Schnittstelle finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Getpropertyproxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Typschnell Ansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
