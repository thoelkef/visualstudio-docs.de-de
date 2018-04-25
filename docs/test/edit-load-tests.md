---
title: Bearbeiten von Auslastungstests in Visual Studio| Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6e79dd964593e79c69ec6ec8ab44f10ff4c9ca99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="edit-load-tests"></a>Bearbeitung von Auslastungstests

Auslastungstests führen Webleistungstests oder Komponententests aus, um den gleichzeitigen Zugriff von vielen Benutzern auf einen Server zu simulieren. Ein Auslastungstest gewährt Ihnen Zugriff auf die Anwendungsbelastung und die Leistungsdaten. Ein Auslastungstest kann konfiguriert werden, um verschiedene Auslastungsbedingungen z. B. Benutzerlasten und Netzwerktypen zu emulieren.

> [!NOTE]
> Auslastungstests sind nur in der Enterprise Edition von Visual Studio 2017 verfügbar.

Ein Auslastungstest wird mithilfe von *Szenarios*, *Indikatorensätzen* und *Laufzeiteinstellungen* definiert. In der folgenden Abbildung werden die Unterschiede zwischen [Szenarios](../test/edit-load-test-scenarios.md), [Indikatorensätzen](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md) und [Laufzeiteinstellungen](../test/load-test-run-settings-properties.md) veranschaulicht:

![Laden der Testarchitektur](../test/media/load_test_editor.png)

## <a name="edit-load-test-scenario-settings"></a>Bearbeiten von Auslastungstestszenario-Einstellungen

Mit einem Szenario wird festgelegt, wie eine Gruppe von Benutzern mit einer Serveranwendung interagiert. Ein Szenario besteht aus einem Auslastungsmuster, einem Testmischungsmodell, einer Testmischung, einem Browsermix und einer Netzwerkmischung. Ein Auslastungstest kann mehr als ein Szenario besitzen, und ein einzelnes Szenario kann Webleistungs- und Komponententests umfassen. Durch Gruppieren ähnlicher Einstellungen können Sie in einem Szenario ähnliche Tests gruppieren und zusammen ausführen.

Weitere Informationen finden Sie unter [Editing Load Test Scenarios (Szenarios zum Bearbeiten von Auslastungstests)](../test/edit-load-test-scenarios.md) und [Load Test Scenario Properties (Auslastungstestszenario-Einstellungen)](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurieren und Verwalten von Leistungsindikatorensätzen

Auslastungstests stellen benannte, nach verwendeter Technologie organisierte Indikatorensätze zur Verfügung, die bei der Analyse von Leistungsindikatordaten von Nutzen sind. Die Indikatorensätze enthalten Auslastungstest, IIS, ASP.NET und SQL. Wenn Sie einen Auslastungstest mit dem Assistenten für neuen Auslastungstest erstellen, wird für die Computer, die Sie in den Auslastungstest einschließen, ein Ausgangssatz mit vordefinierten und wichtigen Indikatoren konfiguriert. Sie können die Indikatoren im Auslastungstest-Editor verwalten.

Weitere Informationen finden Sie unter [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Konfigurieren und Verwalten von Laufzeiteinstellungen von Auslastungstests

Laufzeiteinstellungen stellen Eigenschaften dar, die die Art der Ausführung eines Testlaufs beeinflussen. Testlaufeinstellungen sind im Eigenschaftenfenster nach Kategorien geordnet.

Weitere Informationen finden Sie unter [Configuring Load Test Run Settings (Konfigurieren von Laufzeiteinstellungen von Auslastungstests)](../test/configure-load-test-run-settings.md) und [Load Test Run Settings Properties (Eigenschaften der Laufzeiteinstellungen von Auslastungstests)](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Siehe auch

- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyzing Threshold Rule Violations (Analysieren von Verstößen gegen die Schwellenwertregel)](../test/analyze-threshold-rule-violations-in-load-tests.md)