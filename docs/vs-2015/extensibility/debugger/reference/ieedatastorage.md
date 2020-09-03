---
title: Ieedatastorage | Microsoft-Dokumentation
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
ms.openlocfilehash: ad398380c7c951b99e7d84283355ee9d31955173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704733"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Bytearray dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Ausdrucks Auswertung (EE) implementiert diese Schnittstelle, um ein Bytearray darzustellen (wird von typvisualisierungen zum Abrufen und Ändern von Daten über die [ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) -Schnittstelle verwendet). Der EE implementiert diese Schnittstelle in der Regel, um externe typvisualisierungen zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die-Methoden der- `IPropertyProxyEESide` Schnittstelle geben diese Schnittstelle zurück. Rufen Sie [getpropertyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) auf, um die [ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) -Schnittstelle zu erhalten. Rufen Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle auf, um die [ipropertyproxyprovider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) -Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Die- `IEEDataStorage` Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Ruft die angegebene Anzahl von Daten Bytes in einen angegebenen Puffer ab.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Ruft die Anzahl der verfügbaren Daten Bytes ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle wird von einer typschnell Ansicht verwendet, um auf Daten zuzugreifen, die von einem bestimmten Objekt gespeichert werden. Die Daten werden als Bytearray behandelt, sodass die typschnell Ansicht diese auf die gleiche Weise bearbeiten kann, wie Sie dem Benutzer zur Verfügung gestellt wird.  
  
 Ein benutzerdefinierter Viewer kann bei Bedarf auch diese Schnittstelle verwenden, obwohl ein benutzerdefinierter Viewer in der Regel eine benutzerdefinierte Schnittstelle, [getmemorybytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) oder [getstringchars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (für Zeichen folgen orientierte Daten) verwendet.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
