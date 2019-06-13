---
title: Funktionen von Dotfuscator
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: dotfuscator, dotfuscator community, dotfuscator ce, preemptive, preemptive solutions, preemptive protection, protection, community edition, obfuskation, .NET, kostenlos, visual studio 2017, visual studio 2019, visual studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Erfahren Sie mehr über die Funktionen der kostenlos in Visual Studio enthaltenen Kopie von Dotfuscator Community.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 87d093a540e3c6fae6a80761a5b945c572bd890d
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744779"
---
# <a name="capabilities-of-dotfuscator"></a>Funktionen von Dotfuscator

Diese Seite beschreibt die Funktionen von Dotfuscator Community und nimmt dabei Bezug auf einige erweiterte Optionen, die durch [Upgrades][upgrades] verfügbar sind.

Dotfuscator Community ist ein *Postbuildsystem* für .NET-Anwendungen.
Dotfuscator Community bietet Benutzern von Visual Studio die Möglichkeit, [Assemblys zu verschleiern][obfuscation] und [aktive Verteidigungsmaßnahmen][checks] in die Anwendung einzufügen – und das, ohne dass Dotfuscator auf den Originalquellcode zugreifen muss.
Dotfuscator schützt Ihre Anwendung auf verschiedene Arten und schafft so eine vielschichtige Schutzstrategie.

Dotfuscator Community unterstützt eine Vielfalt von .NET-Assemblys und Anwendungstypen, wie z.B. die [Universelle Windows-Plattform (UWP)][uwp] und [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Schutz geistigen Eigentums

Die Bauweise, das Verhalten und die Implementierung Ihrer Anwendung gehören zum geistigen Eigentum (intellectual property, IP).
Allerdings sind die Anwendungen für .NET erstellt wurden, im Grunde offene Bücher; Es ist einfach auf .NET-Assemblys rückzuentwickeln, [da sie hochrangige Metadaten und Zwischencode enthalten][assemblies].

Dotfuscator Community enthält eine grundlegende [.NET-Obfuskation ][obfuscation] in Form von [Umbenennung][renaming].
Das Verbergen Ihres Codes mit Dotfuscator senkt das Risiko des unautorisierten Zugriffs auf Quellcode durch Reverse Engineering, da wichtige Namensinformationen nicht mehr öffentlich sind.
Die Obfuskation zeigt außerdem Ihre Bemühungen, Ihren Code vor Durchsuchung zu schützen – ein wichtiger Schritt, um zu bekräftigen, dass Ihre IP rechtlich als Geschäftsgeheimnis geschützt ist.

Viele [Features zum Schutz der Anwendungsintegrität](#application-integrity-protection) von Dotfuscator Community tragen dazu bei, dass Reverse Engineering erschwert wird.
Es könnte z.B. sein, dass ein schädlicher Akteur versucht, einen Debugger an eine ausgeführte Instanz Ihrer Anwendung anzufügen, um die Logik des Programm zu verstehen.
Dotfuscator kann [Antidebugverhalten][debug] in Ihre Anwendung einfügen, um dies zu erschweren.

## <a name="application-integrity-protection"></a>Schutz der Anwendungsintegrität

Zusätzlich zum Schutz Ihres Quellcodes ist es außerdem wichtig, sicherzustellen, dass Ihre Anwendung für das verwendet wird, für das sie entworfen wurde.
Angreifer können versuchen, zu Kapern Ihrer Anwendung zu umgehen (d.h. Softwarepiraterie), zu stehlen oder manipulieren sensible Daten, die von der Anwendung behandelt oder das Verhalten der Anwendung zu ändern.

Dotfuscator Community kann [Anwendungsvalidierungscode][checks] in Ihre Assemblys einfügen, wie z. B. die Maßnahmen [Anti-Tamper][tamper], [Anti-Debug][debug] und [Schutz von Geräten ohne Rootzugriff][root].
Wenn ein ungültiger Anwendungszustand erkannt wird, kann der Validierungscode [Anwendungscode aufrufen, um angemessen auf die Situation zu reagieren][check-app].
Falls Sie lieber keinen Code für den ungültigen Gebrauch von Anwendungen schreiben möchten, kann Dotfuscator auch [Rückmeldungsverhalten][check-action] einfügen, ohne dass Ihr Quellcode modifiziert werden muss.

Viele der gleichen Methoden können auch verwendet werden, um [End-of-Life-Deadlines][shelflife] für Auswertungs- oder Testsoftware zu erzwingen.

## <a name="see-also"></a>Siehe auch

[Dieses Thema im vollständigen Dotfuscator Community-Benutzerhandbuch][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
