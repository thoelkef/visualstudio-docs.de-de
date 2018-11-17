---
title: Debuggen von verwaltetem Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 801a4654b2297e3c19929063716339c7a4fcd50b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774418"
---
# <a name="debugging-managed-code"></a>Debuggen von verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt werden die häufigsten Probleme beim Debuggen sowie Verfahrensweisen für verwaltete Anwendungen bzw. Anwendungen erörtert, die in Sprachen für die Common Language Runtime geschrieben wurden, z. B. Visual Basic, C# und C++. Die in diesem Abschnitt behandelten Verfahren setzen Programmiererfahrung voraus. Weitere Informationen finden Sie unter [mithilfe des Debuggers](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Diagnosemeldungen im Ausgabefenster](../debugger/diagnostic-messages-in-the-output-window.md)  
 Beschreibt die <xref:System.Diagnostics.Debug> und <xref:System.Diagnostics.Trace> Klassen, mit dem können Sie laufzeitmeldungen zum Schreiben der **Ausgabe** Fenster. Die in diesen Klassen enthaltenen Ausgabemethoden ermöglichen die Datenausgabe, ohne die Ausführung zu unterbrechen, sowie die Datenausgabe mit Unterbrechung der Ausführung, wenn eine bestimmte Bedingung nicht erfüllt ist.  
  
 [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md)  
 Hier werden Assertionen in verwaltetem Code beschrieben. Diese testen Bedingungen, die Sie als Argumente für `Assert`-Methoden angeben. Sie finden in diesem Abschnitt außerdem Beispielcode, Informationen zum Verwenden der <xref:System.Diagnostics.Debug>-Klassenmethode und der <xref:System.Diagnostics.Trace>-Klassenmethode, zur Debug- und zur Releaseversion von Code, Nebeneffekten, Assert-Argumenten, dem Anpassen des Assert-Verhaltens und zu Konfigurationsdateien.  
  
 [Stop-Anweisungen in Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
 Hier wird die `Stop`-Anweisung beschrieben, die eine Alternative zum Festlegen eines Haltepunkts bietet. Sie finden hier außerdem Beispielcode sowie Vergleiche zwischen der `Stop`-Anweisung und der `End`-Anweisung sowie zwischen der `Stop`-Anweisung und der `Assert`-Anweisung.  
  
 [Exemplarische Vorgehensweise: Debuggen eines Windows Forms](../debugger/walkthrough-debugging-a-windows-form.md)  
 Hier finden Sie Schritt-für-Schritt-Anweisungen zum Erstellen eines Windows Forms und zum Debuggen dieses Formulars. Ein Windows Form, eine Standardkomponente verwalteter Windows-Anwendungen, ist eine der am häufigsten verwendeten verwalteten Anwendungen. In dieser exemplarischen Vorgehensweise werden Visual C# und Visual Basic verwendet, die Verfahrensweisen zum Erstellen eines Windows Forms mit C++ sind jedoch grundsätzlich vergleichbar.  
  
 [Debuggen der OnStart-Methode](../debugger/how-to-debug-the-onstart-method.md)  
 Dieser Abschnitt enthält Codebeispiele zum Debuggen der `OnStart`-Methode eines verwalteten Windows-Diensts. Um die `OnStart`-Methode eines Windows-Diensts zu debuggen, müssen Sie ein paar Codezeilen hinzufügen, mit denen der Dienst simuliert wird.  
  
 [Mixed-Mode Debugging](../debugger/debugging-mixed-mode-applications.md)  
 Erörtert das Debuggen von Anwendungen im gemischten Modus. Dies sind alle Anwendungen, die nativen Code mit verwaltetem Code kombinieren.  
  
 [Fehler: Das Debuggen ist nicht möglich, da ein Kerndebugger auf dem System aktiviert ist](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 Beschreibt eine Fehlermeldung angezeigt, das auftritt, wenn Sie versuchen, das Debuggen von verwalteten Codes auf eine [!INCLUDE[win7](../includes/win7-md.md)], [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)], [!INCLUDE[winxp](../includes/winxp-md.md)], [!INCLUDE[Win2kFamily](../includes/win2kfamily-md.md)], oder Windows NT-System, das im Debugmodus gestartet wurde.  
  
 [JIT-Optimierung und -Debuggen](../debugger/jit-optimization-and-debugging.md)  
 Beschreibt die Auswirkungen der JIT-Optimierung auf das Debuggen.  
  
 [Debuggen von LINQ und DLINQ](../debugger/debugging-linq.md)  
 Erörtert Verfahren zum Debuggen von LINQ-Abfragen.  
  
 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Beschreibt, wie die **Parallele Aufgaben** und **parallele Stapel** Toolfenster zum Debuggen einer parallelen Anwendung.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [IntelliTrace](../debugger/intellitrace.md)  
 Fehler werden einfacher und schneller gefunden, da der Ausführungsverlauf mit IntelliTrace aufgezeichnet wird. Sehen Sie sich die aufgezeichneten Ereignisse und Aufrufe sorgfältig an, um den Zustand der Anwendung zu wichtigen Zeitpunkt zu überprüfen. Debuggen Sie den Code, ohne viele Haltepunkte festzulegen oder Ihre Anwendung häufig neu zu starten. Erfordert Visual Studio Ultimate.  
  
 [Ablaufverfolgung und Instrumentieren von Anwendungen](http://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)  
 Hier werden die Ablaufverfolgung (eine Methode zum Überwachen der Ausführung einer Anwendung) und die Instrumentation (das Platzieren von Ablaufverfolgungsanweisungen an strategischen Stellen im Code) beschrieben. Die Links in diesem Abschnitt bringen Sie zu den folgenden Themen: Einführung in die Instrumentierung und die Ablaufverfolgung, Ablaufverfolgungsschalter, Ablaufverfolgungslistener, Ablaufverfolgung für Code in einer Anwendung, Hinzufügen von Ablaufverfolgungsanweisungen zu Anwendungscode und bedingte Kompilierung mit <xref:System.Diagnostics.Debug> und <xref:System.Diagnostics.Trace>.  
  
 [/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)  
 Beschreibt eine Linkeroption, die hinzufügt <xref:System.Diagnostics.DebuggableAttribute> mit C++ geschriebenem Code. Dieses Attribut wird für die Verwendung von Debugfunktionen, wie das Anhängen, mit C++ benötigt.  
  
 [Debuggen von Windows-Dienstanwendungen](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2)  
 Hier finden Sie Hinweise zum Debuggen von Windows-Dienstanwendungen, z. B. zum Einrichten, Anhängen an den Prozess, Debuggen des Codes in der `OnStart`-Methode des Diensts und in der Main-Methode, zum Festlegen von Haltepunkten sowie zum Verwenden des Dienststeuerungs-Managers zum Starten, Beenden, Anhalten und Fortsetzen eines Diensts.  
  
 [Debuggen und Profilerstellung](http://msdn.microsoft.com/library/4a04863e-2475-46f4-bc3f-3c11510c2a4b)  
 Hier werden das Debuggen von .NET Framework-Anwendungen sowie die Konfigurationsanforderungen beschrieben.  
  
 [Debuggen von Skript- und Webanwendungen](../debugger/debugging-web-applications-and-script.md)  
 Beschreibt allgemeine Probleme und Verfahren, die beim Debuggen von Skript- und Webanwendungen auftreten können.  
  
 [Neues im Debugger in Visual Studio 2015](../debugger/what’s-new-for-the-debugger-in-visual-studio-2015.md)  
 Hier finden Sie eine Beschreibung der neuen Debugfunktionen im aktuellen Release von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 [Debuggen-Homepage](../debugger/debugging-in-visual-studio.md)  
 Enthält Links zu den ausführlicheren Abschnitten der Debugdokumentation. Zu den behandelten Themen gehören neue Funktionen im Debugger, Einstellungen und Vorbereitung, Haltepunkte, Ausnahmebehandlung, die Funktion Bearbeiten und Fortfahren, Debuggen von verwaltetem Code, Debuggen von Visual C++-Projekten, Debuggen von COM und ActiveX, Debuggen von DLLs, Debuggen von SQL und Verweise auf die Benutzeroberfläche.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Debuggen von benutzerdefinierten Windows Forms-Steuerelementen zur Entwurfszeit](http://msdn.microsoft.com/library/1fd83ccd-3798-42fc-85a3-6cba99467387)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)



