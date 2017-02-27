---
title: "IDebugCodeContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2"
helpviewer_keywords: 
  - "IDebugCodeContext2-Schnittstelle"
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt die Startposition einer Code Anweisung dar.  Für die meisten von heute architekturen können Code in einem Kontext für eine Adresse datenstrom des Programms Laufzeit beibehalten werden.  
  
## Syntax  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul implementiert diese Schnittstelle, um die Position einer Anweisung Code zu einer Position Dokumente zu verknüpfen.  
  
## Hinweise für Aufrufer  
 Methoden in zahlreichen Schnittstellen geben diese Schnittstelle in der Regel [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)zurück.  Er wird auch in großem Umfang der [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)\-Schnittstelle sowie in den Haltepunkt auflösungs werden.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden der [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ruft den Dokumentenkontext ab, der dem aktiven Kontext des Codes entspricht.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ruft die Sprachinformationen für diesen Code Elementkontext ab.|  
  
## Hinweise  
 Der Hauptunterschied zwischen einer `IDebugCodeContext2`\-Schnittstelle und einer [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Schnittstelle ist, dass `IDebugCodeContext2` immer Anweisung\-ausgerichtet ist.  Dies bedeutet, dass `IDebugCodeContext2` sich immer auf den Anfang einer Anweisung wird, während `IDebugMemoryContext2` möglicherweise zu jedem Byte des Arbeitsspeichers in der Architektur der Laufzeit zeigt.  `IDebugCodeContext2` anstelle von Anweisungen wird durch die Größe Basisspeicher erhöht \(in der Regel Byte\).  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [Nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)