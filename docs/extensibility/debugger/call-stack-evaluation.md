---
title: "Call Stack-Evaluierung | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] Call Stack Auswertung"
  - "Aufruflisten, Bewertung"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Call Stack-Evaluierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Um die Stapelrahmen der Aufrufliste während des Unterbrechungsmodus anzuzeigen, müssen Sie die [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)\-Methode implementieren.  
  
## Methoden zur Auswertung  
 Für ein einfaches Debuggen Modul \(DE\), könnte es nur einen Stapelrahmen.  Um den Stapelrahmen während des Unterbrechungsmodus zu überprüfen, müssen Sie die folgenden Arten von [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)implementieren.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Kontext des Codes für einen Stapelrahmen ab.  Der Code stellt den Kontext des aktuellen Anweisungszeiger in einem Stapelrahmen dar.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokumentenkontext für einen Stapelrahmen ab.  Der Dokumentenkontext stellt den aktuellen Position im Quellcode für einen Stapelrahmen dar.  Erforderlich zum Anzeigen von Quellcode, wenn Sie in einem Programm beendet werden.|  
  
 Diese Methoden erfordern die Implementierung einiger Kontext\-verknüpfter Schnittstellen und Methoden.  Daher müssen Sie die [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)\-Methode und die [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)der folgenden Methoden implementieren.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft den Datei im Bereich eines Dokuments für kontexts ab.|  
  
 Um Code kontexte aufzulisten, müssen Sie alle Methoden aus [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)implementieren.  
  
## Siehe auch  
 [Steuerung der Ausführung und Status Bewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)