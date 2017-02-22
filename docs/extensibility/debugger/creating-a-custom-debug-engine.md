---
title: "Erstellen einer benutzerdefinierten Debugmodul | Microsoft Docs"
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
  - "Debugmodule, implementieren"
  - "benutzerdefinierte Debugmodule"
  - "Debuggen von benutzerdefinierten Debugmodule [Debugging-SDK]"
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen einer benutzerdefinierten Debugmodul
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Debuggen Modul \(DE\) ist eine Komponente, die das Debuggen von bestimmten Ablauf architekturen zulässig.  Es gibt in der Regel nur ein DE implementation pro Laufzeitumgebung.  
  
> [!NOTE]
>  Während es separates DE implementations für Transact\-SQL und JScript gibt, geben VBScript und JScript einzelne DE frei.  
  
 DE arbeitet mit dem Interpreter\- oder Operation System, um solche Debugdienste wie Haltepunkte Execution Control und Ausdrucksauswertung bereitzustellen.  Diese Dienste werden von DE interfaces implementiert und können den Debugger für den Übergang zwischen verschiedenen Betriebsweisen verursachen.  Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).  
  
 Das Erstellen von DE besteht aus den folgenden Schritten:  
  
1.  Registrieren von Visual Studio mit DE  
  
2.  Ein gedebuggt werden soll Programm aktivieren  
  
3.  Ausführungssteuerungs\- Auswertung und das Feld Status  
  
4.  Senden von Ereignissen  
  
5.  Trennen und Beenden  
  
## In diesem Abschnitt  
 [Registrieren einer benutzerdefinierten Debugmodul](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Erläutert die Schritte, die erforderlich sind, um eine Debug\- Modul mit Visual Studio zu registrieren, damit er verwendet werden kann.  
  
 [Ein Programm zum Debuggen aktivieren](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Erläutert das Debuggen eines Programms DE, bevor Sie das erste Mal starten, kann es zu einem vorhandenen oder DE Programm anhängen müssen.  
  
 [Steuerung der Ausführung und Status Bewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Erläutert, warum das Debuggen einer Anwendung Ausführungssteuerungs das Implementieren von Features erforderlich ist.  
  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)  
 Beschreibt die Kommunikation zwischen dem Debugger und DE als Ereignismodell auf der Grundlage von DCOM.  
  
 [Beenden und Abtrennen](../../extensibility/debugger/termination-and-detaching.md)  
 Erklärt, wie normale Beendigung, was bedeutet, dass keine Haltepunkte, Endlosschleifen oder Laufzeitfehler Ausnahmen in der Anwendung gedebuggt werden soll wird.  
  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumentiert die aufrufende Reihenfolge der Ereignisse, die in einer Debugsitzung auftreten.  
  
 [Gewusst wie: Debuggen einer benutzerdefinierten Debugmodul](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Erläutert, wie ein benutzerdefinierter DE gedebuggt.  
  
## Siehe auch  
 [Visual Studio\-Debugger\-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)