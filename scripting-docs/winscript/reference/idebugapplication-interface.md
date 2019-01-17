---
title: IDebugApplication-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3483bea94d7a53fabf3f552df97a681307b885c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349724"
---
# <a name="idebugapplication-interface"></a>IDebugApplication-Schnittstelle
Macht nicht-Remote-debuggingmethoden für die Verwendung von Sprach-Engines und Hosts verfügbar.  
  
 Zusätzlich zu den von geerbten Methoden `IRemoteDebugApplication`, `IDebugApplication` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Legt den Namen der Anwendung.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Benachrichtigt prozessbasierten Debug-Manager, dass es sich bei eine Sprach-Engine im einschrittigen Modus zum an den Aufrufer zurückgegeben wird.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Bewirkt, dass die angegebene Zeichenfolge von der Debugger-IDE angezeigt werden soll.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Startet den Standarddebugger-IDE, und fügt eine Debugsitzung dieser Anwendung, wenn noch nicht angefügt ist.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Bewirkt, dass den aktuelle Thread blockiert, und sendet eine Benachrichtigung des Haltepunkts an der Debugger-IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Bewirkt, dass dieser Anwendung alle Verweise freigeben, und geben einen inaktiven Status.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Gibt den aktuellen Break-Flags für die Anwendung zurück.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Gibt den Thread, der mit dem aktuell ausgeführten Thread verknüpft ist.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Bietet asynchronen Zugriff auf einen bestimmten synchronen Debugvorgang.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Diese Anwendung hinzugefügt einen Stack-Frame-Enumerator-Anbieter.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Entfernt einen Stack-Frame-Enumerator-Anbieter von dieser Anwendung.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Bestimmt, ob der aktuelle ausgeführte Thread Debugger ist.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Stellt einen Mechanismus für den Aufrufer zum Ausführen von Code im Debuggerthread.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Erstellt einen neuen Anwendungsknoten, der mit einem bestimmten Dokument Anbieter zugeordnet ist.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Wird ausgelöst, ein generisches Ereignisses des Debuggers `IApplicationDebugger` Schnittstelle.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Bewirkt, dass den aktuelle Thread blockiert, und sendet eine Benachrichtigung über den Fehler an den Debugger-IDE.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Bestimmt, ob ein just-in-Time (JIT)-Debugger registriert ist.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Bestimmt, ob ein JIT-Debugger zu dumm Auto-Debug-Hosts registriert ist.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Diese Anwendung hinzugefügt einen globalen anwendungsausdrücken Kontextanbieter.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Entfernt einen globalen anwendungsausdrücken Kontextanbieter aus dieser Anwendung an.|