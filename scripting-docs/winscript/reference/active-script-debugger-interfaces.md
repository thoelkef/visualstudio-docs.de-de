---
title: Active Script-Debuggerschnittstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f260df5a23ef6b5ef6ef7253726b1fea7bc00269
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855429"
---
# <a name="active-script-debugger-interfaces"></a>Active Script-Debuggerschnittstellen
Die Headerdateien "activdbg.h" und "activdbg100.h" stellen die in diesem Abschnitt aufgeführten Schnittstellen, Enumerationen und Strukturen bereit. Sie dienen dem Debuggen von Skripts.  
  
> [!NOTE]
>  Die `IJSDebug*`-Schnittstellen und die `IEnumJsStackFrames`-Schnittstelle waren erstmalig in Internet Explorer 11 für das Debuggen von systemeigenem Code mit Skript enthalten. Die Headerdatei für diese Schnittstellen ist "jscript9diag.h".  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die folgenden Schnittstellen ermöglichen sprachneutrales, hostneutrales Debuggen:  
  
- [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
- [IActiveScriptDebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md)  
  
- [IActiveScriptErrorDebug-Schnittstelle](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
- [IActiveScriptErrorDebug110-Schnittstelle](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
- [IActiveScriptSiteDebug-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
- [IActiveScriptSiteDebug32-Schnittstelle](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
- [IActiveScriptSiteDebugEx-Schnittstelle](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
- [IActiveScriptWinRTErrorDebug-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
- [IApplicationDebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)  
  
- [IApplicationDebuggerUI-Schnittstelle](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
- [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)  
  
- [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md)  
  
- [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)  
  
- [IDebugApplicationNode100-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
- [IDebugApplicationNodeEvents-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
- [IDebugApplicationThread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)  
  
- [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
- [IDebugApplicationThreadEvents110-Schnittstelle](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
- [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)  
  
- [IDebugAsyncOperationCallBack-Schnittstelle](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
- [IDebugCodeContext-Schnittstelle](../../winscript/reference/idebugcodecontext-interface.md)  
  
- [IDebugCookie-Schnittstelle](../../winscript/reference/idebugcookie-interface.md)  
  
- [IDebugDocument-Schnittstelle](../../winscript/reference/idebugdocument-interface.md)  
  
- [IDebugDocumentContext-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
- [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
- [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)  
  
- [IDebugDocumentInfo-Schnittstelle](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
- [IDebugDocumentProvider-Schnittstelle](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
- [IDebugDocumentText-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)  
  
- [IDebugDocumentTextAuthor-Schnittstelle](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
- [IDebugDocumentTextEvents-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
- [IDebugDocumentTextExternalAuthor-Schnittstelle](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
- [IDebugExpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)  
  
- [IDebugExpressionCallBack-Schnittstelle](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
- [IDebugExpressionContext-Schnittstelle](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
- [IDebugFormatter-Schnittstelle](../../winscript/reference/idebugformatter-interface.md)  
  
- [IDebugHelper-Schnittstelle](../../winscript/reference/idebughelper-interface.md)  
  
- [IDebugSessionProvider-Schnittstelle](../../winscript/reference/idebugsessionprovider-interface.md)  
  
- [IDebugSessionProviderEx-Schnittstelle](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
- [IDebugStackFrame-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)  
  
- [IDebugStackFrameSniffer-Schnittstelle](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
- [IDebugStackFrameSnifferEx-Schnittstelle](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
- [IDebugSyncOperation-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)  
  
- [IDebugThreadCall-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md)  
  
- [IEnumDebugApplicationNodes-Schnittstelle](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
- [IEnumDebugCodeContexts-Schnittstelle](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
- [IEnumDebugExpressionContexts-Schnittstelle](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
- [IEnumDebugStackFrames-Schnittstelle](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
- [IEnumJsStackFrames-Schnittstelle](../../winscript/reference/ienumjsstackframes-interface.md)  
  
- [IEnumRemoteDebugApplications-Schnittstelle](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
- [IEnumRemoteDebugApplicationThreads-Schnittstelle](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
- [IJsDebug-Schnittstelle](../../winscript/reference/ijsdebug-interface.md)  
  
- [IJsDebugBreakPoint-Schnittstelle](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
- [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
- [IJsDebugFrame-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)  
  
- [IJsDebugProcess-Schnittstelle](../../winscript/reference/ijsdebugprocess-interface.md)  
  
- [IJsDebugProperty-Schnittstelle](../../winscript/reference/ijsdebugproperty-interface.md)  
  
- [IJsDebugStackWalker-Schnittstelle](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
- [IJsEnumDebugProperty-Schnittstelle](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
- [IMachineDebugManager-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)  
  
- [IMachineDebugManagerCookie-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
- [IMachineDebugManagerEvents-Schnittstelle](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
- [IProcessDebugManager-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
- [IProvideExpressionContexts-Schnittstelle](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
- [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)  
  
- [IRemoteDebugApplication110-Schnittstelle](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
- [IRemoteDebugApplicationEx-Schnittstelle](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
- [IRemoteDebugApplicationEvents-Schnittstelle](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
- [IRemoteDebugApplicationThread-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
- [IRemoteDebugApplicationThreadEx-Schnittstelle](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
- [ISetNextStatement-Schnittstelle](../../winscript/reference/isetnextstatement-interface.md)  
  
- [ISimpleConnectionPoint-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
- [IWebAppDiagnosticsSetup-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
- [IWebAppDiagnosticsObjectInitialization-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
  Im folgenden Abschnitt sind die für das Debuggen verwendeten Konstanten, Enumerationen und Strukturen aufgeführt:  
  
- [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen mit Active Script – Übersicht](../../winscript/active-script-debugging-overview.md)