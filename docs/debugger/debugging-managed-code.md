---
title: Debuggen von verwaltetem Code | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 14dc53413f646718b85ec9ea43d968dc9f64a96f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719314"
---
# <a name="debugging-managed-code"></a>Debuggen von verwaltetem Code

In diesem Abschnitt werden die häufigsten Probleme beim Debuggen sowie Verfahrensweisen für verwaltete Anwendungen bzw. Anwendungen erörtert, die in Sprachen für die Common Language Runtime geschrieben wurden, z. B. Visual Basic, C# und C++. Die in diesem Abschnitt behandelten Verfahren setzen Programmiererfahrung voraus. [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Diagnosemeldungen im Ausgabefenster](../debugger/diagnostic-messages-in-the-output-window.md) beschreibt die <xref:System.Diagnostics.Debug> und <xref:System.Diagnostics.Trace> Klassen, mit dem können Sie laufzeitmeldungen zum Schreiben der **Ausgabe** Fenster. Die in diesen Klassen enthaltenen Ausgabemethoden ermöglichen die Datenausgabe, ohne die Ausführung zu unterbrechen, sowie die Datenausgabe mit Unterbrechung der Ausführung, wenn eine bestimmte Bedingung nicht erfüllt ist.

[Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md) beschreibt Assertionen in verwaltetem Code, der Bedingungen zu testen, die Sie als Argumente für angeben `Assert` Methoden. Sie finden in diesem Abschnitt außerdem Beispielcode, Informationen zum Verwenden der <xref:System.Diagnostics.Debug>-Klassenmethode und der <xref:System.Diagnostics.Trace>-Klassenmethode, zur Debug- und zur Releaseversion von Code, Nebeneffekten, Assert-Argumenten, dem Anpassen des Assert-Verhaltens und zu Konfigurationsdateien.

[Stop-Anweisungen in Visual Basic](../debugger/stop-statements-in-visual-basic.md) beschreibt die `Stop` -Anweisung, die eine Alternative zum Festlegen eines Haltepunkts bietet. Sie finden hier außerdem Beispielcode sowie Vergleiche zwischen der `Stop`-Anweisung und der `End`-Anweisung sowie zwischen der `Stop`-Anweisung und der `Assert`-Anweisung.

[Exemplarische Vorgehensweise: Debuggen eines Windows-Formulars](../debugger/walkthrough-debugging-a-windows-form.md) bietet eine ausführliche Anleitung zum Erstellen eines Windows Forms und zum Debuggen dieses Formulars. Ein Windows Form, eine Standardkomponente verwalteter Windows-Anwendungen, ist eine der am häufigsten verwendeten verwalteten Anwendungen. In dieser exemplarischen Vorgehensweise werden Visual C# und Visual Basic verwendet, die Verfahrensweisen zum Erstellen eines Windows Forms mit C++ sind jedoch grundsätzlich vergleichbar.

[Debuggen der OnStart-Methode](../debugger/how-to-debug-the-onstart-method.md) enthält Codebeispiele zum Debuggen der `OnStart` Methode eines verwalteten Windows-Diensts. Um die `OnStart`-Methode eines Windows-Diensts zu debuggen, müssen Sie ein paar Codezeilen hinzufügen, mit denen der Dienst simuliert wird.

[Debuggen im gemischten Modus](../debugger/debugging-mixed-mode-applications.md) Debuggen im gemischten Modus Anwendungen erläutert. Dies sind alle Anwendungen, die nativen Code mit verwaltetem Code kombinieren.

[Fehler: Das Debuggen ist nicht möglich, da ein Kerneldebugger, auf dem System aktiviert ist](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md) beschreibt eine Fehlermeldung angezeigt, das auftritt, wenn Sie versuchen, das Debuggen von verwalteten Codes auf eine [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], oder Windows NT-System wurde im Debugmodus gestartet.

[JIT-Optimierung und Debugging](../debugger/jit-optimization-and-debugging.md) beschreibt die Auswirkungen der JIT-Optimierung über das Debuggen.

