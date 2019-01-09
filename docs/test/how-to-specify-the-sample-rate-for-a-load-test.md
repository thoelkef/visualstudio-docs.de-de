---
title: 'Vorgehensweise: Festlegen der Abtastrate für die Einstellung eines Auslastungstestlaufs'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 896975330db08a0121aedd4bf3bea38f660e17fc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931267"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Vorgehensweise: Festlegen der Abtastrate für die Einstellung eines Auslastungstestlaufs

Nach dem Erstellen des Auslastungstests mit dem **Assistenten für neuen Auslastungstest** können Sie mit dem **Auslastungstest-Editor** die Eigenschaften ändern, um die Testanforderungen und -ziele zu erreichen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Mit dem **Auslastungstest-Editor** können Sie den Eigenschaftswert **Samplingrate** einer Laufzeiteinstellung im Fenster **Eigenschaften** bearbeiten. Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

Wählen Sie basierend auf der Länge des Auslastungstests einen entsprechenden Wert für die Eigenschaft **Samplingrate** für die Laufzeiteinstellung des Auslastungstests aus. Eine kleinere Samplingrate (z. B. der Standardwert von fünf Sekunden) erfordert mehr Speicherplatz in der Datenbank für die Auslastungstestergebnisse. Bei längeren Auslastungstests wird durch eine höhere Samplingrate die gesammelte Datenmenge reduziert. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen der Abtastrate für die Einstellung eines Auslastungstestlaufs](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Die folgende Tabelle enthält Richtlinien für die Samplingraten:

|Dauer des Auslastungstests|Empfohlene Samplingrate|
|-|-----------------------------|
|\< 1 Stunde|5 Sekunden|
|1 – 8 Stunden|15 Sekunden|
|8 – 24 Stunden|30 Sekunden|
|> 24 Stunden|60 Sekunden|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>So geben Sie die Leistungsindikator-Samplingrate in einer Testlaufeinstellung an

1.  Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2.  Klicken Sie in der Auslastungsteststruktur im Ordner **Laufzeiteinstellungen** auf die Laufzeiteinstellung, für die Sie die Samplingrate angeben möchten.

3.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Kategorien und Eigenschaften der Testlaufeinstellung werden im **Eigenschaftenfenster** angezeigt.

4.  Geben Sie in der Eigenschaft **Samplingrate** einen Zeitwert ein, der die Häufigkeit angibt, mit der Leistungsindikatordaten beim Auslastungstest gesammelt werden.

5.  Nachdem die Änderungen der Eigenschaft abgeschlossen sind, klicken Sie im Menü **Datei** auf die Option **Speichern**. Anschließend können Sie den Auslastungstest mit dem neuen Wert für **Samplingrate** ausführen.

## <a name="see-also"></a>Siehe auch

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)