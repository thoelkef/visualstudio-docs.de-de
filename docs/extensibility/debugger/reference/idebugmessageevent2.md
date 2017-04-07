---
title: IDebugMessageEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: dfbe6b139a823fa13e9ce58284026c163cc07ffa
ms.lasthandoff: 04/05/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Diese Schnittstelle wird durch die Debugging-Modul (DE) verwendet, zum Senden einer Nachricht zu Visual Studio, die eine Antwort vom Benutzer erforderlich sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle zum Senden einer Nachricht zu Visual Studio, die eine Antwort des Benutzers erfordert. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
 Die Implementierung dieser Schnittstelle muss Visual Studio-Aufruf der kommunizieren [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) de. Z. B. Dies erreichen Sie mit einer Nachricht an die DE Meldungsbehandlung-Thread gesendet oder das Objekt implementiert diese Schnittstelle konnte enthalten einen Verweis auf die DE und mit der übergebenen Antwort ein Rückruf de `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt eine Meldung an den Benutzer angezeigt, die eine Antwort erforderlich sind. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn es an das derzeit debuggte Programm angefügt ist.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugMessageEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ruft die Meldung ab, die angezeigt werden.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Legt die Antwort fest, sofern vorhanden, aus der MessageBox.|  
  
## <a name="remarks"></a>Hinweise  
 Die DE wird diese Schnittstelle verwenden, wenn eine bestimmte Reaktion des Benutzers für eine bestimmte Nachricht erforderlich ist. Wenn DE Fehlermeldung "Zugriff verweigert" nach einem Versuch, Remote an ein Programm angefügt wird, sendet der DE jeweilige Nachricht z. B. zu Visual Studio in einem `IDebugMessageEvent2` Ereignis "mit" Message Box-Stil `MB_RETRYCANCEL`. Dies ermöglicht es dem Benutzer zu wiederholen oder Abbrechen anzufügen.  
  
 Die DE gibt an, wie diese Meldung behandelt werden, indem Sie gemäß den Konventionen der Win32-Funktion `MessageBox` (finden Sie unter [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) Einzelheiten).  
  
 Verwenden der [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) Schnittstelle zum Senden von Nachrichten an Visual Studio, die nicht über eine Antwort des Benutzers erfordern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
