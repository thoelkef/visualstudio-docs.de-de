---
title: IDebugStopCompleteEvent2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b64c9719c6d2975829451dbf11cf584f98805c1b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780476"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die Debug-Engine (DE) kann dieses optionale Ereignis für die Sitzung Debug-Manager (SDM) senden, wenn ein Programm beendet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Dies ist eine neue Schnittstelle für [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Asynchrones beenden wurde von frühere Versionen nicht unterstützt.  
  
 [Beenden Sie](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird aufgerufen, durch die SDM mit mehreren Prozessen oder mit mehreren Programm Szenarios. Wenn ein Programm eine Beenden-Ereignis, das SDM sendet, fordert das SDM andere Programme zu beenden.  
  
 Es wird verwendet, um asynchron die SDM zu informieren, die ein Programm beendet wurde. Dies ist nützlich für ein Interpreter Debug-Engine, manchmal ist, in denen kein Code innerhalb des gedebuggten Programms ausgeführt, sodass [beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nicht synchron abgeschlossen werden kann. Wenn eine Debug-Engine diese asynchrone Benachrichtigung einsetzen will, muss es zurückgeben `S_ASYNC_STOP` aus [beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

