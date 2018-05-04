---
title: Protokollierungseinstellungen für Auslastungstests in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ffd20812ec37e324dc919ea5943cf30a5329321b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="modify-load-test-logging-settings"></a>Ändern von Einstellungen für die Auslastungstestprotokollierung

Das Auslastungstestergebnis für den abgeschlossenen Auslastungstest enthält Leistungsindikatorsamplings und Fehlerinformationen, die in regelmäßigen Abständen von den Testcomputern in einem Protokoll erfasst wurden. Im Verlauf eines Auslastungstestlaufs kann eine große Anzahl von Leistungsindikatorsamplings erfasst werden. Die Menge der gesammelten Leistungsdaten hängt von der Länge des Testlaufs, dem Samplingintervall, der Anzahl von Testcomputern und der Anzahl zu erfassender Indikatoren ab. Da bei einem großen Auslastungstest die gesammelte Menge von Leistungsdaten leicht mehrere Gigabytes betragen kann, können Sie ggf. die Häufigkeit ändern, mit der Daten im Protokoll gespeichert werden. Weitere Informationen finden Sie unter [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

Der *Testcontroller* spoolt während der Testausführung alle gesammelten Beispieldaten des Auslastungstests in ein Datenbankprotokoll. Weitere Daten, z. B. Details zur zeitlichen Steuerung und Fehlerdetails, werden nach Abschluss des Tests in die Datenbank geladen.

|Aufgabe|Verwandte Themen|
|----------|-----------------------|
|**Festlegen der Häufigkeit, mit der Protokolle während eines Auslastungstestlaufs gespeichert werden:** Sie können angeben, wie oft das Testprotokoll bei der Ausführung des Auslastungstests gespeichert werden soll.|-   [How to: Specify How Frequently Test Logs are Saved (Vorgehensweise: Angeben, wie häufig Testprotokolle gespeichert werden)](../test/how-to-specify-how-frequently-test-logs-are-saved.md)|
|**Speichern von Protokollen bei einem Auslastungstestfehler:** Sie können angeben, ob das Testprotokoll gespeichert werden soll, wenn ein Auslastungstest fehlschlägt.|-   [How to: Specify if Test Failures are Saved to Test Logs (Vorgehensweise: Angeben, ob Testfehler in Testprotokollen gespeichert werden)](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Festlegen der maximalen Dateigröße für die Protokolldatei:** Sie können die XML-Konfigurationsdatei für den Testcontrollerdienst bearbeiten, um die gewünschte maximale Dateigröße für die Protokolldatei anzugeben.|[Gewusst wie: Angeben der maximalen Größe für die Protokolldatei](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="related-tasks"></a>Verwandte Aufgaben

Eine verwandte Eigenschaft ist **Speicher für Details der zeitlichen Steuerung**. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren der Erfassung aller Details zur Verwendung des Diagramms für Aktivitäten virtueller Benutzer](../test/how-to-configure-load-tests-to-collect-full-details.md).

## <a name="see-also"></a>Siehe auch

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)