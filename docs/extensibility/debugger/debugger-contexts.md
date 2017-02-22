---
title: "Debugger-Kontexte | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] Kontexten"
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Debugger-Kontexte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In debuggendem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , funktioniert das Debugmodul \(DE\) gleichzeitig innerhalb mehrerer unterschiedlicher Kontexte wie folgt:  
  
-   Der Code, der vom Kontext der aktuellen Position in einem Laufzeit des Programms datenstrom beschreibt.  
  
-   Der Dokumentation Elementkontext oder Position, die die aktuelle Position innerhalb des Quelldokuments beschreibt.  
  
-   Der Kontext Ausdrucksauswertungs, der den Kontext beschreibt, in dem Ausdrucksauswertung stattfindet.  
  
## In diesem Abschnitt  
 [Code\-Kontext](../../extensibility/debugger/code-context.md)  
 Erläutert Code in einem Kontext als Adresse in den Anweisungsstream des Programms nicht gegen architekturen Laufzeit heutigen traditionele Sprachen, in denen Code nicht von Anweisungen dargestellt wird, aber eine andere Ressourcen.  
  
 [Dokumenten\-Position](../../extensibility/debugger/document-position.md)  
 Definiert die Zeilenposition in Visual Studio\-Debugging mittels einer Abstraktion einer Position in einer Quelldatei auch die IDE, z.  
  
 [Dokumenten\-Kontext](../../extensibility/debugger/document-context.md)  
 Erläutert, was Dokumentenkontext in Visual Studio\-Debugging in Bezug auf eine Quelldatei darstellt.  Erläutert außerdem, wie der Code einen Klassenhandler für den Kontext des Symbols Kontext Dokumentation.  
  
 [Ausdrucksauswertungs\-Kontext](../../extensibility/debugger/expression-evaluation-context.md)  
 Enthält Informationen zu einem Ausdrucksauswertungs Elementkontext in Visual Studio bereit.  Beispielsweise stellt ein Ausdrucksauswertungs Elementkontext, der mit einem Stapelrahmen zugeordnet ist, den Kontext für die Auswertung von lokalen Variablen, Methodenparameter und Klassenmember bereit.  
  
## Verwandte Abschnitte  
 [Debuggings\-Konzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die Architektur wichtigsten Konzepte des Debuggens.  
  
 [Debuggings\-Komponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die Visual Studio\-Debuggings Komponenten bereit, die das Debugmodul \(DE\), Ausdrucksauswertung \(Symbol\) und EE Klassenhandler \(SH\) enthalten.  
  
 [Debuggings\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu den verschiedenen Aufgaben Debuggen eines Programms starten, z und Auswerten von Ausdrücken.