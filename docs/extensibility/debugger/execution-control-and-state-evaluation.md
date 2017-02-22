---
title: "Steuerung der Ausf&#252;hrung und Auswertung Zustand | Microsoft Docs"
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
  - "Debuggen [Debugging-SDK], ablaufsteuerung"
  - "Auswertung von Ausdrücken, Steuerung der Ausführung"
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Steuerung der Ausf&#252;hrung und Auswertung Zustand
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debuggen einer Anwendung erfordert die Ausführung Steuerelement mit Funktionen wie die schrittweise Ausführung von Funktionen an Haltepunkten anhalten und Fortsetzen der Ausführung zu implementieren. Visual Studio-debugging Basen werden die Steuerung der Ausführung auf Ereignisse zwischen Debuggerkomponenten gesendet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Programmsteuerung](../../extensibility/debugger/program-control.md)  
 Listet die folgenden Routinen, die auf der Ebene des Programms auftreten: Festlegen der nächsten Anweisung, Ausführung, schrittweises Ausführen, Sie den Vorgang fortsetzen, Anhalten und fortsetzen.  
  
 [Haltepunkt-bezogenen Methoden](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definiert die Grenze und ausstehende Typen von Haltepunkten, die Visual Studio unterstützt.  
  
 [Call Stack Auswertung](../../extensibility/debugger/call-stack-evaluation.md)  
 Beschreibt die Implementierung der Methoden, mit die Anzeige der Stapelrahmen der Aufrufliste im Unterbrechungsmodus können.  
  
 [Auswertung von Ausdrücken](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Erklärt, wie die Debugging-Modul (DE) Ausdruck Evaluation (EE) und Sitzung Debug-Managers in die Analyse beteiligt sind, und Auswertung eines Ausdrucks in eines der Fenster der IDE eingegeben.  
  
 [Steuerelementereignisse](../../extensibility/debugger/control-events.md)  
 Beschreibt die Schnittstelle, die zum Senden von Ereignissen während der gesteuerte Ausführung des Programms an.