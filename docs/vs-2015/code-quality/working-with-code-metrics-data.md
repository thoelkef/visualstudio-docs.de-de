---
title: Arbeiten mit Codemetrikdaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645703"
---
# <a name="working-with-code-metrics-data"></a>Arbeiten mit Codemetrikdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Fenster **Code Metrikergebnisse** werden die Daten angezeigt, die von der Codemetrikanalyse generiert werden. Weitere Informationen zu den Datenwerten von Codemetriken finden Sie unter [codemetrikwerte](../code-quality/code-metrics-values.md).

 Dieses Thema enthält folgende Abschnitte:

- [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [Anzeigen von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [Filtern von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [Hinzufügen, entfernen und Neuanordnen von Datenspalten](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [Kopieren von Daten in die Zwischenablage oder Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [Erstellen eines Arbeits Elements basierend auf Code metrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window
 Das Fenster **Code Metrikergebnisse** enthält eine Symbolleiste am oberen Rand und die Spalten, um die berechneten Ergebnisse anzuzeigen.

|Spalte|Beschreibung|
|------------|-----------------|
|**Hier**|Die Spalte **Hierarchie** enthält eine Strukturansicht der Code Hierarchie, die Sie erweitern oder reduzieren können, um den gewünschten Detailgrad anzuzeigen. In den restlichen Spalten werden die berechneten Ergebnisse angezeigt. Sie können die Ergebnis Spalten beliebig ausblenden oder anordnen.|
|**Verwaltbarkeit**|Die **wart barkeits** Spalte enthält neben dem numerischen Ergebnis ein Symbol. Ein grünes Symbol weist auf ein relativ hohes Maß an Wartbarkeit hin. Ein gelbes Symbol weist auf einen mittleren Grad der Wartbarkeit hin. Ein rotes Symbol weist auf eine geringe Wartbarkeit und einen potenziellen Fehler hin. Diese Farbindikatoren entsprechen den Schweregraden, die von der FxCop-Regel "vermeidunwart Code" verwendet werden. Diese Regel löst einen Fehler aus, wenn der verwaltbarkeitsindex niedriger als 10 ist, eine Warnung, wenn der Index zwischen 10 und 20 liegt, und weder ein Fehler noch eine Warnung, wenn der Index größer als 20 ist. Der Wartbarkeitsindex ist eine Synthese aus drei Metriken: zyklomatische Komplexität, Codezeilen und Berechnungs Komplexität. Seine Werte werden nicht in Einheiten ausgedrückt.|

## <a name="BKMK_DisplayingCodeMetricsResults"></a>Anzeigen von Codemetrikergebnissen
 Das Fenster Code Metrikergebnisse wird automatisch angezeigt, wenn Sie Code Metrikergebnisse generieren. Sie können das Fenster auch jederzeit anzeigen.

#### <a name="to-display-the-code-metrics-results-window"></a>So zeigen Sie das Fenster "Code Metrikergebnisse" an

- Klicken Sie im Menü **analysieren** auf **Fenster** , und klicken Sie dann auf **Codemetrikergebnisse**.

     \- oder -

- Zeigen Sie im Menü **Ansicht** auf **Weitere Fenster** , und klicken Sie dann auf **Codemetrikergebnisse**.

     Das Fenster Code Metrikergebnisse wird auch dann angezeigt, wenn es keine Ergebnisse enthält.

#### <a name="to-view-code-metrics-details"></a>So zeigen Sie Code metrikdetails an

- Wenn Codemetrikergebnisse generiert wurden, erweitern Sie die Struktur in der **Hierarchie** Spalte.

## <a name="BKMK_FilteringCodeMetricsResults"></a>Filtern von Codemetrikergebnissen
 Sie können die Ergebnisse filtern, die im Fenster **Code Metrikergebnisse** angezeigt werden, indem Sie die Symbolleiste oben verwenden. Beispielsweise möchten Sie möglicherweise nur die Ergebnisse sehen, die einen verwaltbarkeitsindex unter 65 aufweisen.

 Das Dropdown Feld **Filter** enthält die Namen der Ergebnis Spalten. Wenn ein Filter definiert ist, wird er am Ende der Liste zusammen mit einem Einzug hinzugefügt. Die Liste kann die letzten zehn Filter enthalten, die definiert wurden.

#### <a name="to-filter-the-code-metrics-results"></a>So filtern Sie die Codemetrikergebnisse

1. Wählen Sie in der Liste **Filter** den Spaltennamen aus.

2. Geben Sie in **Min**den minimalen Wert ein, der angezeigt werden soll.

3. Geben Sie in **Max**den Maximalwert ein, der angezeigt werden soll.

4. Klicken Sie auf die Schaltfläche **Filter anwenden** .

5. Um die Ergebnis Details anzuzeigen, erweitern Sie die Hierarchiestruktur.

## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Hinzufügen, entfernen und Neuanordnen von Datenspalten
 Sie können Ergebnis Spalten im Fenster **Code Metrikergebnisse** hinzufügen oder entfernen. Außerdem können Sie Ergebnis Spalten neu anordnen, sodass Sie in der gewünschten Reihenfolge angezeigt werden.

#### <a name="to-remove-a-column"></a>So entfernen Sie eine Spalte

1. Klicken Sie auf die Schaltfläche **Spalten hinzufügen/entfernen** .

     \- oder -

     Klicken Sie mit der rechten Maustaste auf eine beliebige Spaltenüberschrift und dann auf **Spalten hinzufügen/entfernen**

2. Deaktivieren Sie im Dialogfeld **Spalten hinzufügen/entfernen** das Kontrollkästchen für die Spalte, die Sie entfernen möchten, und klicken Sie dann auf **OK**.

#### <a name="to-add-a-previously-removed-column"></a>So fügen Sie eine zuvor entfernte Spalte hinzu

1. Klicken Sie auf die Schaltfläche **Spalten hinzufügen/entfernen** .

     \- oder -

     Klicken Sie mit der rechten Maustaste auf eine beliebige Spaltenüberschrift und dann auf **Spalten hinzufügen/entfernen**

2. Aktivieren Sie im Dialogfeld **Spalten hinzufügen/entfernen** das Kontrollkästchen für die Spalte, die Sie hinzufügen möchten, und klicken Sie dann auf **OK**.

#### <a name="to-rearrange-columns"></a>So ordnen Sie Spalten neu an

1. Klicken Sie auf die Schaltfläche **Spalten hinzufügen/entfernen** .

     \- oder -

     Klicken Sie mit der rechten Maustaste auf eine beliebige Spaltenüberschrift und dann auf **Spalten hinzufügen/entfernen**

2. Wählen Sie im Dialogfeld **Spalten hinzufügen/entfernen** die Spalte aus, die Sie verschieben möchten, und klicken Sie dann entweder auf den Pfeil nach oben oder den Pfeil nach unten.

3. Wenn die Spalte an der gewünschten Position positioniert ist, klicken Sie auf **OK**.

## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Kopieren von Daten in die Zwischenablage oder Excel
 Sie können eine ausgewählte Zeile mit Codemetrikdaten auswählen und als Text Zeichenfolge in die Zwischenablage kopieren, die eine Zeile für den Namen und den Wert jeder Datenspalte enthält. Sie können auch auf **Liste in Microsoft Excel öffnen** klicken, um alle Code Metrikergebnisse in eine Excel-Kalkulations Tabelle zu exportieren.

## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Erstellen eines Arbeits Elements basierend auf Code metrikergebnissen
 Sie können ein [!INCLUDE[esprfound](../includes/esprfound-md.md)] Arbeits Element erstellen, das auf Ergebnissen im Fenster " **Code Metrikergebnisse** " basiert. Wenn das Arbeits Element erstellt wird, werden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatisch einen Titel im **Titelfeld** eingeben und Metrikdaten auf der Registerkarte **Verlauf** codieren.

 Weitere Informationen zum Erstellen von Arbeits Elementen finden Sie unter [Erstellen eines umgeleiteten &#91;&#93;Arbeits Elements](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).

#### <a name="to-create-a-work-item-based-on-a-result"></a>So erstellen Sie ein Arbeits Element basierend auf einem Ergebnis

1. Klicken Sie mit der rechten Maustaste auf das Ergebnis.

2. Zeigen Sie auf **Arbeits Element erstellen**, und klicken Sie dann auf den Typ des Arbeits Elements, das Sie erstellen möchten (**Fehler**, **Aufgabe**usw.).

3. Vervollständigen Sie das Arbeits Element Formular, indem Sie alle erforderlichen Felder ausfüllen.

4. Klicken Sie im Menü **Datei** auf **Alle speichern** , um das Arbeits Element zu speichern.

#### <a name="to-create-a-bug-based-on-a-result"></a>So erstellen Sie einen Fehler basierend auf einem Ergebnis

1. Klicken Sie auf das Ergebnis, um es auszuwählen.

2. Klicken Sie auf die Schaltfläche **Arbeitsaufgabe erstellen** .

3. Vervollständigen Sie das Arbeits Element Formular, indem Sie alle erforderlichen Felder ausfüllen.

4. Klicken Sie im Menü **Datei** auf **Alle speichern** , um das Arbeits Element zu speichern.

## <a name="see-also"></a>Siehe auch
 [Messen von Komplexität und Verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Gewusst [wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)
