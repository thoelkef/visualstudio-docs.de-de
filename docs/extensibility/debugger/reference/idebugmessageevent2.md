---
title: IDebugMessageEvent2 | Microsoft-Dokumentation
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 0f033c5793dc3b89a1f2bd74a2bc4857730fb746
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Diese Schnittstelle wird von der Debugging-Modul (DE) verwendet, zum Senden einer Nachricht zu Visual Studio, die eine Reaktion des Benutzers erfordert.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle zum Senden einer Nachricht zu Visual Studio, die eine Antwort des Benutzers erfordert. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface](/visual-cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
 Die Implementierung dieser Schnittstelle muss Visual Studio-Aufruf der kommunizieren [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) de. Z. B. Dies erreichen Sie mit einer Meldung an die DE Meldungsbehandlung Thread gesendet, oder das Objekt, das diese Schnittstelle implementiert einen Verweis auf die DE und einen Rückruf an de die übergebene Antwort konnte `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt eine Meldung für den Benutzer an, die eine Antwort erforderlich sind. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch das SDM angegeben wird, wenn sie das derzeit debuggte Programm zugeordnet ist.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugMessageEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ruft die Meldung angezeigt werden.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Die Antwort wird, ggf. von der MessageBox.|  
  
## <a name="remarks"></a>Hinweise  
 Die DE verwendet diese Schnittstelle, wenn eine bestimmte Reaktion des Benutzers für eine bestimmte Nachricht erforderlich ist. Wenn DE nach einem Versuch, Remote Anfügen an ein Programm eine "Zugriff verweigert" angezeigt wird, sendet der DE diese bestimmte Nachricht z. B. Visual Studio in eine `IDebugMessageEvent2` Ereignis mit der Formatvorlage für ein Nachrichtenfeld `MB_RETRYCANCEL`. Dies ermöglicht es dem Benutzer zu wiederholen oder Abbrechen des Anhängens.  
  
 Die DE gibt an, wie diese Meldung behandelt werden, indem Sie die folgenden Konventionen für die Win32-Funktion `MessageBox` (siehe [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) Details).  
  
 Verwenden der [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) Schnittstelle zum Senden von Nachrichten an Visual Studio, die nicht über eine Reaktion des Benutzers erfordern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
