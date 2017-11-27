---
title: Arbeitsauslastungs- und Komponenten-IDs in Visual Studio Test Professional 2017 | Microsoft-Dokumentation
description: Verwenden Sie Arbeitsauslastungs- und Komponenten-IDs in Visual Studio, um Generalisten beim Testen integrierte Testtools bereitzustellen
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-ide-install
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.openlocfilehash: 82375aa5b08b3890aa2c615f9d44877ca7fb3a22
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="visual-studio-test-professional-2017-component-directory"></a>Visual Studio Test Professional 2017-Komponentenverzeichnis

In den Tabellen auf dieser Seite sind die IDs aufgeführt, die Sie verwenden können, um Visual Studio über die Befehlszeile zu installieren. Beachten Sie, dass weitere Komponenten hinzugefügt werden, wenn wir Updates für Visual Studio veröffentlichen.

Beachten Sie zudem Folgendes im Hinblick auf diese Seite:

* Für jede Arbeitsauslastung gibt es einen eigenen Abschnitt, gefolgt von der Arbeitsauslastungs-ID und einer Tabelle der Komponenten, die für die Arbeitsauslastung zur Verfügung stehen.
* Die **erforderlichen** Komponenten werden standardmäßig bei der Installation der Arbeitsauslastung installiert. Bei Bedarf können Sie auch die **empfohlenen** und **optionalen** Komponenten installieren.
* Wir haben auch einen Abschnitt hinzugefügt, in dem die zusätzlichen Komponenten aufgeführt sind, die keiner Arbeitsauslastung zugeordnet sind.

Weitere Informationen zur Verwendung dieser IDs finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Eine Liste der Arbeitsauslastungs- und Komponenten-IDs für andere Produkte finden Sie auf der Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](workload-and-component-ids.md).

## <a name="test-professional"></a>Test Professional

**ID:** Microsoft.VisualStudio.Workload.TestProfessional

**Beschreibung:** Test Professional bietet integrierte Testtools für Generalisten beim Testen, mit denen die Testanforderungen über den gesamten Testlebenszyklus hinweg abgedeckt werden können.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.0.26711.1 | Erforderlich
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.0.26606.0 | Erforderlich

## <a name="unaffiliated-components"></a>Nicht zugeordnete Komponenten

Dies sind Komponenten, die in keiner Arbeitsauslastung enthalten sind, jedoch als einzelne Komponenten ausgewählt werden können.

Komponenten-ID | Name | Version
--- | --- | ---
n/v | nicht verfügbar | n/v

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn die Installation von Visual Studio fehlschlägt, lesen Sie den Artikel [Problembehandlung bei der Visual Studio 2017-Installation und Upgradefehlern](troubleshooting-installation-issues.md), um Hilfe bei der Problemlösung zu erhalten. Sie können uns außerdem über das Tool [Ein Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) in der Visual Studio-IDE Probleme mit Produkten melden oder uns über [UserVoice](https://visualstudio.uservoice.com/forums/121579) einen Vorschlag mitteilen. Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden. Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder anderen Visual Studio-Entwicklern aufnehmen ([GitHub](https://github.com/)-Konto erforderlich).

## <a name="see-also"></a>Siehe auch

* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Beispiele für Befehlszeilenparameter](command-line-parameter-examples.md)
* [Erstellen einer Offlineinstallation von Visual Studio](create-an-offline-installation-of-visual-studio.md)
