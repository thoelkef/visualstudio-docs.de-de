---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e92138f969189a33e1a5aad5a083c8ac57852dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
Debugging-Modul (DE) kann die Sitzung Debug-Manager (SDM) dieses optionale Ereignis senden, Beendigung ein Programms.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Dies ist eine neue Schnittstelle für [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Asynchrone beenden wurde von frühere Versionen nicht unterstützt.  
  
 [Beenden Sie](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) durch die SDM in Prozessen oder ein Programm mit mehreren Szenarien aufgerufen wird. Wenn ein Programm, das SDM Stopping-Ereignis gesendet wird, fordert die SDM andere Programme zu beenden.  
  
 Es wird verwendet, um die SDM asynchron zu informieren, die eine Anwendung beendet wurde. Dies ist nützlich für ein Interpreter-Debugging-Modul, in dem in einigen Fällen kein Code innerhalb des zu debuggenden Programms ausgeführt wird, damit [beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) kann nicht synchron abgeschlossen werden. Wenn ein Debugmodul diese asynchrone Benachrichtigung verwendet möchte, muss er zurück `S_ASYNC_STOP` aus [beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll