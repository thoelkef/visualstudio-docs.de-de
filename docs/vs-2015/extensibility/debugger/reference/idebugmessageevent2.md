---
title: IDebugMessageEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c2b76d0972768bf4d77e7f6d9bd153920799970
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947314"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird von der Debug-Engine (DE) verwendet, zum Senden einer Nachricht zu Visual Studio, die eine Antwort des Benutzers erforderlich sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle zum Senden einer Nachricht zu Visual Studio, die eine Antwort des Benutzers erforderlich sind. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
 Die Implementierung dieser Schnittstelle muss Visual Studio Aufruf kommunizieren [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) de. Beispielsweise dazu mit der Meldung an die DE Meldungsbehandlung Thread gesendet oder das Objekt, das diese Schnittstelle implementiert konnte enthalten einen Verweis auf den DE und einen Rückruf an, die DE mit der Antwort übergebenen `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet dieses Ereignisobjekt, eine Meldung an den Benutzer an, die eine Antwort erforderlich sind. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn es um das derzeit debuggte Programm angefügt wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugMessageEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ruft die Meldung ab, die angezeigt werden.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Legt die Antwort fest, sofern vorhanden, aus der MessageBox.|  
  
## <a name="remarks"></a>Hinweise  
 Die DE wird diese Schnittstelle verwenden, wenn eine bestimmte Antwort des Benutzers für eine bestimmte Nachricht erforderlich ist. Wenn die DE Fehlermeldung "Zugriff verweigert" nach einem Versuch, Remote Anfügen an ein Programm empfängt, sendet der DE jeweilige Nachricht z. B. zu Visual Studio in eine `IDebugMessageEvent2` -Ereignis mit den Message Box-Stil `MB_RETRYCANCEL`. Dadurch kann der Benutzer zu wiederholen oder Abbrechen den Anfügevorgang.  
  
 Die DE gibt an, wie diese Nachricht verarbeitet werden, indem Sie gemäß den Konventionen der Win32-Funktion `MessageBox` (finden Sie unter [AfxMessageBox](http://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) Einzelheiten).  
  
 Verwenden der [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) Schnittstelle zum Senden von Nachrichten an Visual Studio, die nicht über eine Antwort des Benutzers erfordern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
