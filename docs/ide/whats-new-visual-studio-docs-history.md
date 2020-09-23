---
title: 'Visual Studio-Dokumentation: Verlauf der Neuerungen '
titleSuffix: ''
description: Verlauf der Neuerungen in der Visual Studio-Dokumentation
ms.date: 09/01/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 8505f98163c57fe276bcf4c76195fe843300394f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809465"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Verlauf der Neuerungen in der Visual Studio-Dokumentation

Willkommen beim Verlauf der Neuerungen in der Visual Studio-Dokumentation. Dieses Thema enthält die wichtigsten Änderungen an der Dokumentation vor August 2020 (ab Juli 2020). Aktuelle Neuerungen finden Sie unter [Visual Studio-Dokumentation: Neues in der Dokumentation](whats-new-visual-studio-docs.md).

## <a name="july-2020"></a>Juli 2020
### <a name="code-quality"></a>Codequalität

**Neue Artikel**

- [CA1417: `OutAttribute` nicht bei Zeichenfolgenparametern für P/Invokes verwenden](../code-quality/ca1417.md) – Dokumentation für CA1417 hinzufügen
- [CA1805: Keine unnötige Initialisierung.](../code-quality/ca1805.md) – Dokumente für CA1805 hinzufügen
- [CA1836: IsEmpty gegenüber Count bevorzugen, wenn verfügbar](../code-quality/ca1836.md) – Dokumentation für CA1836 hinzufügen (IsEmpty gegenüber Count bevorzugen)
- [CA2016: CancellationToken-Parameter an Methoden weiterleiten, die einen solchen Parameter entgegennehmen](../code-quality/ca2016.md) – Dokument CA2016 – CancellationToken-Parameter an Methoden weiterleiten, die einen solchen Parameter entgegennehmen
- [CA2350: Sicherstellen, dass die Eingabe von DataTable.ReadXml() vertrauenswürdig ist](../code-quality/ca2350.md) – Dokumente zu Regeln zur Deserialisierung von anfänglichem DataSet/anfänglicher DataTable
- [CA2351: Sicherstellen, dass die Eingabe von DataSet.ReadXml() vertrauenswürdig ist](../code-quality/ca2351.md) – Dokumente zu Regeln zur Deserialisierung von anfänglichem DataSet/anfänglicher DataTable
- [CA2352: Unsichere DataSet- oder DataTable-Elemente in einem serialisierbaren Typ können anfällig für Angriffe durch Remotecodeausführung sein](../code-quality/ca2352.md) – Dokumente zu Regeln zur Deserialisierung von anfänglichem DataSet/anfänglicher DataTable
- [CA2353: Unsichere DataSet- oder DataTable-Elemente in einem serialisierbaren Typ](../code-quality/ca2353.md) – Dokumente zu Regeln zur Deserialisierung von anfänglichem DataSet/anfänglicher DataTable
- [CA2354: Unsichere DataSet- oder DataTable-Elemente in einem deserialisierten Objektgraph können anfällig für Angriffe durch Remotecodeausführung sein](../code-quality/ca2354.md) – Dokumente zu Regeln zur Deserialisierung von anfänglichem DataSet/anfänglicher DataTable
- [CA2355: Unsichere DataSet- oder DataTable-Elemente in einem deserialisierten Objektgraph](../code-quality/ca2355.md) – Dokumente zu Regeln zur Deserialisierung von anfänglichem DataSet/anfänglicher DataTable
- [CA2356: Unsicherer DataSet- oder DataTable-Typ in einem webdeserialisierten Objektgraph](../code-quality/ca2356.md) – Dokumente zu Regeln zur Deserialisierung von anfänglichem DataSet/anfänglicher DataTable

### <a name="containers"></a>Container

**Neue Artikel**

- [Konfigurieren des lokalen Prozesses mit Kubernetes](../containers/configure-local-process-with-kubernetes.md) – Lokaler Prozess mit Kubernetes: YAML-Konfiguration
- [Verwenden des lokalen Prozesses mit Kubernetes (Vorschau)](../containers/local-process-kubernetes.md) – Dev Spaces-Migration
- [Funktionsweise des lokalen Prozesses mit Kubernetes](../containers/overview-local-process-kubernetes.md)
  - Lokaler Prozess für Kubernetes: Hinzufügen des Routingabschnitts
  - Dev Spaces-Migration

### <a name="cross-platform"></a>Plattformübergreifend

**Aktualisierte Artikel**

- [Änderungsprotokoll (Visual Studio Tools für Unity, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md) – VSTU-Änderungsprotokoll auf 4.7.1.0 aktualisieren
- [Änderungsprotokoll (Visual Studio Tools für Unity, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) – VSTU-Änderungsprotokoll auf 2.7.1.0 aktualisieren

### <a name="get-started"></a>Erste Schritte

**Neue Artikel**

- [Tutorial: Erweitern einer einfachen C#-Konsolen-App](../get-started/csharp/tutorial-console-part-2.md) – Veröffentlichen der ersten Version des Sidewalk-Tutorials zum Erweitern

### <a name="ide"></a>IDE

**Neue Artikel**

- [Richtlinien für die Entwicklercommunity](./developer-community-guidelines.md) – DevCom-Richtlinien wurden hinzugefügt
- [IntelliSense-Vervollständigung für nicht importierte Typen und Erweiterungsmethoden](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Installieren

**Neue Artikel**

- [Aktualisieren von Visual Studio mit einem minimalen Offlinelayout](../install/update-minimal-layout.md) – Dokumentation des Features „Minimales Layout“
- [Leitfaden zu Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) – Enterprise-Leitfaden

### <a name="javascript"></a>JavaScript

**Neue Artikel**

- [Kompilieren von TypeScript-Code (Node.js)](../javascript/compile-typescript-code-npm.md) – TypeScript kompilieren und erstellen
- [Kompilieren von TypeScript-Code (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) – TypeScript kompilieren und erstellen

### <a name="msbuild"></a>MSBuild

**Neue Artikel**

- [Gemeinsame MSBuild-Elementmetadaten](../msbuild/common-msbuild-item-metadata.md) – MSBuild: Tabelle für optionale Metadaten mit Link und LinkBase hinzufügen
- [Projektmappenfilter in MSBuild](../msbuild/solution-filters.md) – MSBuild-Projektmappenfilter

### <a name="test"></a>Test

**Neue Artikel**

- [Debuggen und Analysieren von Komponententests mit dem Test-Explorer](../test/debug-unit-tests-with-test-explorer.md) – Arbeitsweise des Test-Explorers

**Aktualisierte Artikel**

- [Konfigurieren von Komponententests mithilfe einer *RUNSETTINGS*-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Aktualisieren des Konfigurierens von Komponententests mithilfe einer RUNSETTINGS-Datei
  - Die Option „Verantwortung zuweisen“ wurde geändert und ein Beispiel hinzugefügt.