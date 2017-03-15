---
title: "Debuggen von verwaltetem Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen von ASP.NET-Webanwendungen, Verwalteter Code"
  - "Debuggen von verwaltetem Code"
  - "Verwalteter Code, Debuggen"
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen von verwaltetem Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt werden die häufigsten Probleme beim Debuggen sowie Verfahrensweisen für verwaltete Anwendungen bzw. Anwendungen erörtert, die in Sprachen für die Common Language Runtime geschrieben wurden, z. B. Visual Basic, C\# und C\+\+.  Die in diesem Abschnitt behandelten Verfahren setzen Programmiererfahrung voraus.  Weitere Informationen finden Sie unter [Verwenden des Debuggers](../debugger/debugger-basics.md).  
  
## In diesem Abschnitt  
 [Diagnosemeldungen im Ausgabefenster](../debugger/diagnostic-messages-in-the-output-window.md)  
 Erläutert die <xref:System.Diagnostics.Debug>\-Klasse und die <xref:System.Diagnostics.Trace>\-Klasse, mit denen Sie Laufzeitmeldungen ins **Ausgabefenster** schreiben können.  Die in diesen Klassen enthaltenen Ausgabemethoden ermöglichen die Datenausgabe, ohne die Ausführung zu unterbrechen, sowie die Datenausgabe mit Unterbrechung der Ausführung, wenn eine bestimmte Bedingung nicht erfüllt ist.  
  
 [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md)  
 Hier werden Assertionen in verwaltetem Code beschrieben. Diese testen Bedingungen, die Sie als Argumente für `Assert`\-Methoden angeben.  Sie finden in diesem Abschnitt außerdem Beispielcode, Informationen zum Verwenden der <xref:System.Diagnostics.Debug>\-Klassenmethode und der <xref:System.Diagnostics.Trace>\-Klassenmethode, zur Debug\- und zur Releaseversion von Code, Nebeneffekten, Assert\-Argumenten, dem Anpassen des Assert\-Verhaltens und zu Konfigurationsdateien.  
  
 [Stop\-Anweisungen in Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
 Hier wird die `Stop`\-Anweisung beschrieben, die eine Alternative zum Festlegen eines Haltepunkts bietet.  Sie finden hier außerdem Beispielcode sowie Vergleiche zwischen der `Stop`\-Anweisung und der `End`\-Anweisung sowie zwischen der `Stop`\-Anweisung und der `Assert`\-Anweisung.  
  
 [Exemplarische Vorgehensweise: Debuggen eines Windows Forms](../debugger/walkthrough-debugging-a-windows-form.md)  
 Hier finden Sie Schritt\-für\-Schritt\-Anweisungen zum Erstellen eines Windows Forms und zum Debuggen dieses Formulars.  Ein Windows Form, eine Standardkomponente verwalteter Windows\-Anwendungen, ist eine der am häufigsten verwendeten verwalteten Anwendungen.  In dieser exemplarischen Vorgehensweise werden Visual C\# und Visual Basic verwendet, die Verfahrensweisen zum Erstellen eines Windows Forms mit C\+\+ sind jedoch grundsätzlich vergleichbar.  
  
 [Debuggen der OnStart\-Methode](../debugger/how-to-debug-the-onstart-method.md)  
 Dieser Abschnitt enthält Codebeispiele zum Debuggen der `OnStart`\-Methode eines verwalteten Windows\-Diensts.  Um die `OnStart`\-Methode eines Windows\-Diensts zu debuggen, müssen Sie ein paar Codezeilen hinzufügen, mit denen der Dienst simuliert wird.  
  
 [Debuggen im gemischten Modus](../debugger/debugging-mixed-mode-applications.md)  
 Erörtert das Debuggen von Anwendungen im gemischten Modus.  Dies sind alle Anwendungen, die systemeigenen Code mit verwaltetem Code kombinieren.  
  
 [Fehler: Das Debuggen ist nicht möglich, da ein Kernel\-Debugger auf dem System aktiviert ist](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 In diesem Abschnitt wird eine Fehlermeldung beschrieben, die auftritt, wenn Sie versuchen, verwalteten Code auf einem [!INCLUDE[win7](../debugger/includes/win7_md.md)]\-, [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]\-, [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)]\-, [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)]\- oder Windows NT\-System zu debuggen, das im Debugmodus gestartet wurde.  
  
 [JIT\-Optimierung und \-Debuggen](../debugger/jit-optimization-and-debugging.md)  
 Beschreibt die Auswirkungen der JIT\-Optimierung auf das Debuggen.  
  
 [Debuggen von LINQ und DLINQ](../debugger/debugging-linq.md)  
 Erörtert Verfahren zum Debuggen von LINQ\-Abfragen.  
  
 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Beschreibt, wie die Toolfenster **Parallele Aufgaben** und **Parallele Stapel** zum Debuggen einer parallelen Anwendung verwendet werden.  
  
