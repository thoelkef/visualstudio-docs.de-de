---
title: Auswertung von aufrufsstapeln | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15fecbc61fec8ba7aa62ca7d79cf11c56b7ce938
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146412"
---
# <a name="call-stack-evaluation"></a>Auswertung der Aufrufliste
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um die Stapel Rahmen der aufzurufenden Auflistung im Break-Modus anzuzeigen, müssen Sie die [enumframeinfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) -Methode implementieren.  
  
## <a name="methods-for-evaluation"></a>Methoden für die Auswertung  
 Für eine einfache Debug-Engine (de) gibt es möglicherweise nur einen Stapel Rahmen. Um den Stapel Rahmen im Break-Modus zu untersuchen, müssen Sie die folgenden Methoden von [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)implementieren.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Code Kontext für einen Stapel Rahmen ab. Der Code Kontext stellt den aktuellen Anweisungs Zeiger in einem Stapel Rahmen dar.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokument Kontext für einen Stapel Rahmen ab. Der Dokument Kontext stellt die aktuelle Position im Quellcode für einen Stapel Rahmen dar. Erforderlich zum Anzeigen des Quellcodes, wenn Sie in einem Programm angehalten werden.|  
  
 Diese Methoden erfordern die Implementierung mehrerer kontextbezogener Schnittstellen und Methoden. Daher müssen Sie die [getdocumentcontext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) -Methode und die folgenden Methoden von [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)implementieren.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft den Datei Anweisungs Bereich eines Dokument Kontexts ab.|  
  
 Um Code Kontexte aufzulisten, müssen Sie alle Methoden von [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)implementieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
