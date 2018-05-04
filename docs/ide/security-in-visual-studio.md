---
title: Sicherheit in Visual Studio
ms.date: 02/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74e557fd0e92742f33c25d68862ae15254104963
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="security-in-visual-studio"></a>Sicherheit in Visual Studio

Sicherheitsüberlegungen sollten vom Entwurf bis zur Bereitstellung in alle Aspekte der Anwendungsentwicklung einfließen. Beginnen Sie damit, Visual Studio so sicher wie möglich auszuführen. Weitere Informationen finden Sie unter [Benutzerberechtigungen](../ide/user-permissions-and-visual-studio.md).

 Damit Sie sichere Anwendungen effektiv entwickeln können, benötigen Sie grundlegende Kenntnisse über die Sicherheitskonzepte und Sicherheitsfunktionen der Plattformen, für die Anwendungen entwickelt werden. Außerdem sollten Kenntnisse im Bereich sicherer Codierungstechniken vorhanden sein.

## <a name="understand-security"></a>Grundlagen zur Sicherheit
 [Sicherheit:](/dotnet/standard/security/index) Beschreibt Codezugriffssicherheit, rollenbasierte Sicherheit, Sicherheitsrichtlinien und Sicherheitstools in .NET Framework.

 [Defend Your Code with Top Ten Security Tips Every Developer Must Know (Die zehn wichtigsten Tipps zum Schützen des Codes, die jeder Entwickler kennen sollte):](http://go.microsoft.com/fwlink/?LinkId=72877) Beschreibt Probleme, auf die Sie achten sollten, um Ihre Daten oder Ihr System nicht zu gefährden.

## <a name="code-for-security"></a>Codieren im Hinblick auf Sicherheit
 Die meisten Codierungsfehler, die Sicherheitsmängel verursachen, entstehen, weil Entwickler bei Benutzereingaben von falschen Voraussetzungen ausgehen oder nicht vollständig mit der Plattform vertraut sind, für welche die Anwendung entwickelt wird.

 [Richtlinien für das Schreiben von sicherem Code:](/dotnet/standard/security/secure-coding-guidelines) Stellt Richtlinien zum Klassifizieren der Komponenten bereit, um Sicherheitsprobleme zu beheben.

 [Empfohlene Vorgehensweisen bezüglich der Sicherheit:](/cpp/top/security-best-practices-for-cpp) Behandelt Pufferüberläufe und beschreibt ausführlich das über das Kompilierzeitflag /GS bereitgestellte Feature für Sicherheitsüberprüfungen von Microsoft Visual C++.

## <a name="build-for-security"></a>Erstellen im Hinblick auf Sicherheit
 Die Sicherheit ist im Buildprozess auch ein wichtiger Aspekt.  Einige zusätzliche Schritte können die Sicherheit einer bereitgestellten App verbessern und nicht autorisiertes Reverse Engineering, Spoofing oder andere Angriffe verhindern.

 [Dotfuscator Community Edition (CE):](dotfuscator/index.md) Erläutert das Einrichten und Starten mithilfe des kostenlosen Programms „PreEmptive Protection – Dotfuscator Community Edition“ zum Schutz von .NET-Assemblys vor Reverse Engineering und nicht autorisierter Nutzung (z.B. nicht autorisiertes Debuggen).

 [Verwalten der Signierung von Assemblys und Manifesten:](managing-assembly-and-manifest-signing.md) Beschreibt das Signieren mit starken Namen, das zum eindeutigen Identifizieren von Softwarekomponenten verwendet werden kann und das Spoofing von Namen verhindert.