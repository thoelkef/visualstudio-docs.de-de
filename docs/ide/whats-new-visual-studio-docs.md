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
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808980"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Visual Studio-Dokumentation: Neues im August 2020

Willkommen bei den Neuerungen in der Visual Studio-Dokumentation für August 2020. Nachfolgend sind alle größeren Änderungen aufgelistet, die in diesem Zeitraum an der Dokumentation vorgenommen wurden. Informationen zu den Neuerungen in den vorherigen Monaten finden Sie im [Verlauf der Neuerungen](whats-new-visual-studio-docs-history.md).

## <a name="azure"></a>Azure

**Neue Artikel**

- [Hinzufügen von Azure Application Insights über verbundene Visual Studio-Dienste](../azure/azure-app-insights-add-connected-service.md): verbundene Dienste für VS 2019 16.7
- [Hinzufügen von Azure Cache for Redis über verbundene Visual Studio-Dienste](../azure/azure-cache-for-redis-add-connected-service.md): verbundene Dienste für VS 2019 16.7
- [Hinzufügen von Azure Cosmos DB zu Ihrer App über verbundene Visual Studio-Dienste](../azure/azure-cosmosdb-add-connected-service.md): verbundene Dienste für VS 2019 16.7
- [Hinzufügen von Azure SignalR über verbundene Visual Studio-Dienste](../azure/azure-signalr-add-connected-service.md): verbundene Dienste für VS 2019 16.7
- [Hinzufügen einer Verbindung mit Azure SQL-Datenbank](../azure/azure-sql-database-add-connected-service.md): verbundene Dienste für VS 2019 16.7

**Aktualisierte Artikel**

- [Hinzufügen von Azure-Speicher mithilfe von verbundenen Visual Studio-Diensten](../azure/vs-azure-tools-connected-services-storage.md)
  - Verbundene Dienste für VS 2019 16.7
  - Artikel zu verbundenen Azure Storage-Diensten: Benutzeroberfläche und unterstützte Projekttypen aktualisiert

## <a name="code-quality"></a>Codequalität

**Neue Artikel**

- [CA1310: StringComparison für Richtigkeit angeben](../code-quality/ca1310.md): Dokumentation für CA1310 hinzugefügt und Dokumentation für CA1307 aktualisiert
- [CA1837: Verwenden von Environment.ProcessId anstelle von Process.GetCurrentProcess().Id](../code-quality/ca1837.md): Dokumentation für CA1837
- [CA1838: `StringBuilder`-Parameter für P/Invokes](../code-quality/ca1838.md) vermeiden: Dokumentation für CA1838 hinzugefügt
- [CA2008: Keine Tasks ohne Übergabe eines TaskSchedulers erstellen](../code-quality/ca2008.md): Dokumentation für CA2008 hinzugefügt
- [CA2249: Verwendung von String.Contains anstelle von String.IndexOf erwägen](../code-quality/ca2249.md): Dokumentation für CA2249
- [CA2361: Sicherstellen, dass die automatisch generierte Klasse mit DataSet.ReadXml() nicht mit nicht vertrauenswürdigen Daten verwendet wird](../code-quality/ca2361.md): weitere DataSet/DataTable-Regeln
- [CA2362: Unsichere DataSet- oder DataTable-Elemente in automatisch generiertem serialisierbarem Typ können für Angriffe durch Remotecodeausführung anfällig sein](../code-quality/ca2362.md): weitere DataSet/DataTable-Regeln
- [IL3000: Vermeiden des Zugriffs auf den Assemblydateipfad beim Veröffentlichen als Einzeldatei](../code-quality/il3000.md): Dokumentation für IL3000 hinzugefügt
- [IL3001: Vermeiden des Zugriffs auf den Assemblydateipfad beim Veröffentlichen als Einzeldatei](../code-quality/il3001.md): Dokumentation für IL3001 hinzugefügt

**Aktualisiert**

