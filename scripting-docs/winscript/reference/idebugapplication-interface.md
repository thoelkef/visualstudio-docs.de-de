---
title: "IDebugApplication-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication-Schnittstelle"
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplication-Schnittstelle
Macht NichtRemote Debugmethoden für Sprachmodule und Hosts verfügbar.  
  
 Zusätzlich zu den von `IRemoteDebugApplication` geerbten Methoden macht die `IDebugApplication`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Legt den Namen der Anwendung fest.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Benachrichtigt den Debug\- ProzessManager, dass ein Sprachmodul im einschrittigen Modus im Begriff ist, an dessen Aufrufer zurückzukehren.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Ruft die angegebene Zeichenfolge, vom Debugger IDE angezeigt werden.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Stellt den Standard Debugger IDE auf und fügt eine Debugsitzung zu dieser Anwendung an, wenn nicht bereits angefügt wird.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Veranlasst den aktuellen Thread zu blockieren und sendet eine Benachrichtigung des Haltepunkts an den Debugger IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Verursacht diese Anwendung, alle Verweise freizugeben und einen inaktiven Zustand übergeht.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Gibt die aktuellen Unterbrechungsflags für die Anwendung zurück.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Gibt den Thread zurück, der mit dem aktuell ausgeführten Thread zugeordnet ist.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Bietet asynchronen Zugriff auf einen angegebenen synchronen Debugvorgang.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Fügt einen Stapelrahmenenumeratoranbieter dieser Anwendung hinzu.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Entfernt einen Stapelrahmenenumeratoranbieter aus der Anwendung.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Bestimmt, ob der aktuelle Betriebsthread der Debuggerthread ist.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Stellt einen Mechanismus für den Aufrufer um Code im Debuggerthread bereit.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Erstellt einen Neuanmeldungsknoten, der mit einem Anbieter für spezielle Dokuments zugeordnet ist.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Löst ein generisches Ereignis zur `IApplicationDebugger`\-Schnittstelle des Debuggers aus.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Veranlasst den aktuellen Thread zu blockieren und sendet eine Benachrichtigung des Fehlers an den Debugger IDE.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Bestimmt, ob ein Just\-in\-Time\-Debugger \(JIT\) registriert ist.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Bestimmt, ob ein JIT\-Debugger zu stummen Hosts AUTODEBUGs registriert wird.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Fügt einen globalen Ausdruckskontextanbieter dieser Anwendung hinzu.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Entfernt einen globalen Ausdruckskontextanbieter aus der Anwendung.|