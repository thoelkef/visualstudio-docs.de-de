---
title: "IDebugStackFrame-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrame-Schnittstelle"
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame-Schnittstelle
Stellt einen logischen Stapelrahmen im Threadstapel dar.  Rufen Sie die `IDebugStackFrame::QueryInterface`\-Methode auf, um die `IDebugExpressionContext`\-Schnittstelle zu erhalten, die Ausdrucksauswertung und Überwachungsfenster zulässig.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugStackFrame`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Gibt den aktuellen Codekontext zurück, der mit dem Stapelrahmen zugeordnet ist.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Gibt eine kurze oder lange Textbeschreibung des Stapelrahmens zurück.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Gibt eine kurze oder lange Textbeschreibung der Sprache zurück.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Gibt den Thread zurück, der diesem Stapelrahmen zugeordnet ist.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Gibt einen Eigenschaftenbrowser für den aktuellen Frame zurück.|