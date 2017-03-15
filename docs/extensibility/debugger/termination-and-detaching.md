---
title: "Beenden und Abtrennen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Programme, die Beendigungsereignisse"
  - "Debugmodule, Trennen von Programmen"
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Beenden und Abtrennen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden werden die normale Beendigung.  
  
## Erörterung  
 Nach [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)\-Schnittstelle wird, wenn keine Haltepunkte, Endlosschleifen oder Laufzeitfehler Ausnahmen in der Anwendung gedebuggt werden sollen, gibt das Programm, das gedebuggt wird fortgesetzt, bis zum Abschluss ausgeführt wird.  Dies ist eine normale Beendigung.  
  
 Sie müssen [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) senden, um normale Beendigung zu implementieren.  Dies erfordert das Implementieren der [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)\-Methode.  
  
## Siehe auch  
 [Erstellen einer benutzerdefinierten Debugmodul](../../extensibility/debugger/creating-a-custom-debug-engine.md)