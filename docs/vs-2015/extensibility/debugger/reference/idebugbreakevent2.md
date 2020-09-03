---
title: IDebugBreakEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98e8c1b1669b3fdd1f442c6987e4e9d2b9fc4835
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675378"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle weist den sitzungsdebug-Manager (SDM) darauf hin, dass eine asynchrone Unterbrechung erfolgreich abgeschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die de implementiert diese Schnittstelle, um Benutzer Umbrüche in einem Programm zu unterstützen. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden (SDM verwendet [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für den Zugriff auf die- `IDebugEvent2` Schnittstelle).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Der SDM ruft [cauanbreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) auf, wenn der Benutzer angefordert hat, dass das Programm, das gedeppt wird, angehalten werden soll. Wenn das Programm erfolgreich angehalten wurde, sendet der de das `IDebugBreakEvent2` Ereignis. Dieses Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von SDM beim Anfügen an das gedestete Programm bereitgestellt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Beispielsweise kann ein Benutzer im Menü **Debuggen** den Befehl **Alle unterbrechen** auswählen, um das Programm zu verlassen, das eine Endlosschleife ausführen soll. Der SDM weist das Programm an, durch den Aufruf von [caust Break](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)anzuhalten. Der de sendet, `IDebugBreakEvent2` Wenn das Programm beendet wird.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Causeelbreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
