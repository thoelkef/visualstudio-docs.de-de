---
title: 'Visual Studio-Dokumentation: Neues im August 2020 '
titleSuffix: ''
description: Neues in der Visual Studio-Dokumentation für August 2020.
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 4364bd62ac19be958632b8cb2dbbe907013e8a70
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402243"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Visual Studio-Dokumentation: Neues im August 2020

Willkommen bei den Neuerungen in der Visual Studio-Dokumentation für August 2020. Nachfolgend sind alle größeren Änderungen aufgelistet, die in diesem Zeitraum an der Dokumentation vorgenommen wurden. Informationen zu den Neuerungen in den vorherigen Monaten finden Sie im [Verlauf der Neuerungen](whats-new-visual-studio-docs-history.md).

## <a name="azure"></a>Azure

**Neue Artikel**

- [Hinzufügen von Azure Application Insights über verbundene Visual Studio-Dienste](/visualstudio/azure/azure-app-insights-add-connected-service): verbundene Dienste für VS 2019 16.7
- [Hinzufügen von Azure Cache for Redis über verbundene Visual Studio-Dienste](/visualstudio/azure/azure-cache-for-redis-add-connected-service): verbundene Dienste für VS 2019 16.7
- [Hinzufügen von Azure Cosmos DB zu Ihrer App über verbundene Visual Studio-Dienste](/visualstudio/azure/azure-cosmosdb-add-connected-service): verbundene Dienste für VS 2019 16.7
- [Hinzufügen von Azure SignalR über verbundene Visual Studio-Dienste](/visualstudio/azure/azure-signalr-add-connected-service): verbundene Dienste für VS 2019 16.7
- [Hinzufügen einer Verbindung mit Azure SQL-Datenbank](/visualstudio/azure/azure-sql-database-add-connected-service): verbundene Dienste für VS 2019 16.7

**Aktualisierte Artikel**

- [Hinzufügen von Azure-Speicher mithilfe von verbundenen Visual Studio-Diensten](/visualstudio/azure/vs-azure-tools-connected-services-storage)
  - Verbundene Dienste für VS 2019 16.7
  - Artikel zu verbundenen Azure Storage-Diensten: Benutzeroberfläche und unterstützte Projekttypen aktualisiert

## <a name="code-quality"></a>Codequalität

**Neue Artikel**

- [CA1310: StringComparison für Richtigkeit angeben](/visualstudio/code-quality/ca1310): Dokumentation für CA1310 hinzugefügt und Dokumentation für CA1307 aktualisiert
- [CA1837: Verwenden von Environment.ProcessId anstelle von Process.GetCurrentProcess().Id](/visualstudio/code-quality/ca1837): Dokumentation für CA1837
- [CA1838: `StringBuilder`-Parameter für P/Invokes](/visualstudio/code-quality/ca1838) vermeiden: Dokumentation für CA1838 hinzugefügt
- [CA2008: Keine Tasks ohne Übergabe eines TaskSchedulers erstellen](/visualstudio/code-quality/ca2008): Dokumentation für CA2008 hinzugefügt
- [CA2249: Verwendung von String.Contains anstelle von String.IndexOf erwägen](/visualstudio/code-quality/ca2249): Dokumentation für CA2249
- [CA2361: Sicherstellen, dass die automatisch generierte Klasse mit DataSet.ReadXml() nicht mit nicht vertrauenswürdigen Daten verwendet wird](/visualstudio/code-quality/ca2361): weitere DataSet/DataTable-Regeln
- [CA2362: Unsichere DataSet- oder DataTable-Elemente in automatisch generiertem serialisierbarem Typ können für Angriffe durch Remotecodeausführung anfällig sein](/visualstudio/code-quality/ca2362): weitere DataSet/DataTable-Regeln
- [IL3000: Vermeiden des Zugriffs auf den Assemblydateipfad beim Veröffentlichen als Einzeldatei](/visualstudio/code-quality/il3000): Dokumentation für IL3000 hinzugefügt
- [IL3001: Vermeiden des Zugriffs auf den Assemblydateipfad beim Veröffentlichen als Einzeldatei](/visualstudio/code-quality/il3001): Dokumentation für IL3001 hinzugefügt

**Aktualisiert**

