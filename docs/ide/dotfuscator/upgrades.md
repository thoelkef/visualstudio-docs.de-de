---
title: Upgraden von Dotfuscator Community Edition (CE)
ms.date: 02/08/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, Schutz, Community Edition, Obfuskation, .NET, kostenlos, Visual Studio 2017, upgraden, Befehlszeile
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Erfahren Sie, wie Sie die in Visual Studio 2017 enthaltene, kostenlose Dotfuscator Community Edition upgraden können.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 62a9273ef55a84c26714d2ad2ea1ebb7efe94319
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034141"
---
# <a name="upgrade-dotfuscator-community-edition-ce"></a>Upgraden von Dotfuscator Community Edition (CE)

Die Dotfuscator Community Edition (Dotfuscator CE) bietet viele Funktionen für Anwendungsschutz und Härtung für alle Entwickler, die mit Microsoft Visual Studio arbeiten.
Für Benutzer, die Ihre Version von Dotfuscator upgraden, sind jedoch mehr Funktionen verfügbar.

## <a name="registering-dotfuscator-ce"></a>Registrieren von Dotfuscator CE

Als registrierte Benutzer von Dotfuscator CE erhalten Sie Zugriff auf zusätzliche Features wie z.B. [Befehlszeilenunterstützung][cli], sodass Sie Dotfuscator CE mühelos in den automatisierten Buildprozess integrieren können. Darüber hinaus gewährt die Registrierung Zugriff auf Lucidator, ein integriertes Tool, das für die [Decodierung verborgener Stapelüberwachungen][decode-obfuscated] verwendet wird.

Die Registrierung ist schnell, einfach und kostenlos.
Informationen zum Registrieren von Dotfuscator CE finden Sie im [Abschnitt „Registering Dotfuscator CE“ (Registrieren von Dotfuscator CE) auf der Seite „Getting Started“ (Erste Schritte) des vollständigen Dotfuscator CE User Guide (Dotfuscator CE-Benutzerhandbuch)][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Während die Dotfuscator Community Edition ein grundlegendes Schutzlevel bietet, enthält die **_PreEmptive Protection - Dotfuscator_ Professional Edition** erweiterte Obfuskationstransformationen und Schutzfunktionen. Folgendes zählt zu den erweiterten Transformationen und Funktionen:

* *Schutz geistigen Eigentums*
  * Zusätzliche Umbenennungsoptionen einschließlich Enhanced Overload Induction™ sowie zufällige Auswahl von Bezeichnern.
  * Tools für die Decodierung verborgener Stapelüberwachungen.
  * Zugriff auf Obfuskationstransformationen auf Unternehmensebene einschließlich [Transformationen zur Vereitelung von automatisierter Code-Dekompilierung][control-flow].
  * Die Möglichkeit zum [Verbergen vertraulicher Zeichenfolgen][string-encryption], die eine einfache Suche im dekompilierten Code unmöglich macht.
  * Die Möglichkeit zur [diskreten Einbettung von Besitz und Verteilungszeichenfolgen in Ihre Assemblys][watermarking], mit der Sie die Quelle nicht autorisierter Softwareleaks finden können.
  * Die Möglichkeit, [mehrere Assemblys in einer zu kombinieren][linking] und damit Angreifern das Bestimmen der Rollen von Codeelementen weiter zu erschweren, wurde als Trennung der Belange entfernt.
  * Die Möglichkeit, [nicht verwendeten Code automatisch aus der Anwendung zu entfernen][pruning] und so die Menge an vertraulichem Code, der implementiert wird, zu reduzieren.
* *Schutz der Anwendungsintegrität*
  * Zusätzliche [Abwehrverhalten der Anwendung][check-actions].
  * Die Möglichkeit, einen Warnungszeitraum vor der End-of-Life-Deadline einer Anwendung anzugeben.
  * Die Möglichkeit, Anwendungscode während eines End-of-Life-Warnungszeitraums oder nach Ablauf der Deadline anzuzeigen.

Dotfuscator Professional ist der [.NET Obfuscator][net-obfuscator]-Industriestandard und eignet sich für Enterprise-Entwickler, die fortlaufende Unterstützung, Wartung und Produkt-Updates benötigen.
Darüber hinaus bietet Dotfuscator Professional eine engere Integration mit Visual Studio und ist für die gewerbliche Verwendung lizenziert.

Weitere Informationen zu den erweiterten Features von Dotfuscator Professional zum Anwendungsschutz erhalten Sie auf der Seite [Dotfuscator Overview (Übersicht über Dotfuscator)][product-about] von PreEmptive Solutions und im [Vergleich mit der Community Edition][product-compare].
[Vollständig unterstützte Testversionen sind unter preemptive.com erhältlich][eval].

## <a name="see-also"></a>Siehe auch

[Dieser Artikel im vollständigen Dotfuscator CE-Benutzerleitfaden][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html