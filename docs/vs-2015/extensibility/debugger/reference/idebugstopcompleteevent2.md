---
title: IDebugStopCompleteEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546919"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die Debug-Engine (de) kann dieses optionale Ereignis an den Sitzungs-Debug-Manager (SDM) senden, wenn ein Programm beendet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Dies ist eine neue Schnittstelle für [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Frühere Releases haben das asynchrone beenden nicht unterstützt.  
  
 " [Beendet](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " wird von SDM in Szenarios mit mehreren Prozessen oder mehreren Programmen aufgerufen. Wenn ein Programm ein anhalteereignis an SDM sendet, fordert der SDM auch andere Programme an, die ebenfalls beendet werden.  
  
 Sie wird verwendet, um die SDM asynchron zu informieren, dass ein Programm beendet wurde. Dies ist nützlich für eine interpreterdebug-Engine, bei der manchmal kein Code im debuggten Programm ausgeführt wird. Daher kann " [Beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " nicht synchron abgeschlossen werden. Wenn eine Debug-Engine diese asynchrone Benachrichtigung verwenden möchte, muss Sie von "Ende" zurückgegeben werden `S_ASYNC_STOP` . [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
