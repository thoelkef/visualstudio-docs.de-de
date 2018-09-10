---
title: Bearbeiten von Auslastungstests in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f4c29f3b98440c9e8462083a24012944157b848b
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178412"
---
# <a name="edit-load-tests"></a>Bearbeitung von Auslastungstests

Auslastungstests führen Webleistungstests oder Komponententests aus, um den gleichzeitigen Zugriff von vielen Benutzern auf einen Server zu simulieren. Ein Auslastungstest gewährt Ihnen Zugriff auf die Anwendungsbelastung und die Leistungsdaten. Ein Auslastungstest kann konfiguriert werden, um verschiedene Auslastungsbedingungen z. B. Benutzerlasten und Netzwerktypen zu emulieren.

> [!NOTE]
> Auslastungstests sind nur in der Enterprise Edition von Visual Studio 2017 verfügbar.

Ein Auslastungstest wird mithilfe von *Szenarios*, *Indikatorensätzen* und *Laufzeiteinstellungen* definiert. In der folgenden Abbildung werden die Unterschiede zwischen [Szenarios](../test/edit-load-test-scenarios.md), [Indikatorensätzen](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md) und [Laufzeiteinstellungen](../test/load-test-run-settings-properties.md) veranschaulicht:

![Laden der Testarchitektur](../test/media/load_test_editor.png)

## <a name="edit-load-test-scenario-settings"></a>Bearbeiten von Auslastungstestszenario-Einstellungen

Mit einem Szenario wird festgelegt, wie eine Gruppe von Benutzern mit einer Serveranwendung interagiert. Ein Szenario besteht aus einem Auslastungsmuster, einem Testmischungsmodell, einer Testmischung, einem Browsermix und einer Netzwerkmischung. Ein Auslastungstest kann mehr als ein Szenario besitzen, und ein einzelnes Szenario kann Webleistungs- und Komponententests umfassen. Durch Gruppieren ähnlicher Einstellungen können Sie in einem Szenario ähnliche Tests gruppieren und zusammen ausführen.

Weitere Informationen finden Sie unter [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md) und [Laden von Testszenarioeigenschaften](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurieren und Verwalten von Leistungsindikatorensätzen

Auslastungstests stellen benannte, nach verwendeter Technologie organisierte Indikatorensätze zur Verfügung, die bei der Analyse von Leistungsindikatordaten von Nutzen sind. Die Indikatorensätze enthalten Auslastungstest, IIS, ASP.NET und SQL. Wenn Sie einen Auslastungstest mit dem **Assistenten für neuen Auslastungstest** erstellen, wird für die Computer, die Sie in den Auslastungstest einschließen, ein Ausgangssatz mit vordefinierten und wichtigen Indikatoren konfiguriert. Sie können die Indikatoren mit dem **Auslastungstest-Editor** verwalten.

Weitere Informationen finden Sie unter [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Konfigurieren und Verwalten von Laufzeiteinstellungen von Auslastungstests

Laufzeiteinstellungen stellen Eigenschaften dar, die die Art der Ausführung eines Testlaufs beeinflussen. Laufzeiteinstellungen werden nach Kategorien im **Eigenschaftenfenster** strukturiert.

Weitere Informationen finden Sie unter [Konfigurieren der Laufzeiteinstellungen von Auslastungstests](../test/configure-load-test-run-settings.md) und [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Siehe auch

- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analysieren von Verletzungen der Schwellenwertregeln in Auslastungstests mithilfe des Auslastungstest-Analyzers](../test/analyze-threshold-rule-violations-in-load-tests.md)