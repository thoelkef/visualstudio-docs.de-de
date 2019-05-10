---
title: Codemetrikfenster
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe2c216a9293ddc8c5c1212957c2987924d14e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825070"
---
# <a name="use-the-code-metrics-results-window"></a>Verwenden Sie das Fenster Codemetrikergebnisse

Die **Codemetrikergebnisse** Fenster zeigt die Daten, die von der Codeanalyse für die Metrik generiert werden. Weitere Informationen zu Datenwerten der Codemetrik, finden Sie unter [Code Metrikwerte](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Anzeigen von Codemetrikergebnissen

Die **Codemetrikergebnisse** Fenster wird automatisch beim Generieren von Codemetrikergebnissen angezeigt. Sie können auch das Fenster jederzeit anzeigen.

Sie können das Codemetrikergebnisse-Fenster, das mithilfe einer der Sequenzen folgenden Menü anzeigen:

- Auf der **analysieren** Menü wählen **Windows** > **Codemetrikergebnisse**.

- Auf der **Ansicht** Menü wählen **Other Windows** > **Codemetrikergebnisse**.

Die **Codemetrikergebnisse** Fenster geöffnet wird, auch wenn es sich um keine Ergebnisse enthält.

### <a name="to-view-code-metrics-details"></a>Anzeigen von Details von basisanalysemetriken

Wenn Codemetrikergebnisse generiert wurden, erweitern Sie die Struktur in der **Hierarchie** Spalte.

## <a name="filter-code-metrics-results"></a>Filtern von Codemetrikergebnissen

Sie können die Ergebnisse, die in angezeigt werden, Filtern die **Codemetrikergebnisse** Fenster mithilfe der Symbolleiste oben. Beispielsweise empfiehlt es sich um nur die Ergebnisse anzuzeigen, die einen Wartbarkeitsindex unter 65 haben.

Die **Filter** Dropdown-Feld enthält die Namen der Ergebnisspalten. Wenn ein Filter definiert wird, wird es am Ende der Liste zusammen mit einem Einzug hinzugefügt. Die Liste kann die letzten 10 Filter enthalten, die definiert wurden.

### <a name="to-filter-the-code-metrics-results"></a>Zum Filtern der Codemetrikergebnisse

1. Von der **Filter** wählen Sie den Namen der Spalte.

2. In **Min**, geben Sie den minimalen Wert, der angezeigt werden.

3. In **Max**, geben Sie den maximalen Wert angezeigt werden.

4. Klicken Sie auf die **Filter anwenden** Schaltfläche.

5. Um die Details der anzuzeigen, erweitern Sie in der Hierarchiestruktur.

## <a name="add-remove-and-rearrange-data-columns"></a>Hinzufügen, entfernen und Neuanordnen von Datenspalten

Sie können hinzufügen oder entfernen führt die Spalten aus der **Codemetrikergebnisse** Fenster. Darüber hinaus können Sie Ergebnisspalten neu anordnen, damit sie in der Reihenfolge angezeigt werden, die Sie möchten.

### <a name="add-or-remove-a-column"></a>Hinzufügen oder Entfernen einer Spalte

1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche oder mit der rechten Maustaste in eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.

1. In der **Spalten hinzufügen/entfernen** Dialogfeld aktivieren oder deaktivieren das Kontrollkästchen für die Spalte, die Sie verwenden möchten, hinzufügen oder entfernen, und wählen Sie dann **OK**.

### <a name="rearrange-columns"></a>Neuanordnen von Spalten

1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.

1. In der **Spalten hinzufügen/entfernen** Dialogfeld wählen die Spalte, die Sie verschieben möchten und wählen Sie dann entweder auf den Pfeil nach oben oder auf den Pfeil nach unten.

1. Wenn die Spalte an der gewünschten Position befindet, wählen Sie **OK**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Kopieren von Daten in die Zwischenablage oder Excel

Sie können auswählen, und eine ausgewählte Zeile von Codemetrikdaten werden in die Zwischenablage kopieren, als eine Zeichenfolge, die eine Zeile für den Namen und den Wert der einzelnen Datenspalten enthält. Sie können auch klicken **Auswahl in Microsoft Excel öffnen** aller der Codemetrikergebnisse in eine Excel-Kalkulationstabelle exportieren.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Erstellen einer Arbeitsaufgabe anhand von Codemetrikergebnissen

Können Sie erstellen eine [Azure Boards](/azure/devops/boards/index?view=vsts) führt zu Arbeitselement auf der Grundlage der **Codemetrikergebnisse** Fenster. Wenn das Arbeitselement erstellt wird, fügt Visual Studio automatisch einen Titel in der **Titel** Feld und die Codemetrikdaten werden unter der **Verlauf** Registerkarte.

Weitere Informationen zu Azure-Boards Arbeitselemente angezeigt werden, finden Sie unter [Arbeitsaufgaben](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Um eine Arbeitsaufgabe basierend auf ein Ergebnis zu erstellen.

1. Mit der rechten Maustaste in des Ergebnis.

2. Zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ des zu erstellenden Arbeitsaufgabe (**Fehler**, **Aufgabe**usw.).

3. Führen Sie das arbeitselementformular, indem Sie alle erforderlichen Felder ausfüllen.

4. Auf der **Datei** Menü klicken Sie auf **Alles speichern** zum Speichern des Arbeitselements.

### <a name="to-create-a-bug-based-on-a-result"></a>So erstellen Sie einen Fehler basierend auf ein Ergebnis

1. Klicken Sie auf das Ergebnis, um es auszuwählen.

2. Klicken Sie auf die **Arbeitselement erstellen** Schaltfläche.

3. Führen Sie das arbeitselementformular, indem Sie alle erforderlichen Felder ausfüllen.

4. Auf der **Datei** Menü klicken Sie auf **Alles speichern** zum Speichern des Arbeitselements.

## <a name="see-also"></a>Siehe auch

- [Codemetrikwerte](../code-quality/code-metrics-values.md)
- [Vorgehensweise: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)