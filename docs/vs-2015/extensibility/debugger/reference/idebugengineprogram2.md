---
title: IDebugEngineProgram2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f9af106d32cf62e8ce07b8d27dec8ae7f2c9016
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512806"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugEngineProgram2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengineprogram2).  
  
Diese Schnittstelle stellt Multithread-debugging-Unterstützung bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Debugmodul implementiert diese Schnittstelle, um das gleichzeitige Debuggen von mehreren Threads unterstützen. Diese Schnittstelle wird implementiert, für das gleiche Objekt, das implementiert die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) dieser Schnittstelle vom Abrufen einer `IDebugProgram2` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugEngineProgram2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Beendet alle Threads, die in diesem Programm ausgeführt wird.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Wird überwacht, ob die Ausführung (oder beenden, die für die Ausführung überwachen) an den angegebenen Thread ausgeführt.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Auswertung von Ausdrücken für den angegebenen Thread ausgeführt wird, auch wenn das Programm beendet wird hiermit (oder verweigert).|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio ruft diese Schnittstelle als Reaktion auf eine [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignis und die "Sehen Sie sich für die Thread-Step" und "Sehen Sie sich für Ausdruck Auswertung auf Thread" Status des Programms festlegen. [Beenden Sie](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird aufgerufen, wenn das Programm beendet werden, diese Methode gibt dem Programm die Möglichkeit, die alle Threads zu beenden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

