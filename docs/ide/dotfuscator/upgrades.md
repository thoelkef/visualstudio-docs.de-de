---
title: Upgraden von Dotfuscator Community Edition (CE) | Microsoft-Dokumentation
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, Schutz, Community Edition, Obfuskation, .NET, kostenlos, Visual Studio 2017, upgraden, Befehlszeile
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
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
description: "Erfahren Sie, wie Sie die in Visual Studio 2017 enthaltene, kostenlose Dotfuscator Community Edition upgraden können."
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 60ca38639f6523cdbace4efa4aa48b48d5e9a886
ms.contentlocale: de-de
ms.lasthandoff: 06/23/2017

---

# Upgraden von Dotfuscator Community Edition (CE)
<a id="upgrade-dotfuscator-community-edition-ce" class="xliff"></a>

Die Dotfuscator Community Edition (Dotfuscator CE) bietet viele Funktionen für Anwendungsschutz und Härtung für alle Entwickler, die mit Microsoft Visual Studio arbeiten.
Für Benutzer, die Ihre Version von Dotfuscator upgraden, sind jedoch mehr Funktionen verfügbar.

## Registrieren von Dotfuscator CE
<a id="registering-dotfuscator-ce" class="xliff"></a>

Als registrierte Benutzer von Dotfuscator CE erhalten Sie Zugriff auf zusätzliche Funktionen wie z.B. [Befehlszeilenunterstützung][cli], sodass Sie Dotfuscator CE mühelos in den automatisierten Buildprozess integrieren können.

Die Registrierung ist schnell, einfach und kostenlos.
Informationen zum Registrieren von Dotfuscator CE finden Sie im [Abschnitt „Registering Dotfuscator CE“ (Registrieren von Dotfuscator CE) auf der Seite „Getting Started“ (Erste Schritte) des vollständigen Dotfuscator CE User Guide (Dotfuscator CE-Benutzerhandbuch)][register-ce].

## Dotfuscator Professional
<a id="dotfuscator-professional" class="xliff"></a>

Während die Dotfuscator Community Edition ein grundlegendes Schutzlevel bietet, enthält die **_PreEmptive Protection - Dotfuscator_ Professional Edition** erweiterte Obfuskationstransformationen und Schutzfunktionen.
Dazu gehören:

* *Schutz geistigen Eigentums*
  * Zusätzliche Umbenennungsoptionen einschließlich Enhanced Overload Induction™ sowie zufällige Auswahl von Bezeichnern.
  * Tools für die Decodierung verborgener Stapelüberwachungen.
  * Zugriff auf Obfuskationstransformationen auf Unternehmensebene einschließlich [Transformationen zur Vereitelung von automatisierter Code-Dekompilierung][control-flow].
  * Die Möglichkeit zum [Verbergen vertraulicher Zeichenfolgen][string-encryption], die eine einfache Suche im dekompilierten Code unmöglich macht.
  * Die Möglichkeit zur [diskreten Einbettung von Besitz und Verteilungszeichenfolgen in Ihre Assemblys][watermarking] (Softwarewasserzeichen), mit der Sie die Quelle unautorisierter Softwareleaks finden können.
  * Die Möglichkeit, [mehrere Assemblys in einer zu kombinieren][linking] und damit Angreifern das Bestimmen der Rollen von Codeelementen weiter zu erschweren, wurde als Trennung der Belange entfernt.
  * Die Möglichkeit, [nicht verwendeten Code automatisch aus der Anwendung zu entfernen][pruning] und so die Menge an vertraulichem Code, der implementiert wird, zu reduzieren.
* *Schutz der Anwendungsintegrität*
  * Zusätzliche [Abwehrverhalten der Anwendung][check-actions].
  * Die Möglichkeit, Anti-Tamper- und Anti-Debug-Code in `.dll`-Assemblys einzuschleusen.
  * Die Möglichkeit, einen Warnungszeitraum vor der End-of-Life-Deadline einer Anwendung anzugeben.
  * Die Möglichkeit, Anwendungscode während eines End-of-Life-Warnungszeitraums oder nach Ablauf der Deadline anzuzeigen.
  * Telemetrie-Verschlüsselung.
* *Anwendungsüberwachung*
  * Die Möglichkeit zum Sammeln und Speichern von Informationen während temporärer Netzwerkausfälle.
  * Die Möglichkeit zum Sammeln persönlich identifizierbarer Informationen.
  * Unbegrenzte Nutzung der [Funktionsnachverfolgung][features].
  * Die Möglichkeit, neben Ausnahmefehlern auch Ausnahmen nachzuverfolgen, die vom Code abgefangen und ausgelöst wurden.
  * Die Möglichkeit zum Nachverfolgen von Ausnahmen in `.dll`-Assemblys.
  * Telemetrie-Verschlüsselung.

Dotfuscator Professional ist der [.NET Obfuscator][net-obfuscator]-Industriestandard und eignet sich für Enterprise-Entwickler, die fortlaufende Unterstützung, Wartung und Produkt-Updates benötigen.
Darüber hinaus bietet Dotfuscator Professional eine engere Integration mit Visual Studio und ist für die gewerbliche Verwendung lizenziert.

Weitere Informationen zu den erweiterten Anwendungsschutzfunktionen von Dotfuscator Professional erhalten Sie auf der Seite [Dotfuscator Overview (Dotfuscator Übersicht)][product-about] von PreEmptive Solutions und im [Vergleich mit der Community Edition][product-compare].
[Vollständig unterstützte Testversionen sind auf Anfrage unter preemptive.com erhältlich][eval].

## Siehe auch
<a id="see-also" class="xliff"></a>

[Dieses Thema im vollständigen Dotfuscator CE-Benutzerhandbuch][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Check%20Actions.html
[features]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Feature_Usage_Tracking_and_the_Feature_Attribute.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html