- [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002.md): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA1046: Operatorgleichheit bei Verweistypen nicht überladen](../code-quality/ca1046.md): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA1307: StringComparison zur Klarheit angeben](../code-quality/ca1307.md): Dokumentation für CA1310 hinzugefügt und Dokumentation für CA1307 aktualisiert
- [CA1700: &#39;Reserved&#39;-Enumerationswerte nicht benennen](../code-quality/ca1700.md): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA1707: Bezeichner dürfen keine Unterstriche enthalten](../code-quality/ca1707.md): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA1822: Member als statisch markieren](../code-quality/ca1822.md): Abschnitt zur Konfigurierbarkeit/API-Oberfläche hinzugefügt
- [CA2351: Sicherstellen, dass die Eingabe von DataSet.ReadXml() vertrauenswürdig ist](../code-quality/ca2351.md): weitere DataSet/DataTable-Regeln
- [Analysetools von Drittanbietern installieren](../code-quality/install-roslyn-analyzers.md): Struktur und Titel für die Dokumentation der Codeanalyse geändert

## <a name="containers"></a>Container

**Aktualisierte Artikel**

- [Bereitstellen eines ASP.NET-Containers für eine Containerregistrierung mithilfe von Visual Studio](../containers/hosting-web-apps-in-docker.md): Updates der Containertools für die Veröffentlichungsoberfläche von Visual Studio 16.7
- [Erste Schritte mit Kubernetes-Tools in Visual Studio](../containers/tutorial-kubernetes-tools.md): Kubernetes-Tutorial: Schritte für die Entfernung hinzugefügt

## <a name="deployment"></a>Bereitstellung

**Neue Artikel**

- [Projekterweiterung für Visual Studio-Installer und .NET Core 3.1](../deployment/installer-projects-net-core.md): Erstellen einer neuen Hilfeseite für .NET Core 3.1-Features für Installer-Projekte

**Aktualisierte Artikel**

- [Bereitstellen Ihrer App in einem Ordner, in IIS, in Azure oder einem anderen Ziel](../deployment/deploying-applications-services-and-components-resources.md): Aktualisierungen der Bereitstellung
- [Bereitstellung in Visual Studio](../deployment/index.yml): Aktualisierungen der Bereitstellung

## <a name="extensibility"></a>Erweiterungen

**Aktualisierte Artikel**
- [Projektuntertypen](../extensibility/internals/project-subtypes.md): Einzug für Listenelemente korrigiert
- [Farbwertreferenz für Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md): AB#1759333 – fehlende Spaltenüberschriften korrigiert

## <a name="get-started"></a>Erste Schritte

**Aktualisierte Artikel**

- [Schritt 5: Bereitstellen Ihrer ASP.NET Core-App in Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md): Videotutorial zur neuen Benutzeroberfläche für verbundene Dienste aktualisiert

## <a name="ide"></a>IDE

**Neue Artikel**

- [Ändern der F1-Hilfetaste in Visual Studio](./not-in-toc/change-f1-help-key.md): standardmäßige F1-Hilfeseite umgestaltet
- [F1-Hilfe für den Text-Editor](./not-in-toc/default-f1-text-editor.md): standardmäßige F1-Hilfeseite umgestaltet
- [`typeof` in `nameof` konvertieren](./reference/convert-typeof-to-nameof.md): Konvertierung von „typeof“ zu „nameof“ umgestaltet
- [Vereinfachen von LINQ-Ausdrücken](./reference/simplify-linq-expression.md): Umgestaltung von LINQ-Ausdrücken vereinfacht

**Aktualisierte Artikel**

- [Anpassen von Fensterlayouts in Visual Studio](./customizing-window-layouts-in-visual-studio.md): Infomoniker für vertikale Dokumentregisterkarten zum Thema „Anpassen von Fensterlayouts“ hinzugefügt
- [Melden eines Problems mit Visual Studio oder Visual Studio-Installer](./how-to-report-a-problem-with-visual-studio.md)
  - Weitere Informationen zu NMI hinzugefügt
  - Gesamte Seite zu „Melden eines Problems“ neu erstellt
- [F1-Hilfe](./not-in-toc/default.md): standardmäßige F1-Hilfeseite umgestaltet
- [Dialogfelder für automatisches Wiederherstellen, Umgebung und Optionen](./reference/autorecover-environment-options-dialog-box.md): Informationen zu aktualisierten Dateispeicherorten für die automatische Speicherung hinzugefügt
- [Optionen, Text-Editor, Basic (Visual Basic), Erweitert](./reference/options-text-editor-basic-visual-basic.md): grundlegende Dokumentation zu Namenshinweisen für Inlineparameter hinzugefügt
- [Optionen, Text-Editor, C#, Erweitert](./reference/options-text-editor-csharp-advanced.md): grundlegende Dokumentation zu Namenshinweisen für Inlineparameter hinzugefügt
- [Tipps und Tricks zur Leistung von Visual Studio](./visual-studio-performance-tips-and-tricks.md): Informationen zum Deaktivieren des Zuordnungsmodus und zum Deaktivieren des Zeilenumbruchs hinzugefügt
- [Neues in Visual Studio 2019](./whats-new-visual-studio-2019.md): Abschnitt „Neues in Visual Studio 2019“ mit Informationen zur allgemeinen Verfügbarkeit von Version 16.7 aktualisiert

## <a name="rtvs"></a>RTVS

**Aktualisierte Artikel**

- [Arbeiten mit SQL Server und R](../rtvs/integrating-sql-server-with-r.md): Tabellen korrigiert, sodass diese jetzt Spaltenüberschriften enthalten

## <a name="community-contributors"></a>Mitwirkende in der Community

Die folgenden Personen haben während dieses Zeitraums zu den Visual Studio-Dokumenten beigetragen. Vielen Dank! In [Leitfaden für Mitwirkende an der Microsoft-Dokumentation: Übersicht](/contribute/) erfahren Sie, wie Sie an den Visual Studio-Dokumenten mitwirken können.

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