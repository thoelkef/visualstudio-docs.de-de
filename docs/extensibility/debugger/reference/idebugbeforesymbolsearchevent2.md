---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 790aa358a40c79c7d517935192fd0155150063a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100454"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Debugging-Modul (DE) sendet diese Schnittstelle zu dem Sitzung Debug-Manager (SDM), legen Sie den Status Strich Nachricht während des Symbol lädt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle auf, wenn diese Meldung in der Statuszeile während Symbol lädt festgelegt werden muss. Diese Schnittstelle wird nur von Debugmodule implementiert, die mit arbeiten oder sind ein Teil der Skript-Interpreter. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss implementiert werden, auf das gleiche Objekt wie diese Schnittstelle (verwendet die SDM **QueryInterface** für den Zugriff auf die **IDebugEvent2** Schnittstelle).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt, wenn diese Meldung in der Statuszeile während Symbol lädt festgelegt werden muss. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM angegeben werden, wenn es an das derzeit debuggte Programm angefügt.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugBeforeSymbolSearchEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Ruft den Namen des Moduls, das gerade gedebuggt werden.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll