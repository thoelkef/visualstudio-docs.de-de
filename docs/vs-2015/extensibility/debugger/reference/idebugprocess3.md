---
title: IDebugProcess3 | Microsoft-Dokumentation
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
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab646482762d9175a682b55691d012b2facef5f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524407"
---
# <a name="idebugprocess3"></a>IDebugProcess3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProcess3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess3).  
  
Diese Schnittstelle stellt einen laufenden Prozess und seine Programme. Diese Schnittstelle vorhanden ist, als Ersatz für einige Methoden in der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle. Es stellt die Kontrolle über alle Programme im Prozess bereit.  
  
> [!NOTE]
>  [Weiterhin](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), und [Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md) Methoden sind veraltet und sollte nicht mehr verwendet werden. Verwenden Sie die entsprechenden Methoden auf die `IDebugProcess3` Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von einem benutzerdefinierten Port Lieferanten zum Verwalten von Programmen als Gruppe implementiert. Wenn Programme als Gruppe verwaltet werden, können Sie ihre Ausführung steuern und richten Sie eine Sprache für eine ausdrucksauswertung. Diese Schnittstelle muss von den Anschlusslieferanten implementiert werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist in erster Linie durch die sitzungsbasierter Debug-Manager (SDM) aufgerufen, um die Interaktion mit einer Gruppe von Programmen, die in diesem Prozess identifiziert.  
  
 Rufen Sie [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf eine [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` die folgenden Methoden implementiert.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Wird fortgesetzt, Ausführung oder einen Prozess durchlaufen.|  
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Beginnt die Ausführung eines Prozesses.|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Schritte weiter eine Anweisung oder im Prozess-Anweisung.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ruft die Ursache, dass der Prozess zum Debuggen gestartet wurde.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Die hosting-Sprache festgelegt so, dass die Debug-Engine die geeigneten ausdrucksauswertung laden kann.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Ruft die derzeit für diesen Prozess festgelegten Sprache ab.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deaktiviert die bearbeiten und Fortfahren "(ENC) für diesen Prozess.<br /><br /> Ein benutzerdefinierten Port Lieferanten dieser Methode nicht implementiert (es sollte immer zurückgeben `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Den ENC-Status für diesen Prozess zu erhalten.<br /><br /> Ein benutzerdefinierten Port Lieferanten dieser Methode nicht implementiert (es sollte immer zurückgeben `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Ruft ein Array von eindeutigen Bezeichnern für verfügbare Debug-Engines.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