## Verwandte Abschnitte  
 [Verwenden von IntelliTrace](../debugger/intellitrace.md)  
 Fehler werden einfacher und schneller gefunden, da der Ausführungsverlauf mit IntelliTrace aufgezeichnet wird.  Sehen Sie sich die aufgezeichneten Ereignisse und Aufrufe sorgfältig an, um den Zustand der Anwendung zu wichtigen Zeitpunkt zu überprüfen.  Debuggen Sie den Code, ohne viele Haltepunkte festzulegen oder Ihre Anwendung häufig neu zu starten.  Erfordert Visual Studio Ultimate.  
  
 [Ablaufverfolgung und Instrumentieren von Anwendungen](../Topic/Tracing%20and%20Instrumenting%20Applications.md)  
 Hier werden die Ablaufverfolgung \(eine Methode zum Überwachen der Ausführung einer Anwendung\) und die Instrumentation \(das Platzieren von Ablaufverfolgungsanweisungen an strategischen Stellen im Code\) beschrieben.  Die Links in diesem Abschnitt bringen Sie zu den folgenden Themen: Einführung in die Instrumentation und die Ablaufverfolgung, Ablaufverfolgungsschalter, Ablaufverfolgungslistener, Ablaufverfolgung für Code in einer Anwendung, Hinzufügen von Ablaufverfolgungsanweisungen zu Anwendungscode und bedingte Kompilierung mit <xref:System.Diagnostics.Debug> und <xref:System.Diagnostics.Trace>.  
  
 [\/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)  
 Beschreibt eine Linkeroption, die <xref:System.Diagnostics.DebuggableAttribute> mit C\+\+ geschriebenem Code hinzufügt.  Dieses Attribut wird für die Verwendung von Debugfeatures, wie das Anhängen, mit C\+\+ benötigt.  
  
 [Debuggen von Windows\-Dienstanwendungen](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md)  
 Hier finden Sie Hinweise zum Debuggen von Windows\-Dienstanwendungen, z. B. zum Einrichten, Anhängen an den Prozess, Debuggen des Codes in der `OnStart`\-Methode des Diensts und in der Main\-Methode, zum Festlegen von Haltepunkten sowie zum Verwenden des Dienststeuerungs\-Managers zum Starten, Beenden, Anhalten und Fortsetzen eines Diensts.  
  
 [Debuggen und Profilerstellung](../Topic/Debugging,%20Tracing,%20and%20Profiling.md)  
 Hier werden das Debuggen von .NET Framework\-Anwendungen sowie die Konfigurationsvoraussetzungen beschrieben.  
  
 [Debuggen von Skript\- und Webanwendungen](../debugger/debugging-web-applications-and-script.md)  
 Beschreibt allgemeine Probleme und Verfahren, die beim Debuggen von Skript\- und Webanwendungen auftreten können.  
  
 [What’s New for the Debugger in Visual Studio 2015](../debugger/what’s-new-for-the-debugger-in-visual-studio-2015.md)  
 Hier finden Sie eine Beschreibung der neuen Debugfeatures im aktuellen Release von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Debuggen\-Homepage](../debugger/debugging-in-visual-studio.md)  
 Enthält Links zu den ausführlicheren Abschnitten der Debugdokumentation.  Zu den behandelten Themen gehören neue Funktionen im Debugger, Einstellungen und Vorbereitung, Haltepunkte, Ausnahmebehandlung, die Funktion Bearbeiten und Fortfahren, Debuggen von verwaltetem Code, Debuggen von Visual C\+\+\-Projekten, Debuggen von COM und ActiveX, Debuggen von DLLs, Debuggen von SQL und Verweise auf die Benutzeroberfläche.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Debuggen von benutzerdefinierten Windows Forms\-Steuerelementen zur Entwurfszeit](../Topic/Walkthrough:%20Debugging%20Custom%20Windows%20Forms%20Controls%20at%20Design%20Time.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)