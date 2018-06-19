---
title: IDebugApplication-Schnittstelle | Microsoft Docs
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
ms.openlocfilehash: 07964292785634212099a0bfcf8174ebb55e8713
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727440"
---
# <a name="idebugapplication-interface"></a>IDebugApplication-Schnittstelle
Macht nicht-Remote-debuggingmethoden für die Verwendung von Sprache-Module und Hosts an.  
  
 Zusätzlich zu den von geerbten Methoden `IRemoteDebugApplication`, `IDebugApplication` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Legt den Namen der Anwendung.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Benachrichtigt, dass ein Sprachmodul im einschrittigen Modus umgehend an den Aufrufer zurückgeben dem Debug-Prozess-Manager.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Bewirkt, dass die angegebene Zeichenfolge, die vom Debugger IDE angezeigt werden.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Startet die Standarddebugger IDE und fügt eine Debugsitzung für diese Anwendung, wenn nicht bereits angefügt ist.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Bewirkt, dass den aktuelle Thread blockiert, und sendet eine Benachrichtigung des Haltepunkts an den IDE-Debugger.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Bewirkt, dass diese Anwendung alle Verweise freigeben, und geben einen inaktiven Status.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Gibt die aktuelle Break-Flags für die Anwendung zurück.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Gibt den derzeit ausgeführten Thread zugeordneten Thread zurück.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Asynchrone Zugang zu einer bestimmten synchronen Debugvorgang.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Diese Anwendung hinzugefügt einen Stapel Frame Enumerator Anbieter.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Entfernt einen Stapel Frame Enumerator-Anbieter von dieser Anwendung an.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Bestimmt, ob der aktuelle ausgeführte Thread Debugger ist.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Bietet einen Mechanismus für den Aufrufer, Code im Debuggerthread auszuführen.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Erstellt einen neue Anwendungsknoten, der einem bestimmten Dokument Anbieter zugeordnet ist.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Löst ein Ereignis aus, die im Debuggers generische `IApplicationDebugger` Schnittstelle.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Bewirkt, dass den aktuelle Thread blockiert, und sendet eine Benachrichtigung über den Fehler an den IDE-Debugger.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Bestimmt, ob ein Just-in-Time (JIT)-Debugger registriert ist.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Bestimmt, ob ein Debugger JIT dumb Auto-Debug-Hosts registriert ist.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Fügt einen globalen anwendungsausdrücken Kontextanbieter auf diese Anwendung an.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Entfernt eine globale Ausdruck Kontextanbieter aus dieser Anwendung an.|