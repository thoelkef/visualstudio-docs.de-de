---
title: IEEDataStorage | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5d102a4a9cf7946e135ec8f6cdbff44015d3b47
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959222"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Array von Bytes.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung (EE) implementiert diese Schnittstelle, um ein Array von Bytes darstellen (von Typ-Schnellansichten verwendet werden, abrufen und Ändern von Daten über die [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Schnittstelle). Die EE wird in der Regel implementiert diese Schnittstelle, um externen Typ-Schnellansichten unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die Methoden für die `IPropertyProxyEESide` Schnittstelle, die alle zurückzugeben, diese Schnittstelle. Rufen Sie [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) zum Abrufen der [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Schnittstelle. Rufen Sie [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle zum Abrufen der [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die `IEEDataStorage` -Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Ruft die angegebene Anzahl von Datenbytes in einen angegebenen Puffer ab.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Ruft die Anzahl der Datenbytes, die zur Verfügung.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird durch eine typschnellansicht verwendet, den Zugriff auf Daten, die ein bestimmtes Objekt frei. Die Daten werden behandelt, als ein Array von Bytes, sodass der typschnellansicht, und bearbeiten sie mithilfe von bibliotheksgruppen erforderlich, um es dem Benutzer angezeigt wird.  
  
 Ein benutzerdefinierter Viewer kann diese Schnittstelle auch verwenden, falls gewünscht, zwar in der Regel eher, ein benutzerdefinierter Viewer eine benutzerdefinierte Schnittstelle, verwenden [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) oder [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (für Zeichenfolge-orientierte Daten).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
