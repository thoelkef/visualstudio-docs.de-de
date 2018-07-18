---
title: Erstellen eines Adapters für diagnostische Daten für Tests in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: a12cac4e3a0c7144fd2e2cca2044ad416ac966d0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31964950"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Erstellen eines Adapters für diagnostische Daten zum Sammeln von benutzerdefinierten Daten oder Beeinflussen eines Testsystems

Sie können einen eigenen Adapter für diagnostische Daten erstellen, um Daten während der Ausführung eines Tests zu erstellen oder im Rahmen des Tests den Testcomputer zu beeinflussen. Sie möchten beispielsweise Protokolldateien sammeln, die von der getesteten Anwendung erstellt werden, und diese an die Testergebnisse anhängen, oder Sie möchten Tests ausführen, wenn nur noch wenig Speicherplatz auf Ihrem Computer vorhanden ist. Mithilfe der von Visual Studio Enterprise bereitgestellten APIs können Sie Code zur Ausführung von Aufgaben an bestimmten Punkten im Testlauf schreiben. Zum Beispiel können Sie Aufgaben beim Start eines Testlaufs, vor und nach der Ausführung der einzelnen Tests und beim Beenden des Testlaufs ausführen.

Mithilfe einer Datei mit Konfigurationseinstellungen können Sie Standardeingaben für einen benutzerdefinierten Adapter für diagnostische Daten bereitstellen. So können Sie beispielsweise Informationen zum Speicherort der zu erfassenden Datei angeben, die den Testergebnissen angefügt werden soll, und festlegen, wie viel Speicherplatz auf dem System verbleiben soll. Diese Daten können für alle von Ihnen erstellten Testeinstellungen konfiguriert werden. Sie können mit dem von Microsoft Test Manager bereitgestellten Standard-Editor angezeigt und bearbeitet werden. Es besteht auch die Möglichkeit, ein eigenes Benutzersteuerelement zu erstellen, das als Editor verwendet wird. Alle an der Adapterkonfiguration im Editor vorgenommenen Änderungen werden mit den Testeinstellungen gespeichert.

Wenn Sie die Tests aus Visual Studio ausführen, müssen Sie für diese Testeinstellungen festlegen, dass sie aktiv sind. Weitere Informationen zu Testeinstellungen finden Sie unter [Collect Diagnostic Information Using Test Settings (Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md).

## <a name="tasks"></a>Aufgaben

 In den folgenden Themen wird veranschaulicht, wie Sie Adapter für diagnostische Daten erstellen können:

|Aufgaben|Verwandte Themen|
|-----------|-----------------------|
|**Erstellen eines Adapters für diagnostische Daten:** Sie erstellen einen Adapter für diagnostische Daten, indem Sie eine Klassenbibliothek erstellen, und Sie können dann die APIs des Adapters für diagnostische Daten verwenden, um die gewünschten Informationen zu sammeln oder das Testsystem zu beeinflussen, das Sie zum Ausführen der Tests verwenden.|-   [Vorgehensweise: Erstellen eines Adapters für diagnostische Daten](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Installieren eines benutzerdefinierten Adapters für diagnostische Daten:** Sie können den Adapter für diagnostische Daten oder einen von anderer Seite bereitgestellten Adapter installieren, indem Sie diesen in das richtige Verzeichnis kopieren.|-   [Vorgehensweise: Installieren eines benutzerdefinierten Adapters für diagnostische Daten](../test/how-to-install-a-custom-diagnostic-data-adapter.md)|
|**Auswählen eines benutzerdefinierten Adapters für diagnostische Daten, der beim Ausführen der Tests verwendet wird:** Sie können den Adapter für diagnostische Daten auswählen, der für die Testeinstellungen verwendet werden soll, d.h. den Adapter, der zum Ausführen der Tests verwendet wird.|-   [Collect diagnostic data while testing (VSTS) (Sammeln von Diagnosedaten beim Testen (VSTS))](/vsts/manual-test/collect-diagnostic-data)<br />-   [Collect diagnostic data in manual tests (VSTS) (Sammeln von Diagnosedaten in manuellen Tests (VSTS))](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)|
|**Konfigurieren der durch einen Adapter für diagnostische Daten ausgeführten Aktionen:** Sie können Einstellungen zur Steuerung der Aktionen des Adapters für diagnostische Daten in den entsprechenden Testeinstellungen konfigurieren.|-   [Vorgehensweise: Erstellen eines benutzerdefinierten Editors für Daten im Adapter für diagnostische Daten](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)|

## <a name="see-also"></a>Siehe auch

- [Beispielprojekt für das Erstellen eines Adapters für diagnostische Daten](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Collect Diagnostic Information Using Test Settings (Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md)