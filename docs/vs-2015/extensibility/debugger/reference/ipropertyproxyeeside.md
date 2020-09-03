---
title: Ipropertyproxyeeside | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 660c792d9e13fabbd433aee46c57474fb824453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684672"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt Methoden zum Anzeigen von Daten für das zugeordnete-Objekt bereit. Diese Schnittstelle ist Teil der Unterstützung für typvisualisierungen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von einer Ausdrucks Auswertung implementiert, um typvisualisierungen zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [getpropertyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) auf, um diese Schnittstelle zu erhalten. Rufen Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle auf, um die [ipropertyproxyprovider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) -Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Die folgenden Methoden werden von dieser Schnittstelle implementiert:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialisiert einen Datenquellen Anbieter, damit auf die Daten des Objekts zugegriffen werden kann.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Ruft Informationen zur Assembly des Objekts ab.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ruft die Anfangsdaten für das-Objekt ab.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Erstellt eine Kopie eines vorhandenen Datenspeichers.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Erstellt einen Verweis auf eine vorhandene Datenspeicherung.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Ruft Informationen zu einer bestimmten Assembly im Kontext der Assembly ab, die dieses-Objekt enthält.|  
  
## <a name="remarks"></a>Bemerkungen  
 Eine typschnell Ansicht verwendet diese Schnittstelle für den Zugriff auf die Werte, die dem Objekt zugeordnet sind, zu dem diese Schnittstelle gehört. Der Zugriff auf die Daten erfolgt über die [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Schnittstelle, die eine schreibgeschützte Ansicht der Daten bereitstellt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Typschnell Ansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
