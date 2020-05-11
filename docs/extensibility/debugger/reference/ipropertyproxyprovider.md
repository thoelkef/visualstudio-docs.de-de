---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71d993c7f99cade5b866e67298132a325986e3a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714795"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Diese Schnittstelle stellt eine Proxyschnittstelle zum Anzeigen und Ändern der Daten eines Objekts bereit.

## <a name="syntax"></a>Syntax

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Ausdrucksevaluator (EE) implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugProperty3-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty3.md) als Teil der EE-Unterstützung von Typvisualisierern implementiert.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer `IDebugProperty3` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die `IPropertyProxyProvider` Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Ruft eine Eigenschaftsproxyschnittstelle ab, um Daten für ein Objekt anzuzeigen.|

## <a name="remarks"></a>Bemerkungen
 Obwohl der EE diese Schnittstelle implementiert, wird die Implementierung von [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) in der Regel von [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)behandelt. Weitere Informationen zum Abrufen der IEEVisualizerService-Schnittstelle finden Sie unter [Visualisieren und Anzeigen von Daten.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
