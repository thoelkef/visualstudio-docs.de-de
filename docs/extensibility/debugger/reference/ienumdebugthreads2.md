---
title: "IEnumDebugThreads2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2"
helpviewer_keywords: 
  - "IEnumDebugThreads2"
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Dieses interfac listet die Threads auf, die in die Debugsitzung der derzeit ausgeführt werden.  
  
## Syntax  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um eine Liste von Threads in einem Programm darzustellen.  
  
## Hinweise für Aufrufer  
 Rufen Sie [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) an, die zum Abrufen dieser Schnittstelle, die eine Liste aller Threads in Alle Programme darstellt, die in einem Prozess ausgeführt werden.  Rufen Sie [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) an, die zum Abrufen dieser Schnittstelle, die eine Liste von Threads darstellt, die in ein Programm aus.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugThreads2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Ruft eine angegebene Anzahl von Threads in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Überspringt eine angegebene Anzahl von Threads in der Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Ruft die Anzahl der Threads in einem Enumerator ab.|  
  
## Hinweise  
 Visual Studio ruft in der Regel diese Schnittstelle, um **Threads** Fensters sowie zum Aktualisieren der erste Thread zu erhalten, um der Liste [Ausführen](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Weiter](../../../extensibility/debugger/reference/idebugprocess3-continue.md)und [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)aufzurufen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Weiter](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Ausführen](../../../extensibility/debugger/reference/idebugprocess3-execute.md)