---
title: iPropertyproxyeeside | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714859"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Diese Schnittstelle stellt Methoden zum Anzeigen von Daten für das zugeordnete Objekt bereit. Diese Schnittstelle ist Teil der Unterstützung für Typvisualisierer.

## <a name="syntax"></a>Syntax

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Ausdrucksauswertungsgeber implementiert diese Schnittstelle, um Typvisualisierungen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) auf, um diese Schnittstelle abzurufen. Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer [IDebugProperty3-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty3.md) auf, um die [IPropertyProxyProvider-Schnittstelle](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgenden Methoden werden von dieser Schnittstelle implementiert:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialisiert einen Datenquellenanbieter, sodass auf die Daten des Objekts zugegriffen werden kann.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Ruft Informationen zur Assembly des Objekts ab.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ruft die Anfangsdaten für das Objekt ab.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Erstellt eine Kopie eines vorhandenen Datenspeichers.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Erstellt einen Verweis auf einen vorhandenen Datenspeicher.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Ruft Informationen zu einer bestimmten Assembly im Kontext der Assembly ab, die dieses Objekt enthält.|

## <a name="remarks"></a>Bemerkungen
 Eine Typvisualisierung verwendet diese Schnittstelle, um auf die Werte zuzugreifen, die dem Objekt zugeordnet sind, zu dem diese Schnittstelle gehört. Der Zugriff auf die Daten erfolgt über die [IEEDataStorage-Schnittstelle,](../../../extensibility/debugger/reference/ieedatastorage.md) die eine schreibgeschützte Ansicht der Daten bietet.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
