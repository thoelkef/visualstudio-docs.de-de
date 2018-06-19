---
title: Funktionen von Dotfuscator
ms.date: 10/10/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, Schutz, community edition, Obfuskation, .NET, kostenlos, Visual Studio 2017
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Erfahren Sie mehr über die Funktionen von Dotfuscator Community Edition, das in Visual Studio 2017 enthalten und kostenlos ist.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: a087af554ab62a77562dcdf449a18e807f9d17fe
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704446"
---
# <a name="capabilities-of-dotfuscator"></a>Funktionen von Dotfuscator

Diese Seite beschreibt die Funktionen von Dotfuscator Community Edition (Dotfuscator CE), und nimmt dabei Bezug auf einige erweiterte Optionen, die durch [Upgrades][upgrades] verfügbar sind.

Dotfuscator ist ein *Postbuild*system für .NET-Anwendungen.
Benutzer von Visual Studio haben durch Dotfuscator CE die Möglichkeit [Assemblys zu verbergen][obfuscation] und eine [aktive Verteidigung][checks] und eine [Analysenachverfolgung][analytics] in die Anwendung einzufügen – und das ohne dass Dotfuscator auf den Originalquellcode zugreifen muss.
Dotfuscator schützt Ihre Anwendung auf verschiedene Arten und schafft so eine vielschichtige Schutzstrategie.

Dotfuscator CE unterstützt eine Vielfalt von .NET-Assemblys und Anwendungstypen, wie z.B. die [Universelle Windows-Plattform (UWP)][uwp] und [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Schutz geistigen Eigentums

Die Bauweise, das Verhalten und die Implementierung Ihrer Anwendung gehören zum geistigen Eigentum (intellectual property, IP).
Dennoch sind Anwendungen, die für .NET Framework erstellt wurden, im Grunde offene Bücher – denn es ist sehr einfach, .NET-Assemblys rückzuentwickeln, [da sie hochrangige Metadaten und Zwischencode enthalten][assemblies].

Dotfuscator CE enthält grundlegende [.NET-Obfuskation ][obfuscation] in Form von [Umbenennung][renaming].
Das Verbergen Ihres Codes mit Dotfuscator senkt das Risiko des unautorisierten Zugriffs auf Quellcode durch Reverse Engineering, da wichtige Namensinformationen nicht mehr öffentlich sind.
Die Obfuskation zeigt außerdem Ihre Bemühungen, Ihren Code vor Durchsuchung zu schützen – ein wichtiger Schritt, um zu bekräftigen, dass Ihre IP rechtlich als Geschäftsgeheimnis geschützt ist.

Viele [Funktionen zum Schutz der Anwendungsintegrität](#application-integrity-protection) von Dotfuscator CE tragen dazu bei, dass Reverse Engineering erschwert wird.
Es könnte z.B. sein, dass ein schädlicher Akteur versucht, einen Debugger an eine ausgeführte Instanz Ihrer Anwendung anzufügen, um die Logik des Programm zu verstehen.
Dotfuscator kann [Antidebugverhalten][debug] in Ihre Anwendung einfügen, um dies zu erschweren.

## <a name="application-integrity-protection"></a>Schutz der Anwendungsintegrität

Zusätzlich zum Schutz Ihres Quellcodes ist es außerdem wichtig, sicherzustellen, dass Ihre Anwendung für das verwendet wird, für das sie entworfen wurde.
Angreifen können versuchen, die Kontrolle über Ihre Anwendung zu übernehmen, um Lizenzierungsrichtlinien zu umgehen (d.h. Softwarepiraterie), damit sie vertrauliche Daten, die von der Anwendung verarbeitet werden, stehlen oder manipulieren oder das Verhalten der Anwendung ändern können.

Dotfuscator CE kann [Anwendungsvalidierungscode][checks] in Ihre Assemblys einfügen, wie z.B. die Maßnahmen [Anti-Tamper][tamper], [Anti-Debug][debug] und [Schutz von Geräten ohne Rootzugriff][root].
Wenn ein ungültiger Anwendungszustand erkannt wird, kann der Validierungscode [Anwendungscode aufrufen, um angemessen auf die Situation zu reagieren][check-app].
Falls Sie lieber keinen Code für den ungültigen Gebrauch von Anwendungen schreiben möchten, kann Dotfuscator auch [Telemetriebericht][check-telemetry]- und [Rückmeldungs][check-action]verhalten einfügen, ohne dass Ihr Quellcode modifiziert werden muss.

Viele der gleichen Methoden können auch verwendet werden, um [End-of-Life-Deadlines][shelflife] für Auswertungs- oder Testsoftware zu erzwingen.

## <a name="application-monitoring"></a>Anwendungsüberwachung

Bei der Entwicklung einer Anwendung ist es wichtig, die Verhaltensmuster der Benutzer zu verstehen, wie z.B. Betatester und Benutzer von frühen Versionen.
Anwendungsanalysen geben Ihnen die Möglichkeit nachzuverfolgen, wie häufig und auf welche Art die Anwendung verwendet wird. Damit erfahren Sie z.B., auf welche Fehler die Benutzer stoßen.

Dotfuscator CE kann Code zur [Nachverfolgung von Ausnahmen][exceptions], zur [Nachverfolgung von Sitzungen][sessions] und zur [Nachverfolgung von Funktionen][features] in Ihre Anwendung einfügen.
Bei der Ausführung übermittelt die verarbeitete Anwendung Analysedaten an einen konfigurierten [PreEmptive Analytics-Endpunkt][endpoints].

## <a name="see-also"></a>Siehe auch

[Dieses Thema im vollständigen Dotfuscator CE-Benutzerhandbuch][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[analytics]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_overview.html
[endpoints]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_overview.html#endpoints

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html
[exceptions]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_exceptions.html
[sessions]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_sessions.html
[features]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_features.html
[check-telemetry]:  https://www.preemptive.com/dotfuscator/ce/docs/help/instrumentation_checks.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html