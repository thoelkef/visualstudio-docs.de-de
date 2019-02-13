---
title: Einstellungen für die Auslastungstestprotokollierung
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c60aa8284dd19401fb2f4b6db3dc0ec0fc9c7942
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948848"
---
# <a name="modify-load-test-logging-settings"></a>Ändern von Einstellungen für die Auslastungstestprotokollierung

Das Auslastungstestergebnis für den abgeschlossenen Auslastungstest enthält Leistungsindikatorsamplings und Fehlerinformationen, die in regelmäßigen Abständen von den Testcomputern in einem Protokoll erfasst wurden. Im Verlauf eines Auslastungstestlaufs kann eine große Anzahl von Leistungsindikatorsamplings erfasst werden. Die Menge der gesammelten Leistungsdaten hängt von der Länge des Testlaufs, dem Samplingintervall, der Anzahl von Testcomputern und der Anzahl zu erfassender Indikatoren ab. Da bei einem großen Auslastungstest die gesammelte Menge von Leistungsdaten leicht mehrere Gigabytes betragen kann, können Sie ggf. die Häufigkeit ändern, mit der Daten im Protokoll gespeichert werden. Weitere Informationen finden Sie unter [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Der *Testcontroller* spoolt während der Testausführung alle gesammelten Beispieldaten des Auslastungstests in ein Datenbankprotokoll. Weitere Daten, z. B. Details zur zeitlichen Steuerung und Fehlerdetails, werden nach Abschluss des Tests in die Datenbank geladen.

|Aufgabe|Verwandte Themen|
|-|-----------------------|
|**Speichern von Protokollen bei einem Auslastungstestfehler:** Sie können angeben, ob das Testprotokoll gespeichert werden soll, wenn ein Auslastungstest fehlschlägt.|-   [Vorgehensweise: Angeben, ob Testfehler in Testprotokollen gespeichert werden](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Festlegen der maximalen Dateigröße für die Protokolldatei:** Sie können die XML-Konfigurationsdatei für den Testcontrollerdienst bearbeiten, um die gewünschte maximale Dateigröße für die Protokolldatei anzugeben.|[Vorgehensweise: Angeben der maximalen Größe für die Protokolldatei](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="see-also"></a>Siehe auch

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)