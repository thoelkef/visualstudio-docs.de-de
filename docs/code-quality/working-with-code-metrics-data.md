---
title: Der Codemetrikergebnisse Fenster in Visual Studio
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8400ce0d407af2318c4fffa19bc2b41e23f034d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284133"
---
# <a name="using-the-code-metrics-results-window"></a>Verwenden des Fensters Codemetrikergebnisse

Die **Codemetrikergebnisse** Fenster zeigt die Daten, die von der Codeanalyse für die Metrik generiert werden. Weitere Informationen zu Datenwerten der Codemetrik, finden Sie unter [Code Metrikwerte](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Anzeigen von Codemetrikergebnissen

Die **Codemetrikergebnisse** Fenster wird automatisch beim Generieren von Codemetrikergebnissen angezeigt. Sie können auch das Fenster jederzeit anzeigen.

### <a name="to-display-the-code-metrics-results-window"></a>Um das Fenster Codemetrikergebnisse anzuzeigen

- Auf der **analysieren** Menü wählen **Windows** > **Codemetrikergebnisse**.

   \- oder –

- Auf der **Ansicht** Menü wählen **Other Windows** > **Codemetrikergebnisse**.

Die **Codemetrikergebnisse** Fenster wird angezeigt, auch wenn es sich um keine Ergebnisse enthält.

### <a name="to-view-code-metrics-details"></a>Anzeigen von Details von basisanalysemetriken

Wenn Codemetrikergebnisse generiert wurden, erweitern Sie die Struktur in der **Hierarchie** Spalte.

## <a name="filtering-code-metrics-results"></a>Filtern von Codemetrikergebnissen

Sie können die Ergebnisse, die in angezeigt werden, Filtern die **Codemetrikergebnisse** Fenster mithilfe der Symbolleiste oben. Beispielsweise empfiehlt es sich um nur die Ergebnisse anzuzeigen, die einen Wartbarkeitsindex unter 65 haben.

Die **Filter** Dropdown-Feld enthält die Namen der Ergebnisspalten. Wenn ein Filter definiert wird, wird es am Ende der Liste zusammen mit einem Einzug hinzugefügt. Die Liste kann die letzten zehn Filter enthalten, die definiert wurden.

### <a name="to-filter-the-code-metrics-results"></a>Zum Filtern der Codemetrikergebnisse

1.  Von der **Filter** wählen Sie den Namen der Spalte.

2.  In **Min**, geben Sie den minimalen Wert, der angezeigt werden.

3.  In **Max**, geben Sie den maximalen Wert angezeigt werden.

4.  Klicken Sie auf die **Filter anwenden** Schaltfläche.

5.  Um die Details der anzuzeigen, erweitern Sie in der Hierarchiestruktur.

## <a name="adding-removing-and-rearranging-data-columns"></a>Hinzufügen, entfernen und Neuanordnen von Spalten

Sie können hinzufügen oder entfernen führt die Spalten aus der **Codemetrikergebnisse** Fenster. Darüber hinaus können Sie Ergebnisspalten neu anordnen, damit sie in der Reihenfolge angezeigt werden, die Sie möchten.

### <a name="to-remove-a-column"></a>Eine Spalte entfernen

1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.

     \- oder mit der rechten Maustaste in eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.

1. In der **Spalten hinzufügen/entfernen** Dialogfeld deaktivieren das Kontrollkästchen für die Spalte, die Sie entfernen möchten und klicken Sie dann auf **OK**.

### <a name="to-add-a-previously-removed-column"></a>Hinzufügen eine zuvor entfernte Spalte

1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.

     \- oder –

     Mit der rechten Maustaste in eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.

1. In der **Spalten hinzufügen/entfernen** Dialogfeld Feld, das Kontrollkästchen für die Spalte, die Sie hinzufügen möchten und klicken Sie dann auf **OK**.

### <a name="to-rearrange-columns"></a>Um Spalten neu anzuordnen.

1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.

     \- oder –

     Mit der rechten Maustaste in eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.

1. In der **Spalten hinzufügen/entfernen** Dialogfeld wählen die Spalte, die Sie verschieben möchten und klicken Sie dann auf, entweder auf den Pfeil nach oben oder auf den Pfeil nach unten.

1. Wenn die Spalte an der gewünschten Position befindet, klicken Sie auf **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Kopieren von Daten in die Zwischenablage oder Excel

Sie können auswählen, und eine ausgewählte Zeile von Codemetrikdaten werden in die Zwischenablage kopieren, als eine Zeichenfolge, die eine Zeile für den Namen und den Wert der einzelnen Datenspalten enthält. Sie können auch klicken **Auswahl in Microsoft Excel öffnen** aller der Codemetrikergebnisse in eine Excel-Kalkulationstabelle exportieren.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Erstellen eines Arbeitselements anhand von Codemetrikergebnissen

Können Sie erstellen eine [Azure Boards](/azure/devops/boards/index) führt zu Arbeitselement auf der Grundlage der **Codemetrikergebnisse** Fenster. Wenn das Arbeitselement erstellt wird, fügt Visual Studio automatisch einen Titel in der **Titel** Feld und die Codemetrikdaten werden unter der **Verlauf** Registerkarte.

Weitere Informationen zu Azure-Boards Arbeitselemente angezeigt werden, finden Sie unter [Arbeitsaufgaben](/azure/devops/boards/work-items/index).

### <a name="to-create-a-work-item-based-on-a-result"></a>Um eine Arbeitsaufgabe basierend auf ein Ergebnis zu erstellen.

1.  Mit der rechten Maustaste in des Ergebnis.

2.  Zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ des zu erstellenden Arbeitsaufgabe (**Fehler**, **Aufgabe**usw.).

3.  Führen Sie das arbeitselementformular, indem Sie alle erforderlichen Felder ausfüllen.

4.  Auf der **Datei** Menü klicken Sie auf **Alles speichern** zum Speichern des Arbeitselements.

### <a name="to-create-a-bug-based-on-a-result"></a>So erstellen Sie einen Fehler basierend auf ein Ergebnis

1.  Klicken Sie auf das Ergebnis, um es auszuwählen.

2.  Klicken Sie auf die **Arbeitselement erstellen** Schaltfläche.

3.  Führen Sie das arbeitselementformular, indem Sie alle erforderlichen Felder ausfüllen.

4.  Auf der **Datei** Menü klicken Sie auf **Alles speichern** zum Speichern des Arbeitselements.

## <a name="see-also"></a>Siehe auch

- [Codemetrikwerte](../code-quality/code-metrics-values.md)
- [Gewusst wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)