---
title: Das Fenster Codemetrikergebnisse in Visual Studio
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
ms.openlocfilehash: c5e6fdff99a8fc28e83fe4848fa4f31788cda76f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923868"
---
# <a name="using-the-code-metrics-results-window"></a>Mithilfe des Fensters Codemetrikergebnisse

Die **Codemetrikergebnisse** Fenster zeigt die Daten, die von der Codeanalyse für die Metrik generiert werden. Weitere Informationen zu Daten für die codemetrikwerte, finden Sie unter [Code Metrikwerte](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Anzeigen von Codemetrikergebnissen

Die **Codemetrikergebnisse** Fenster wird automatisch angezeigt, wenn Sie Codemetrikergebnisse generieren. Sie können auch das Fenster jederzeit anzeigen.

### <a name="to-display-the-code-metrics-results-window"></a>Zum Anzeigen des Fensters Codemetrikergebnisse

- Auf der **analysieren** Menü wählen **Windows** > **Codemetrikergebnisse**.

   \- oder –

- Auf der **Ansicht** Menü wählen **Weitere Fenster** > **Codemetrikergebnisse**.

Die **Codemetrikergebnisse** Fenster angezeigt wird, auch wenn es keine Ergebnisse enthält.

### <a name="to-view-code-metrics-details"></a>Um Code Metriken Details anzuzeigen.

Wenn Codemetrikergebnisse generiert wurden, erweitern Sie die Struktur in der **Hierarchie** Spalte.

## <a name="filtering-code-metrics-results"></a>Filtern von Codemetrikergebnissen

Sie können im angezeigten Ergebnisse filtern die **Codemetrikergebnisse** Fenster mithilfe der Symbolleiste am oberen. Sie möchten z. B. nur die Ergebnisse anzuzeigen, die einen Wartbarkeitsindex unter 65 aufweisen.

Die **Filter** Dropdown-Feld enthält die Namen der Ergebnisspalten. Wenn ein Filter definiert wird, wird es am Ende der Liste zusammen mit einem Einzug hinzugefügt. Die Liste kann die letzten zehn Filter enthalten, die definiert wurden.

### <a name="to-filter-the-code-metrics-results"></a>Zum Filtern der Codemetrikergebnisse

1.  Aus der **Filter** wählen Sie den Namen der Spalte.

2.  In **Min**, geben Sie den minimalen Wert angezeigt werden.

3.  In **Max**, geben Sie den maximalen Wert angezeigt werden.

4.  Klicken Sie auf die **Filter anwenden** Schaltfläche.

5.  Um die Ergebnisdetails anzuzeigen, erweitern Sie in der Hierarchiestruktur.

## <a name="adding-removing-and-rearranging-data-columns"></a>Hinzufügen, entfernen und Neuanordnen von Spalten

Sie können hinzufügen oder entfernen führt die Spalten aus der **Codemetrikergebnisse** Fenster. Darüber hinaus können Sie Ergebnisspalten neu anordnen, damit sie in der Reihenfolge angezeigt werden, die Sie möchten.

### <a name="to-remove-a-column"></a>So entfernen Sie eine Spalte

1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.

     \- mit der "oder" - Maustaste auf eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.

1. In der **Spalten hinzufügen/entfernen** Dialogfeld deaktivieren das Kontrollkästchen für die Spalte, die Sie entfernen möchten und klicken Sie dann auf **OK**.

### <a name="to-add-a-previously-removed-column"></a>Um eine zuvor entfernter Spalte hinzufügen

1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.

     \- oder –

     Maustaste auf eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.

1. In der **Spalten hinzufügen/entfernen** Dialogfeld Feld, das Kontrollkästchen für die Spalte, die Sie hinzufügen möchten und klicken Sie dann auf **OK**.

### <a name="to-rearrange-columns"></a>Um Spalten neu anzuordnen.

1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.

     \- oder –

     Maustaste auf eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.

1. In der **Spalten hinzufügen/entfernen** Dialogfeld wählen die Spalte, die Sie verschieben möchten und klicken Sie dann auf den Pfeil nach oben oder den Pfeil nach unten.

1. Wenn die Spalte an der gewünschten Position befindet, klicken Sie auf **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Kopieren von Daten in die Zwischenablage oder Excel

Sie können auswählen, und eine ausgewählte Zeile von Codemetrikdaten als Textzeichenfolge, die eine Zeile für den Namen und Wert der einzelnen Datenspalten enthält, in die Zwischenablage kopieren. Sie können auch klicken **Auswahl in Microsoft Excel öffnen** aller der Codemetrikergebnisse in eine Excel-Kalkulationstabelle exportieren.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Erstellen einer Arbeitsaufgabe anhand von Codemetrikergebnissen

Sie erstellen eine [Visual Studio Team Services (VSTS)](/vsts/index) führt zur Arbeitsaufgabe, die basierend auf der **Codemetrikergebnisse** Fenster. Wenn das Arbeitselement erstellt wurde, fügt Visual Studio automatisch einen Titel in die **Titel** Feld und Codemetrikdaten unter der **Verlauf** Registerkarte.

Weitere Informationen zur VSTS Typen von Arbeitsaufgaben, finden Sie unter [Typen von Arbeitsaufgaben (VSTS)](/vsts/work/work-items/index).

### <a name="to-create-a-work-item-based-on-a-result"></a>So erstellen eine Arbeitsaufgabe, die basierend auf ein Ergebnis

1.  Mit der rechten Maustaste in des Ergebnis.

2.  Zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ der Arbeitsaufgabe, die Sie erstellen möchten (**Fehler**, **Aufgabe**usw.).

3.  Führen Sie im Arbeitsaufgabenformular, indem alle erforderlichen Felder ausgefüllt.

4.  Auf der **Datei** Menü klicken Sie auf **alle speichern** zum Speichern der Arbeitsaufgabe.

### <a name="to-create-a-bug-based-on-a-result"></a>So erstellen Sie einen Fehler, die basierend auf ein Ergebnis

1.  Klicken Sie auf das Ergebnis aus, um ihn auszuwählen.

2.  Klicken Sie auf die **Arbeitsaufgabe erstellen** Schaltfläche.

3.  Führen Sie im Arbeitsaufgabenformular, indem alle erforderlichen Felder ausgefüllt.

4.  Auf der **Datei** Menü klicken Sie auf **alle speichern** zum Speichern der Arbeitsaufgabe.

## <a name="see-also"></a>Siehe auch

- [Codemetrikwerte](../code-quality/code-metrics-values.md)
- [Vorgehensweise: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)