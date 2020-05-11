---
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718189"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Diese Schnittstelle stellt ein Array von Bytes dar.

## <a name="syntax"></a>Syntax

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Ausdrucksevaluator (EE) implementiert diese Schnittstelle, um ein Array von Bytes darzustellen (von Typvisualisierern verwendet, um Daten über die [IPropertyProxyEESide-Schnittstelle](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) abzurufen und zu ändern). Der EE implementiert diese Schnittstelle in der Regel, um externe Typvisualisierer zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die Methoden `IPropertyProxyEESide` auf der Schnittstelle geben diese Schnittstelle alle zurück. Rufen Sie [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) auf, um die [IPropertyProxyEESide-Schnittstelle](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) abzurufen. Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer [IDebugProperty3-Schnittstelle](../../../extensibility/debugger/reference/idebugproperty3.md) auf, um die [IPropertyProxyProvider-Schnittstelle](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) abzurufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die `IEEDataStorage` Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Ruft die angegebene Anzahl von Datenbytes in einem bereitgestellten Puffer ab.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Ruft die Anzahl der verfügbaren Datenbytes ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird von einer Typvisualisierung verwendet, um auf Daten zuzugreifen, die von einem bestimmten Objekt gehalten werden. Die Daten werden als Array von Bytes behandelt, sodass die Typvisualisierung sie auf jede Art und Weise bearbeiten kann, die erforderlich ist, um sie dem Benutzer zu präsentieren.

 Ein benutzerdefinierter Viewer kann diese Schnittstelle auch verwenden, wenn gewünscht, obwohl ein benutzerdefinierter Viewer in der Regel eine benutzerdefinierte Schnittstelle, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) oder [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (für Zeichenfolgen-orientierte Daten) verwenden würde.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