[Debuggen von LINQ und DLINQ](../debugger/debugging-linq.md) erörtert Verfahren zum Debuggen von LINQ-Abfragen.

[Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](../debugger/walkthrough-debugging-a-parallel-application.md) beschreibt, wie die **Parallele Aufgaben** und **parallele Stapel** Toolfenster zum Debuggen einer parallelen Anwendung.

## <a name="related-sections"></a>Verwandte Abschnitte

[IntelliTrace](../debugger/intellitrace.md) finden Sie Fehler schneller und einfacher, indem Sie die Aufzeichnung des Ausführungsverlaufs für Ihre app mit IntelliTrace. Sehen Sie sich die aufgezeichneten Ereignisse und Aufrufe sorgfältig an, um den Zustand der Anwendung zu wichtigen Zeitpunkt zu überprüfen. Debuggen Sie den Code, ohne viele Haltepunkte festzulegen oder Ihre Anwendung häufig neu zu starten. Ist Visual Studio Enterprise erforderlich.

[Ablaufverfolgung und Instrumentieren von Anwendungen](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) beschrieben, die Ablaufverfolgung, einer Möglichkeit zum Überwachen der Ausführung der Anwendung, während es ausgeführt wird, und Instrumentierung, hierbei ist das Platzieren von ablaufverfolgungsanweisungen an strategischen Stellen im Code. Die Links in diesem Abschnitt bringen Sie zu den folgenden Themen: Einführung in die Instrumentation und die Ablaufverfolgung, Ablaufverfolgungsschalter, Ablaufverfolgungslistener, Ablaufverfolgung für Code in einer Anwendung, Hinzufügen von Ablaufverfolgungsanweisungen zu Anwendungscode und bedingte Kompilierung mit <xref:System.Diagnostics.Debug> und <xref:System.Diagnostics.Trace>.

[/ ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) beschreibt eine Linkeroption, die hinzufügt <xref:System.Diagnostics.DebuggableAttribute> mit C++ geschriebenem Code. Dieses Attribut wird für die Verwendung von Debugfeatures, wie das Anhängen, mit C++ benötigt.

[Debuggen von Windows-Dienstanwendungen](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) enthält Überlegungen zum Debuggen von Windows-dienstanwendungen, z. B. zum Einrichten, Anhängen an den Prozess, Debuggen von Code in des Diensts `OnStart` -Methode und den Code auf dem Hauptblatt Methode, Festlegen von Haltepunkten und mithilfe des Dienststeuerungs-Managers zum Starten, beenden, Anhalten und Fortsetzen eines Diensts.

[Debuggen und Profilerstellung](/dotnet/framework/debug-trace-profile/index) wird erläutert, Debuggen von .NET Framework-Anwendungen sowie die konfigurationsanforderungen.

[Debuggen von Skript- und Webanwendungen](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications) beschreibt allgemeine Probleme und Verfahren, die möglicherweise beim Debuggen von Skript- und Webanwendungen-Debuggen.

[Neues im Debugger in Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md) Beschreibung der neuen Debugfunktionen in dieser Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Debuggen-Homepage](../debugger/debugger-feature-tour.md) enthält Links zu den ausführlicheren Abschnitten der Debugdokumentation. Zu den behandelten Themen gehören neue Funktionen im Debugger, Einstellungen und Vorbereitung, Haltepunkte, Ausnahmebehandlung, die Funktion Bearbeiten und Fortfahren, Debuggen von verwaltetem Code, Debuggen von Visual C++-Projekten, Debuggen von COM und ActiveX, Debuggen von DLLs, Debuggen von SQL und Verweise auf die Benutzeroberfläche.

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Debuggen von benutzerdefinierten Windows Forms-Steuerelementen zur Entwurfszeit](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[Debuggersicherheit](../debugger/debugger-security.md)
[Debuggen in Visual Studio](../debugger/index.md) 
 [ Ein erster Blick auf den debugger](../debugger/debugger-feature-tour.md)