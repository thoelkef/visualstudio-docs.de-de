---
title: IDebugProcess3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21c4dfffe02d2550bccf5b23f264ab8283524aa2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121091"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Diese Schnittstelle stellt einen laufenden Prozess und seine Programme dar. Diese Schnittstelle vorhanden ist, als Ersatz für einige Methoden in der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle. Er ermöglicht die Steuerung über alle Programme im Prozess.  
  
> [!NOTE]
>  [Weiterhin](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), und [Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md) Methoden sind veraltet und sollte nicht mehr verwendet werden. Verwenden Sie die entsprechenden Methoden auf die `IDebugProcess3` Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird durch einen benutzerdefinierten Port Lieferanten Verwalten von Programmen als Gruppe implementiert. Wenn Programme als Gruppe verwaltet werden, können Sie ihre Ausführung zu steuern und richten Sie eine Sprache für eine ausdrucksauswertung auf. Diese Schnittstelle muss von den Lieferanten Port implementiert werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird in erster Linie durch die Sitzung Debug-Manager (SDM) aufgerufen, um die Interaktion mit einer Gruppe von Programmen, die in diesem Prozess identifiziert.  
  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` die folgenden Methoden implementiert.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Wird fortgesetzt, Ausführung oder das schrittweise eines Prozess.|  
|[Führen Sie](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Beginnt die Ausführung eines Prozesses.|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Eine Anweisung oder-Anweisung im Prozess Schritte weitergeleitet werden.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ruft den Grund, dass der Prozess zum Debuggen gestartet wurde.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Die hosting-Sprache festgelegt so, dass die entsprechenden ausdrucksauswertung Debugging-Modul geladen werden kann.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Ruft die Sprache, die zurzeit für diesen Prozess festgelegt.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deaktiviert die bearbeiten und Fortfahren (ENC) für diesen Prozess.<br /><br /> Implementiert ein benutzerdefinierten Port Lieferanten dieser Methode nicht (es sollten stets `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Abrufen des Status, ENC für diesen Prozess an.<br /><br /> Implementiert ein benutzerdefinierten Port Lieferanten dieser Methode nicht (es sollten stets `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Ruft ein Array von eindeutigen Bezeichnern für verfügbare Debugmodule ab.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)