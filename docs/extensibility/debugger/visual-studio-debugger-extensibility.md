---
title: "Visual Studio-Debugger-Erweiterbarkeit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Debugging-SDK"
  - "Debuggen-SDK"
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Visual Studio-Debugger-Erweiterbarkeit
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio enthält einen vollständig interaktive Source Code\-Debugger, ein leistungsfähiges und leicht zu verwendendes Tool für das Aufspüren von Fehlern in Ihrer Anwendung bereitstellen. Der Debugger hat vollständige Unterstützung von Visual Basic, c\#, C\/C\+\+ und JavaScript. Bei der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], d. h. verfügbar der [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453),, anderen Programmiersprachen können in den Debugger mit den gleichen umfassenden Features unterstützt werden.  
  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger ist die debugging\-Komponenten, die, von der Sprache, die gedebuggt wird wiederum sind, allgemeine Front\-End \(d. h. der Benutzeroberfläche\). Für neue Sprachen unterstützen erforderlich ist, indem die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \-Debugger ist, um die erforderlichen Back\-End\-Komponenten, wie z. B. ein Debugmodul \(DE\) zu erstellen. Sind die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ins Spiel.  
  
 Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] umfasst eine vollständige Referenz für alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Elemente erforderlich, um einen neuen Befehl zu erstellen. Außerdem sind Beispiele und Lernprogramme, die erleichtern Ihnen den Einstieg erleichtern.  
  
 Ein End\-to\-End\-Beispiel von einer Sprache Projektsystem mit debugging\-Unterstützung finden Sie unter der [IronPython sample](http://msdn.microsoft.com/de-de/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 In den folgenden Abschnitten wird beschrieben, wie mithilfe des Debuggers erweitert die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## In diesem Abschnitt  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Beschreibt, was [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen Angebote und das SDK installieren.  
  
 [Erstellen einer benutzerdefinierten Debugmodul](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Dokumentiert die benutzerdefinierten DE\-Prozess von der Vorbereitung Ihrer Anwendung für eine DE zum Trennen der DE.  
  
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Erläutert, ob Sie eine Ausdrucksauswerter schreiben müssen.  
  
 [Auswählen einer Strategie für das Debug\-Modul\-Implementierung](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Erläutert, wie Ihre DE implementieren.  
  
 [Verweis](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Dokumente der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Debug\-API.  
  
 [Proben](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Enthält Links zu einer common Language Runtime Ausdruck Beispiel und ein Beispiel für die Debug\-Modul.