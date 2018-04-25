---
title: Gewährleisten der Anwendungssicherheit in Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unauthorized access
- Baseline Security Analyzer
- Microsoft Baseline Security Analyzer
- security [.NET Framework], best practices
- MBSA (Microsoft Baseline Security Analyzer)
- security [.NET Framework], maintaining after deployment
ms.assetid: 621d10c1-842b-4902-be60-bb9719591751
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fb75bfe3c9e479e67c766137ee84e919f9a6710
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="maintaining-security"></a>Gewährleisten der Sicherheit

Es wird oft betont, dass der Preis für die Sicherheit die ständige Wachsamkeit ist. Auch wenn Sie beim Entwerfen und Entwickeln der Anwendung größten Wert auf Sicherheit gelegt haben, ist davon auszugehen, dass nach der Bereitstellung Sicherheitsfehler auftreten. Durch das Überwachen der Anwendung und Analysieren von Ereignisprotokollen werden möglicherweise einige zuvor nicht feststellbare Fehler erkennbar.

Außerdem ist nicht nur die eigene Anwendung zu überwachen. Sie müssen auch ständig über die aktuellen Sicherheitsrisiken und Fehler der Plattform, auf der die Anwendung ausgeführt wird, und anderer Produkte, von denen die Anwendung abhängt, informiert sein.

[Sicherheit, Datenschutz und Konten](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;Hier erhalten Sie hilfreiche Informationen zu Sicherheit, Datenschutz und Benutzerkonten sowie über Viren, Kennwörter, Jugendschutz, Firewalls und zur Laufwerkverschlüsselung.

[Bulletins zu Microsoft-Sicherheitsupdates](https://technet.microsoft.com/security/bulletins.aspx)&mdash;Diese Seite vereinfacht die Suche nach bereits veröffentlichten Bulletins. Die für IT-Experten erstellten Sicherheitsbulletins enthalten detaillierte Informationen über Sicherheitsupdates.

[Microsoft Baseline Security Analyzer](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;Der Baseline Security Analyzer (MBSA) von Microsoft ist ein Tool sowohl für Heimanwender und Benutzer in Unternehmen als auch für Administratoren, mit dem ein oder mehrere Windows-basierte Computer nach Konfigurationsfehlern im Bereich der Sicherheitseinstellungen durchsucht werden können.