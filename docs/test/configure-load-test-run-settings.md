---
title: Konfigurieren der Laufzeiteinstellungen für Auslastungstests in Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: fb1f9ad69ebe012151a911bf8d7c02ded6af5e11
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283328"
---
# <a name="configure-load-test-run-settings"></a>Konfigurieren der Laufzeiteinstellungen für Auslastungstests

*Laufzeiteinstellungen* stellen mehrere Eigenschaften dar, die die Art der Ausführung eines Auslastungstests beeinflussen. Laufzeiteinstellungen werden nach Kategorien im **Eigenschaftenfenster** strukturiert.

Sie können mehr als eine Laufzeiteinstellung in einem Auslastungstest verwenden, jedoch kann nur eine der Laufzeiteinstellungen pro Ausführung aktiv sein. Die anderen Laufzeiteinstellungen bieten eine schnelle Möglichkeit zur Auswahl einer alternativen Einstellung für nachfolgende Testläufe.

Die anfängliche Laufzeiteinstellung wird erstellt, wenn Sie einen Auslastungstest mit dem **Assistenten für neuen Auslastungstest** erstellen.

![Laden von Laufzeiteinstellungen](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-----------|-----------------------|
|**Hinzufügen weiterer Laufzeiteinstellungen zum Auslastungstest:** Neben der Laufzeiteinstellung, die beim Ausführen des **Assistenten für neuen Auslastungstest** erstellt wird, können Sie dem Auslastungstest zusätzliche Laufzeiteinstellungen hinzufügen, damit Sie den Test unter anderen Bedingungen ausführen können.|-   [Vorgehensweise: Hinzufügen von weiteren Laufzeiteinstellungen zu einem Auslastungstest](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Angeben der aktiven Laufzeiteinstellung zur Verwendung mit dem Auslastungstest:** Sie können mithilfe des Auslastungstest-Editors die Laufzeiteinstellung auswählen, die mit dem Auslastungstest verwendet werden soll. Die aktive Testlaufeinstellung wird durch das Suffix "[Active]" gekennzeichnet.|-   [Vorgehensweise: Auswählen der aktiven Laufzeiteinstellungen für einen Auslastungstest](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Bearbeiten der Eigenschaften der Laufzeiteinstellungen:** Sie können die Eigenschaften der Laufzeiteinstellungen bearbeiten, z.B. Protokollierungsoptionen (weitere Informationen siehe unten), Dauer des Tests und der Aufwärmphase, maximale Anzahl der Fehlerdetails in Berichten, Samplingrate, Verbindungsmodell (nur bei Webleistungstests), Ergebnisspeichertyp, Validierungsebene und SQL-Ablaufverfolgung. Die Laufzeiteinstellungen sollten den Zielen des Auslastungstests entsprechen.|-   [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md)<br />-   [Ändern der Eigenschaften von Laufzeiteinstellungen](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Angeben der Anzahl der Testiterationen in Laufzeiteinstellungen für Auslastungstests:** Sie können die Anzahl der Durchläufe für alle Webleistungs- und Komponententests in allen Szenarios der Auslastungstests angeben, indem Sie die Eigenschaft **Testiterationen** konfigurieren.|-   [How to: Specify the Number of Test Iterations in a Run Setting (Vorgehensweise: Angeben der Anzahl von Testiterationen in einer Laufzeiteinstellung)](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Angeben der Samplingrate für eine Laufzeiteinstellung für Auslastungstests:** Sie können angeben, wie oft vom Auslastungstest Leistungsindikatordaten gesammelt werden sollen, indem Sie die Eigenschaft **Samplingrate** konfigurieren.|-   [How to: Specify the Sample Rate (Vorgehensweise: Angeben der Abtastrate)](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Angeben der Speicheroption für zeitliche Steuerungsdetails:** Sie können angeben, wie die Details des Auslastungstests gespeichert werden sollen, indem Sie die Eigenschaft **Speicher für Details der zeitlichen Steuerung** konfigurieren.|-   [How to: Specify the Timing Details Storage Property (Vorgehensweise: Angeben der Eigenschaft „Speicher für Details der zeitlichen Steuerung“)](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Angeben der Beibehaltungsdauer der Testressourcen:** beschleunigt den Zyklus zum Testen, Beheben von Problemen und erneutem Testen, indem die Testressourcen für einen angegebenen Zeitraum durch Festlegen der Eigenschaft **Ressourcenbeibehaltungsdauer** beibehalten werden.|-   [Retain the resources to speed up load testing (Beibehalten der Ressourcen zur Beschleunigung der Auslastungstests)](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Verwenden von Kontextparametern:** Sie können mithilfe von Kontextparametern eine Zeichenfolge parametrisieren. Wenn der Auslastungstest z.B. einen Webleistungstest enthält, der einen parametrisierten Webserver verwendet, können Sie den Laufzeiteinstellungen einen auf einen anderen Server verweisenden Kontextparameter hinzufügen.|-   [How to: Add Context Parameters to a Run Setting (Vorgehensweise: Hinzufügen von Kontextparametern zu einer Laufzeiteinstellung)](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurieren von Testprotokollierungseigenschaften:** Sie können konfigurieren, wie oft Daten in das den Laufzeiteinstellungen des Auslastungstests zugewiesene Protokoll geschrieben werden sollen. Dies kann bei der Ausführung eines umfangreichen oder komplexen Auslastungstests wichtig sein, da die Größe des Protokolls dann mehrere Gigabyte umfassen kann.<br /><br /> Sie können auch festlegen, dass die Protokolldatei automatisch gespeichert wird, wenn der Auslastungstest beim Debuggen und Analysieren der Anwendung nicht von Nutzen ist.|-   [Ändern von Einstellungen für die Auslastungstestprotokollierung](../test/modify-load-test-logging-settings.md)|