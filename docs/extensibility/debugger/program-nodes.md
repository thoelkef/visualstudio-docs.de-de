---
title: Programmieren von Knoten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90ec92ad46a850c26e700e9feafa60d291f608ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="program-nodes"></a>Programm-Knoten
Im Hinblick auf die Architektur des Debuggers einen **Programm Knoten**:  
  
-   Ist eine einfache Beschreibung eines Programms.  
  
-   Erkennen selbst und den Prozess, den es im ausgeführt wird, den und von getrennt, und beschreiben das Debugmodul (DE), die sie ggf. erstellt angefügt werden kann.  
  
-   Dargestellt durch eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle, die in der Regel von einem DE oder Port erstellt. Programm-Knoten werden an einen Port hinzugefügt, indem [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Wenn ein Programm Knoten mit einem Port hinzugefügt wird, wird er hinzugefügt, an den Prozess mit dem Programm, das diesem Programm Knoten darstellt.  
  
 Einige Zeit, nachdem Sie eine Debugsitzung gestartet wird, abhängig von der Implementierung des Debug-Pakets werden Programm-Knoten verwendet, um entsprechende Programme zu erstellen. Wenn ein Prozess für seinen Programmen abgefragt wird, werden die Programme aufgelistet, eine für jeden Knoten des Programms.  
  
 Bevor Sie ein Programm angefügt ist, benötigt die IDE nur eine einfache Beschreibung des Programms an. Diese Informationen können vom Programm Knoten abgerufen werden. Sobald die Anwendung angefügt ist, muss die IDE anzuzeigenden Ausführlichere Informationen, z. B. eine Liste aller Threads im Programm ausgeführt wird. Diese Informationen werden vom Programm selbst abgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Programme](../../extensibility/debugger/programs.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debuggen des Datenbankmoduls](../../extensibility/debugger/debug-engine.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)