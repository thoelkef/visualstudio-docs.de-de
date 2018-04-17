---
title: Aufrufen der Stapel Auswertung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bcfc2f2afa622534772390df59597f6972463de8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="call-stack-evaluation"></a>Call Stack Auswertung
Um den Stapelrahmen der Aufrufliste im Unterbrechungsmodus anzeigen zu können, müssen Sie implementieren die [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) Methode.  
  
## <a name="methods-for-evaluation"></a>Methoden für die Evaluierung  
 Für eine einfache Debugmodul (DE) möglicherweise nur einen Stapelrahmen entspricht. Um den Stapelrahmen im Unterbrechungsmodus untersuchen zu können, müssen Sie die folgenden Methoden der implementieren [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Codekontext für einen Stapelrahmen entspricht. Der Codekontext stellt den aktuellen Anweisungszeiger in einen Stapelrahmen dar.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokumentenkontext für einen Stapelrahmen entspricht. Der Dokumentenkontext stellt die aktuelle Position im Quellcode für einen Stapelrahmen dar. Erforderlich für das Anzeigen des Quellcodes, wenn Sie in einem Programm beendet werden.|  
  
 Bei diesen Methoden muss die Implementierung von verschiedenen Kontext bezogene Schnittstellen und Methoden. Sie müssen deshalb Implementieren der [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) -Methode und die folgenden Methoden der [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft die Datei Anweisung Bereich eines Dokuments Kontexts ab.|  
  
 Um Code Kontexten aufzuzählen, müssen Sie die Methoden der implementieren [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)