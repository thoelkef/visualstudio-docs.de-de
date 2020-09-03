---
title: Eventattribute | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3026845be9aa6623d6c5cd42406385e8c5c2a11e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149376"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Ereignis Attribute an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>Member  
 EVENT_ASYNCHRONOUS  
 Gibt an, dass das Ereignis asynchron ist und keine Antwort auf das Ereignis benötigt wird.  
  
 EVENT_SYNCHRONOUS  
 Gibt an, dass das Ereignis synchron ist. Antworten mithilfe von [continuefromsynchronoutsvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT_STOPPING  
 Gibt an, dass dies ein anhalteereignis ist. Muss mit oder kombiniert werden `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS` .  
  
 EVENT_ASYNC_STOP  
 Gibt ein asynchrones anhalteereignis an. Zurzeit ist kein derartiges Ereignis vorhanden. Dieses Flag ist nur ein Platzhalter.  
  
 EVENT_SYNC_STOP  
 Gibt ein synchrones anhalteereignis an (eine Kombination aus `EVENT_SYNCHRONOUS` und `EVENT_STOPPING` ). Dieser Wert wird von einer Debug-Engine (de) verwendet, wenn ein anhalteereignis gesendet wird. Die Antwort wird durch einen aufzurufenden [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)-, [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)-oder [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)-Befehl gemacht.  
  
 EVENT_IMMEDIATE  
 Gibt ein Ereignis an, das sofort und synchron an die IDE gesendet wird. Dieses Flag wird mit anderen Flags wie `EVENT_ASYNCHRONOUS` , oder kombiniert, `EVENT_SYNCHRONOUS` `EVENT_SYNC_STOP` um den Ereignistyp anzugeben, und die Tatsache, dass der Antwortmechanismus (sofern vorhanden) bekannt ist.  
  
 EVENT_EXPRESSION_EVALUATION  
 Das Ereignis ist das Ergebnis der Ausdrucks Auswertung.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Werte werden im- `dwAttrib` Parameter der [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode übergeben.  
  
 Diese Werte können mit einem bitweisen kombiniert werden `OR` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Continuefromsynchronouabvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
