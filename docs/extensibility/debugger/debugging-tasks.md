---
title: "Debugging-Aufgaben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] Aufgaben"
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Debugging-Aufgaben
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Um ein Programm zu debuggen, muss er gestartet werden und eine Debug\- Modul \(DE\) oder ihm muss auf DE angefügt werden zu einem vorher aufgerufenen Programms muss angefügt sein.  Sobald angefügt, muss DE bestimmte Ereignisse Start generieren.  Als Antwort darauf versucht das Paket debuggen, die Haltepunkte zu binden, die in der IDE festgelegt werden.  Wenn das Programm einen gebundenen Haltepunkt trifft, erstellt er ein und wartet auf Benutzereingaben.  
  
## In diesem Abschnitt  
 [Sicherheitsprobleme](../../extensibility/debugger/security-issues.md)  
 Erläutert die Schritte, die erforderlich sind, um ein Programm zu debuggen.  
  
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)  
 Stellt schrittweise Anweisungen darüber, wie DE angibt, in dem das Betriebssystem aufgerufen wird, um das Programm zu starten.  
  
 [Anfügen an ein Programm direkt](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Beschreibt den Prozess, der verwendet wird, um ein Programm in einem Prozess debuggen, der bereits ausgeführt wird.  
  
 [Senden Startereignisse nach einem starten](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Führt die Ereignisse aufgeführt, die einmal DE auf das Programm angefügt ist möglich, bis das Programm an seiner Haupteinstiegspunkt ist und zum Debugging bereit ist.  
  
 [Steuerung der Ausführung](../../extensibility/debugger/control-of-execution.md)  
 Erläutert das DE i. d. R. ein Einstiegspunkt für Auswahlereignisse, ein Ereignis oder ein LOAD\-vollständiges aufhörendes Ereignis sendet, je nach den Umständen.  
  
 [Binden der Haltepunkte](../../extensibility/debugger/binding-breakpoints.md)  
 Beschreibt, wie z. B., wenn die Benutzer legt einen Haltepunkt, die IDE die Anforderungen formuliert, und die Debugsitzung aufgefordert wird, den Haltepunkt zu erstellen.  
  
 [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)  
 Erklärt, wie Ausdrücke erstellt werden und was geschieht, wenn ein Ausdruck ausgewertet wird.  
  
 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Erläutert das Typ schnellansichten und benutzerdefinierten Viewer aus dem Ausdrucksauswertung \(EE\) unterstützt werden.  
  
## Verwandte Abschnitte  
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die Architektur wichtigsten Konzepte des Debuggens.  
  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die Visual Studio\-Debuggings Komponenten bereit, die die DE EE Symbol und den Ereignishandler \(SH\) enthalten.  
  
 [Debugger\-Kontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert das DE gleichzeitig innerhalb des Codes, der Dokumentation und den Ausdrucksauswertungs kontexte funktioniert.  Beschreibt für jede der drei Kontexten, des Speicherorts, der Position oder der Auswertung, die relevant ist.  
  
## Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)