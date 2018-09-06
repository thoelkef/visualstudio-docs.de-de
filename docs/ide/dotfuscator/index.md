---
title: Dotfuscator Community Edition (CE)
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
description: Erfahren Sie, wie Sie mit der kostenlosen Dotfuscator Community Edition, die in Visual Studio 2017 enthalten ist, Ihre .NET-Anwendungen schützen können.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: d3f061e095575e8692fc733e3f77f7c9b23e37c1
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775434"
---
# <a name="dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE)

*PreEmptive Protection – Dotfuscator* bietet umfassenden Schutz für .NET-Anwendungen, der problemlos in den sicheren Lebenszyklus der Softwareentwicklung passt.
Verwenden Sie die Lösung, um Desktop-, mobile, Server- und eingebettete Anwendungen zu härten, zu schützen und zu bereinigen. Dadurch können Sie Geschäftsgeheimnisse und sonstiges geistiges Eigentum sichern, Piraterie und Fälschungen reduzieren und Schutz vor Manipulationen und nicht autorisiertem Debuggen bieten.
Dotfuscator arbeitet in kompilierten Assemblys ohne zusätzliche Programmierung und sogar ohne Zugriff auf den Quellcode.

![PreEmptive Protection – Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>Warum der Schutz von Daten wichtig ist

Es ist wichtig, **Ihr geistiges Eigentum zu schützen**.
Der Code Ihrer Anwendung enthält Entwurfs- und Implementierungsdetails, die als geistiges Eigentum angesehen werden können.
Allerdings enthalten in .NET Framework erstellte Anwendungen [wichtige Metadaten und allgemeinen Zwischencode][assemblies], und dies erleichtert das Reverse Engineering mit einem von vielen kostenlosen, automatisierten Tools.
Indem Sie das Reverse Engineering behindern und unterbinden, können Sie die nicht autorisierte Veröffentlichung von geistigem Eigentum verhindern und zeigen, dass Ihr Code Geschäftsgeheimnisse enthält.
Dotfuscator kann Ihre .NET-Assemblys [verschleiern][obfuscation], um Reverse Engineering zu verhindern. Dabei wird das ursprüngliche Verhalten der Anwendung nicht beeinträchtigt.

Es ist auch wichtig, **die Integrität der Anwendung zu schützen**.
Zusätzlich zum Reverse Engineering könnten böswillige Benutzer versuchen, illegale Kopien der Anwendung zu erstellen, das Verhalten der Anwendung zur Laufzeit zu ändern oder Daten zu manipulieren.
Mit Dotfuscator können Sie Ihrer Anwendung um eine Funktionalität erweitern, mit der Sie [eine nicht autorisierte Nutzung erkennen und auf eine solche Nutzung reagieren können][checks], einschließlich Manipulationen, Drittanbieterdebugging und Geräten mit Rootzugriff.

Weitere Informationen zum Integrieren von Dotfuscator in einen sicheren Lebenszyklus der Softwareentwicklung finden Sie auf der PreEmptive Solutions-Seite zum [SDL-App-Schutz][sdl-protection].

## <a name="about-dotfuscator-ce"></a>Informationen zu Dotfuscator CE

Ihre Kopie von Microsoft Visual Studio 2017 beinhaltet eine kostenlose Kopie von **_PreEmptive Protection – Dotfuscator_ Community Edition**, auch bekannt als Dotfuscator CE.
Anweisungen zum Installieren der Version von Dotfuscator CE, die in Visual Studio 2017 enthalten ist, finden Sie auf der [Installationsseite][install].

Dotfuscator CE bietet für Entwickler, Architekten und Tester eine Reihe von Diensten für [Softwareschutz und -härtung][software-protection].
Beispiele von Dotfuscator CE-Funktionen für [.NET-Obfuskation][obfuscation] und sonstigen [Anwendungsschutz][app-protection]:

* *[Umbenennung][renaming]* von Bezeichnern, um das Reverse Engineering der kompilierten Assemblys zu erschweren.
* *[Manipulationsschutz][tamper]*, um die Ausführung manipulierter Anwendungen zu erkennen und manipulierte Sitzungen zu beenden oder in geeigneter Weise zu reagieren.
* *[Debugschutz][debug]*, um das Anfügen eines Debuggers an eine aktive Anwendung zu erkennen und Debugsitzungen zu beenden oder in geeigneter Weise zu reagieren.
* *[Schutz vor Geräten mit Rootzugriff][root]*, um zu ermitteln, ob die Anwendung auf einem Android-Gerät mit Rootzugriff ausgeführt wird, und um Sitzungen auf diesen Geräten zu beenden oder in geeigneter Weise zu reagieren.
* *[Verhaltensweisen beim Ablauf von Anwendungen][shelflife]*, mit denen ein Enddatum codiert wird und abgelaufene Anwendungssitzungen beendet werden.

Weitere Informationen zu diesen Funktionen und dazu, wie sie in die Strategie zum Schutz Ihrer Anwendungen passen, finden Sie auf der [Seite mit Funktionen][capabilities].

Dotfuscator CE bietet ohne zusätzliche Konfiguration grundlegenden Schutz.
Weitere Maßnahmen zum Schutz von Anwendungen stehen für registrierte Benutzer von Dotfuscator CE und für Benutzer von *PreEmptive Protection – Dotfuscator* Professional Edition, der weltweit führenden Lösung für [.NET-Obfuskation][net-obfuscator], zur Verfügung.
Informationen über das Erweitern von Dotfuscator finden Sie auf der [Upgradeseite][upgrades].

## <a name="getting-started"></a>Erste Schritte

Um mit der Nutzung von Dotfuscator CE in Visual Studio zu beginnen, geben Sie `dotfuscator` in der Suchleiste **Schnellstart** (STRG+Q) ein.

* Wenn Dotfuscator CE bereits installiert ist, wird über **Schnellstart** die Option *Menü* angezeigt, um die Benutzeroberfläche von Dotfuscator CE zu starten. Weitere Informationen finden Sie [auf der „Erste Schritte“-Seite des vollständigen Dotfuscator CE-Benutzerhandbuchs][get-started].
* Wenn Dotfuscator CE noch nicht installiert ist, wird durch den **Schnellstart** die relevante Option *Installieren* angezeigt. Details finden Sie auf der [Installationsseite][install].

Sie können auch die **neueste Version** von Dotfuscator CE von [der Seite mit Dotfuscator-Downloads auf „preemptive.com“ herunterladen][download].

## <a name="full-documentation"></a>Vollständige Dokumentation

Diese Seite und die dazugehörigen Unterseiten bieten einen allgemeinen Überblick über Dotfuscator CE-Features sowie [Anweisungen zur Installation des Tools][install].

Ausführliche Anweisungen zur Verwendung finden Sie im [vollständigen Dotfuscator CE-Benutzerhandbuch auf „preemptive.com“][full]. Dort finden Sie auch Informationen [zur Verwendung der Benutzeroberfläche von Dotfuscator CE][get-started].

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
