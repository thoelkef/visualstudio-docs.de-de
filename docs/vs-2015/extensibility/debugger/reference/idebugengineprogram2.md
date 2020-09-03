---
title: IDebugEngineProgram2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c265cbfc89d0b637b1d2f37a3e3b9e948a8dd8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687788"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle bietet Multithread-Debugunterstützung.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von einer Debug-Engine implementiert, um das gleichzeitige Debuggen mehrerer Threads Diese Schnittstelle wird auf demselben Objekt implementiert, das die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle implementiert.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , um diese Schnittstelle von einer `IDebugProgram2` Schnittstelle abzurufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugEngineProgram2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[Beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Beendet alle Threads, die in diesem Programm ausgeführt werden.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Überwacht, dass die Ausführung auf dem angegebenen Thread erfolgt (oder die Ausführung der Ausführung beendet wird).|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Ermöglicht (oder verweigert) die Ausdrucks Auswertung auf dem angegebenen Thread, auch wenn das Programm beendet wird.|  
  
## <a name="remarks"></a>Bemerkungen  
 Visual Studio ruft diese Schnittstelle als Reaktion auf ein [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis auf und legt den Status "nach Thread Schritt überwachen" und "Überwachung der Ausdrucks Auswertung auf Thread" des Programms fest. " [Beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " wird immer dann aufgerufen, wenn das Programm beendet werden soll. Diese Methode gibt dem Programm die Möglichkeit, alle Threads zu beenden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