- [CA1002: Generische Listen nicht verfügbar machen](/visualstudio/code-quality/ca1002): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA1046: Operatorgleichheit bei Verweistypen nicht überladen](/visualstudio/code-quality/ca1046): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA1307: StringComparison zur Klarheit angeben](/visualstudio/code-quality/ca1307): Dokumentation für CA1310 hinzugefügt und Dokumentation für CA1307 aktualisiert
- [CA1700: &#39;Reserved&#39;-Enumerationswerte nicht benennen](/visualstudio/code-quality/ca1700): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA1707: Bezeichner dürfen keine Unterstriche enthalten](/visualstudio/code-quality/ca1707): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA1822: Member als statisch markieren](/visualstudio/code-quality/ca1822): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA2351: Sicherstellen, dass die Eingabe von DataSet.ReadXml() vertrauenswürdig ist](/visualstudio/code-quality/ca2351): weitere DataSet/DataTable-Regeln
- [Analysetools von Drittanbietern installieren](/visualstudio/code-quality/install-roslyn-analyzers): Struktur und Titel für die Dokumentation der Codeanalyse geändert

## <a name="containers"></a>Container

**Aktualisierte Artikel**

- [Bereitstellen eines ASP.NET-Containers für eine Containerregistrierung mithilfe von Visual Studio](/visualstudio/containers/hosting-web-apps-in-docker): Updates der Containertools für die Veröffentlichungsoberfläche von Visual Studio 16.7
- [Erste Schritte mit Kubernetes-Tools in Visual Studio](/visualstudio/containers/tutorial-kubernetes-tools): Kubernetes-Tutorial: Schritte für die Entfernung hinzugefügt

## <a name="deployment"></a>Bereitstellung

**Neue Artikel**

- [Projekterweiterung für Visual Studio-Installer und .NET Core 3.1](/visualstudio/deployment/installer-projects-net-core): Erstellen einer neuen Hilfeseite für .NET Core 3.1-Features für Installer-Projekte

**Aktualisierte Artikel**

- [Bereitstellen Ihrer App in einem Ordner, in IIS, in Azure oder einem anderen Ziel](/visualstudio/deployment/deploying-applications-services-and-components-resources): Aktualisierungen der Bereitstellung
- [Bereitstellung in Visual Studio](/visualstudio/deployment/index): Aktualisierungen der Bereitstellung

## <a name="extensibility"></a>Erweiterungen

**Aktualisierte Artikel**
- [Projektuntertypen](/visualstudio/extensibility/internals/project-subtypes): Einzug für Listenelemente korrigiert
- [Farbwertreferenz für Visual Studio](/visualstudio/extensibility/ux-guidelines/color-value-reference-for-visual-studio): AB#1759333 – fehlende Spaltenüberschriften korrigiert

## <a name="get-started"></a>Erste Schritte

**Aktualisierte Artikel**

- [Schritt 5: Bereitstellen Ihrer ASP.NET Core-App in Azure](/visualstudio/get-started/csharp/tutorial-aspnet-core-ef-step-05): Videotutorial zur neuen Benutzeroberfläche für verbundene Dienste aktualisiert

## <a name="ide"></a>IDE

**Neue Artikel**

- [Ändern der F1-Hilfetaste in Visual Studio](/visualstudio/ide/not-in-toc/change-f1-help-key): standardmäßige F1-Hilfeseite umgestaltet
- [F1-Hilfe für den Text-Editor](/visualstudio/ide/not-in-toc/default-f1-text-editor): standardmäßige F1-Hilfeseite umgestaltet
- [`typeof` in `nameof` konvertieren](/visualstudio/ide/reference/convert-typeof-to-nameof): Konvertierung von „typeof“ zu „nameof“ umgestaltet
- [Vereinfachen von LINQ-Ausdrücken](/visualstudio/ide/reference/simplify-linq-expression): Umgestaltung von LINQ-Ausdrücken vereinfacht

**Aktualisierte Artikel**

- [Anpassen von Fensterlayouts in Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio): Infomoniker für vertikale Dokumentregisterkarten zum Thema „Anpassen von Fensterlayouts“ hinzugefügt
- [Melden eines Problems mit Visual Studio oder Visual Studio-Installer](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
  - Weitere Informationen zu NMI hinzugefügt
  - Gesamte Seite zu „Melden eines Problems“ neu erstellt
- [F1-Hilfe](/visualstudio/ide/not-in-toc/default): standardmäßige F1-Hilfeseite umgestaltet
- [Dialogfelder für automatisches Wiederherstellen, Umgebung und Optionen](/visualstudio/ide/reference/autorecover-environment-options-dialog-box): Informationen zu aktualisierten Dateispeicherorten für die automatische Speicherung hinzugefügt
- [Optionen, Text-Editor, Basic (Visual Basic), Erweitert](/visualstudio/ide/reference/options-text-editor-basic-visual-basic): grundlegende Dokumentation zu Namenshinweisen für Inlineparameter hinzugefügt
- [Optionen, Text-Editor, C#, Erweitert](/visualstudio/ide/reference/options-text-editor-csharp-advanced): grundlegende Dokumentation zu Namenshinweisen für Inlineparameter hinzugefügt
- [Tipps und Tricks zur Leistung von Visual Studio](/visualstudio/ide/visual-studio-performance-tips-and-tricks): Informationen zum Deaktivieren des Zuordnungsmodus und zum Deaktivieren des Zeilenumbruchs hinzugefügt
- [Neues in Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019): Abschnitt „Neues in Visual Studio 2019“ mit Informationen zur allgemeinen Verfügbarkeit von Version 16.7 aktualisiert

## <a name="rtvs"></a>RTVS

**Aktualisierte Artikel**

- [Arbeiten mit SQL Server und R](/visualstudio/rtvs/integrating-sql-server-with-r): Tabellen korrigiert, sodass diese jetzt Spaltenüberschriften enthalten

## <a name="community-contributors"></a>Mitwirkende in der Community

Die folgenden Personen haben während dieses Zeitraums zu den Visual Studio-Dokumenten beigetragen. Vielen Dank! In [Leitfaden für Mitwirkende an der Microsoft-Dokumentation: Übersicht](https://docs.microsoft.com/contribute/) erfahren Sie, wie Sie an den Visual Studio-Dokumenten mitwirken können.

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) – Alex Black (11)
- [Youssef1313](https://github.com/Youssef1313) – Youssef Victor (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) – Hiroshi Yoshioka (3)
- [AstroChoco](https://github.com/AstroChoco) – Qian Lu (Chocolate) (1)
- [athyunnath](https://github.com/athyunnath) – Athyunnath Eleti (1)
- [caro-oviedo](https://github.com/caro-oviedo) – Caro Oviedo  (1)
- [Evangelink](https://github.com/Evangelink) – Amaury Levé (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones) – Shafiq Jetha (1)
- [nebuk89](https://github.com/nebuk89) – Ben De St Paer-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) – Petr Kulikov (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) – Timo Cornelius Metzger (1)
- [weitzhandler](https://github.com/weitzhandler) – Shimmy (1)