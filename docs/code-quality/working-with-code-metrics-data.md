---
title: Arbeiten mit Codemetrikdaten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d45f5d43819dc418b6378d34a19e6af1d8ee12
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-code-metrics-data"></a>Arbeiten mit Codemetrikdaten
Die **Codemetrikergebnisse** Fenster zeigt die Daten, die von der Codeanalyse für die Metrik generiert werden. Weitere Informationen zu Daten für die codemetrikwerte, finden Sie unter [Codemetrikwerte](../code-quality/code-metrics-values.md).  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Anzeigen von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtern von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Hinzufügen, entfernen und Neuanordnen von Spalten](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Kopieren von Daten in die Zwischenablage oder Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Erstellen einer Arbeitsaufgabe anhand von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 Die **Codemetrikergebnisse** Fenster verfügt über eine Symbolleiste am oberen und Spalten, die die berechneten Ergebnisse angezeigt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Hierarchie**|Die **Hierarchie** Spalte enthält eine Strukturansicht der Codehierarchie, die erweitert oder reduziert werden, um die gewünschte Detailebene angezeigt werden kann. Die übrigen Spalten zeigen die berechneten Ergebnisse. Ordnen die Ergebnisspalten wie gewünscht oder ausblenden können.|  
|**Verwaltbarkeit**|Die **Verwaltbarkeit** Spalte enthält ein Symbol neben dem Ergebnis in numerischer Form. Ein grünes Symbol gibt an, einen relativ hohen Grad an Verwaltbarkeit. Ein gelbes Symbol weist ein Mittelschwerer Maß Verwaltbarkeit hin. Ein rotes Symbol gibt an, mit niedriger Verwaltbarkeit und eine potenzielle Probleme vor Ort. Diese Farbe Indikatoren entsprechen den von Schweregradkategorien, die von der FxCop-Regel AvoidUnmaintainableCode verwendet werden. Diese Regel wird einen Fehler ausgelöst, wenn der Wartbarkeitsindex kleiner als 10 ist eine Warnung ist, wenn der Index zwischen 10 und 20, und weder Fehler noch eine Warnung, ist wenn der Index größer als 20 ist. Der Wartbarkeitsindex ist eine Sprachsynthese drei Metriken: zyklomatische Komplexität, Codezeilen und Komplexität der Berechnung. Seine Werte werden in Einheiten nicht angegeben.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a>Anzeigen von Codemetrikergebnissen  
 Fenster Codemetrikergebnisse wird automatisch angezeigt, wenn Sie Codemetrikergebnisse generieren. Sie können auch das Fenster jederzeit anzeigen.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Zum Anzeigen des Fensters Codemetrikergebnisse  
  
-   Auf der **analysieren** Menü klicken Sie auf **Windows** , und klicken Sie dann auf **Codemetrikergebnisse**.  
  
     \- oder –  
  
-   Auf der **Ansicht** Sie im Menü **Weitere Fenster** , und klicken Sie dann auf **Codemetrikergebnisse**.  
  
     Das Fenster Codemetrikergebnisse wird angezeigt, selbst wenn es keine Ergebnisse enthält.  
  
#### <a name="to-view-code-metrics-details"></a>Um Code Metriken Details anzuzeigen.  
  
-   Wenn Codemetrikergebnisse generiert wurden, erweitern Sie die Struktur in der **Hierarchie** Spalte.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a>Filtern von Codemetrikergebnissen  
 Sie können im angezeigten Ergebnisse filtern die **Codemetrikergebnisse** Fenster mithilfe der Symbolleiste am oberen. Sie möchten z. B. nur die Ergebnisse anzuzeigen, die einen Wartbarkeitsindex unter 65 aufweisen.  
  
 Die **Filter** Dropdown-Feld enthält die Namen der Ergebnisspalten. Wenn ein Filter definiert wird, wird es am Ende der Liste zusammen mit einem Einzug hinzugefügt. Die Liste kann die letzten zehn Filter enthalten, die definiert wurden.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Zum Filtern der Codemetrikergebnisse  
  
1.  Aus der **Filter** wählen Sie den Namen der Spalte.  
  
2.  In **Min**, geben Sie den minimalen Wert angezeigt werden.  
  
3.  In **Max**, geben Sie den maximalen Wert angezeigt werden.  
  
4.  Klicken Sie auf die **Filter anwenden** Schaltfläche.  
  
5.  Um die Ergebnisdetails anzuzeigen, erweitern Sie in der Hierarchiestruktur.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Hinzufügen, entfernen und Neuanordnen von Spalten  
 Sie können hinzufügen oder entfernen führt die Spalten aus der **Codemetrikergebnisse** Fenster. Darüber hinaus können Sie Ergebnisspalten neu anordnen, damit sie in der Reihenfolge angezeigt werden, die Sie möchten.  
  
#### <a name="to-remove-a-column"></a>So entfernen Sie eine Spalte  
  
1.  Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.  
  
     \- oder –  
  
     Maustaste auf eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.  
  
2.  In der **Spalten hinzufügen/entfernen** Dialogfeld deaktivieren das Kontrollkästchen für die Spalte, die Sie entfernen möchten und klicken Sie dann auf **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Um eine zuvor entfernter Spalte hinzufügen  
  
1.  Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.  
  
     \- oder –  
  
     Maustaste auf eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.  
  
2.  In der **Spalten hinzufügen/entfernen** Dialogfeld Feld, das Kontrollkästchen für die Spalte, die Sie hinzufügen möchten und klicken Sie dann auf **OK**.  
  
#### <a name="to-rearrange-columns"></a>Um Spalten neu anzuordnen.  
  
1.  Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.  
  
     \- oder –  
  
     Maustaste auf eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.  
  
2.  In der **Spalten hinzufügen/entfernen** Dialogfeld wählen die Spalte, die Sie verschieben möchten und klicken Sie dann auf den Pfeil nach oben oder den Pfeil nach unten.  
  
3.  Wenn die Spalte an der gewünschten Position befindet, klicken Sie auf **OK**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Kopieren von Daten in die Zwischenablage oder Excel  
 Sie können auswählen, und eine ausgewählte Zeile von Codemetrikdaten als Textzeichenfolge, die eine Zeile für den Namen und Wert der einzelnen Datenspalten enthält, in die Zwischenablage kopieren. Sie können auch klicken **Liste in Microsoft Excel öffnen** aller der Codemetrikergebnisse in eine Excel-Kalkulationstabelle exportieren.  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Erstellen einer Arbeitsaufgabe anhand von Codemetrikergebnissen  
 Sie erstellen eine [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] führt zur Arbeitsaufgabe, die basierend auf der **Codemetrikergebnisse** Fenster. Wenn das Arbeitselement erstellt wird, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fügt automatisch einen Titel in die **Titel** Feld und Codemetrikdaten unter der **Verlauf** Registerkarte.  
  
 Weitere Informationen über das Erstellen von Arbeitselementen finden Sie unter [Erstellen einer Arbeitsaufgabe &#91; umgeleitet &#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>So erstellen eine Arbeitsaufgabe, die basierend auf ein Ergebnis  
  
1.  Mit der rechten Maustaste in des Ergebnis.  
  
2.  Zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ der Arbeitsaufgabe, die Sie erstellen möchten (**Fehler**, **Aufgabe**usw.).  
  
3.  Führen Sie im Arbeitsaufgabenformular, indem alle erforderlichen Felder ausgefüllt.  
  
4.  Auf der **Datei** Menü klicken Sie auf **alle speichern** zum Speichern der Arbeitsaufgabe.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>So erstellen Sie einen Fehler, die basierend auf ein Ergebnis  
  
1.  Klicken Sie auf das Ergebnis aus, um ihn auszuwählen.  
  
2.  Klicken Sie auf die **Arbeitsaufgabe erstellen** Schaltfläche.  
  
3.  Führen Sie im Arbeitsaufgabenformular, indem alle erforderlichen Felder ausgefüllt.  
  
4.  Auf der **Datei** Menü klicken Sie auf **alle speichern** zum Speichern der Arbeitsaufgabe.  
  
## <a name="see-also"></a>Siehe auch  
 [Messen von Komplexität und verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Gewusst wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)