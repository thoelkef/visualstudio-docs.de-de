---
title: IPropertyProxyEESide | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd9b804556cd748c921a0c21729daee56e9499b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708458"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Diese Schnittstelle bietet Methoden zum Anzeigen von Daten für das zugeordnete Objekt. Diese Schnittstelle ist Teil der Unterstützung für Typ-Schnellansichten.

## <a name="syntax"></a>Syntax

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine ausdrucksauswertung implementiert diese Schnittstelle, um die Typ-Schnellansichten unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) dieser Schnittstelle abgerufen. Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle zum Abrufen der [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgenden Methoden werden von dieser Schnittstelle implementiert:

|Methode|Beschreibung|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialisiert ein Datenquellenanbieter, sodass die Daten des Objekts zugegriffen werden können.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Ruft Informationen zu der Assembly des Objekts ab.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ruft den ursprünglichen Daten für das Objekt ab.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Erstellt eine Kopie einer vorhandenen Data Storage.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Erstellt einen Verweis auf eine vorhandene Datenspeicher.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Ruft Informationen zu einer bestimmten Assembly im Kontext der Assembly mit der dieses Objekt ab.|

## <a name="remarks"></a>Hinweise
 Eine typschnellansicht verwendet diese Schnittstelle zum Zugriff auf die Werte von das Objekt, dem diese Schnittstelle Teil ist. Die Daten erfolgt über die [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Schnittstelle, die eine schreibgeschützte Ansicht der Daten bereitstellt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)