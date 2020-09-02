---
title: IDebugProcessCreateEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessCreateEvent2
helpviewer_keywords:
- IDebugProcessCreateEvent2
ms.assetid: c660439d-8b23-4dbb-923e-ebb5e1d7edf5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3237857d0345776fe98ae45b31c64285da6fbb0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675406"
---
# <a name="idebugprocesscreateevent2"></a>IDebugProcessCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird gesendet, wenn ein Prozess gestartet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) oder der benutzerdefinierte Port Lieferant implementiert diese Schnittstelle, um zu melden, dass ein Prozess erstellt wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für den Zugriff auf die- `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Der von de oder der benutzerdefinierte Port Lieferant erstellt und sendet dieses Ereignis Objekt, um die Erstellung eines Prozesses zu melden. Der de sendet dieses Ereignis mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird. Der benutzerdefinierte Port Lieferant sendet dieses Ereignis mithilfe der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) -Schnittstelle.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
