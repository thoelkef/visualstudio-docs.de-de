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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d4d206785991d37147d9d55d89947776a94b2ac4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111297"
---
# <a name="working-with-code-metrics-data"></a>Arbeiten mit Codemetrikdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **Codemetrikergebnisse** Fenster zeigt die Daten, die von der Codeanalyse für die Metrik generiert werden. Weitere Informationen zu Datenwerten der Codemetrik, finden Sie unter [Codemetrikwerte](../code-quality/code-metrics-values.md).  
  
 Dieses Thema enthält folgende Abschnitte:  
  
- [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
- [Anzeigen von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
- [Filtern von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
- [Hinzufügen, entfernen und Neuanordnen von Spalten](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
- [Kopieren von Daten in die Zwischenablage oder Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
- [Erstellen eines Arbeitselements anhand von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
## <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 Die **Codemetrikergebnisse** Fenster verfügt über eine Symbolleiste und die Spalten, die die berechneten Ergebnisse anzeigen.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Hierarchy**|Die **Hierarchie** Spalte enthält eine Strukturansicht der der Codehierarchie, die kann erweitert oder reduziert werden, um die gewünschte Detailebene angezeigt. Die übrigen Spalten enthalten die berechneten Ergebnisse. Sie können ordnen die Ergebnisspalten nach Ihren wünschen oder ausblenden.|  
|**Verwaltbarkeit**|Die **Verwaltbarkeit** Spalte enthält ein Symbol neben dem Ergebnis in numerischer Form. Ein grünes Symbol gibt an, ein relativ hohes Maß an Verwaltbarkeit. Ein gelbes Symbol gibt an, ein bestimmtes Maß an Verwaltbarkeit. Ein rotes Symbol weist geringe Verwaltbarkeit und potenzielle Fehler auf. Diese Farbe Indikatoren entsprechen Schweregradkategorien, die von der FxCop-Regel AvoidUnmaintainableCode verwendet werden. Diese Regel wird einen Fehler ausgelöst, wenn der Wartbarkeitsindex kleiner als 10, eine Warnung ist, wenn der Index zwischen 10 und 20, und weder Fehler noch eine Warnung, liegt Wenn der Index mehr als 20 ist. Der Wartbarkeitsindex ist einer Synthese von drei Metriken: zyklomatische Komplexität, Codezeilen, und Komplexität der Berechnung. Die Werte werden nicht in Einheiten ausgedrückt.|  
  
## <a name="BKMK_DisplayingCodeMetricsResults"></a> Anzeigen von Codemetrikergebnissen  
 Das Codemetrikergebnisse-Fenster wird automatisch angezeigt, beim Generieren von Codemetrikergebnissen. Sie können auch das Fenster jederzeit anzeigen.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Um das Fenster Codemetrikergebnisse anzuzeigen  
  
- Auf der **analysieren** Menü klicken Sie auf **Windows** , und klicken Sie dann auf **Codemetrikergebnisse**.  
  
     \- oder –  
  
- Auf der **Ansicht** Startmenü **andere Windows** , und klicken Sie dann auf **Codemetrikergebnisse**.  
  
     Der Codemetrikergebnisse-Fenster wird angezeigt, auch wenn es sich um keine Ergebnisse enthält.  
  
#### <a name="to-view-code-metrics-details"></a>Anzeigen von Details von basisanalysemetriken  
  
- Wenn Codemetrikergebnisse generiert wurden, erweitern Sie die Struktur in der **Hierarchie** Spalte.  
  
## <a name="BKMK_FilteringCodeMetricsResults"></a> Filtern von Codemetrikergebnissen  
 Sie können die Ergebnisse, die in angezeigt werden, Filtern die **Codemetrikergebnisse** Fenster mithilfe der Symbolleiste oben. Beispielsweise empfiehlt es sich um nur die Ergebnisse anzuzeigen, die einen Wartbarkeitsindex unter 65 haben.  
  
 Die **Filter** Dropdown-Feld enthält die Namen der Ergebnisspalten. Wenn ein Filter definiert wird, wird es am Ende der Liste zusammen mit einem Einzug hinzugefügt. Die Liste kann die letzten zehn Filter enthalten, die definiert wurden.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Zum Filtern der Codemetrikergebnisse  
  
1. Von der **Filter** wählen Sie den Namen der Spalte.  
  
2. In **Min**, geben Sie den minimalen Wert, der angezeigt werden.  
  
3. In **Max**, geben Sie den maximalen Wert angezeigt werden.  
  
4. Klicken Sie auf die **Filter anwenden** Schaltfläche.  
  
5. Um die Details der anzuzeigen, erweitern Sie in der Hierarchiestruktur.  
  
## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Hinzufügen, entfernen und Neuanordnen von Spalten  
 Sie können hinzufügen oder entfernen führt die Spalten aus der **Codemetrikergebnisse** Fenster. Darüber hinaus können Sie Ergebnisspalten neu anordnen, damit sie in der Reihenfolge angezeigt werden, die Sie möchten.  
  
#### <a name="to-remove-a-column"></a>Eine Spalte entfernen  
  
1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.  
  
     \- oder –  
  
     Mit der rechten Maustaste in eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.  
  
2. In der **Spalten hinzufügen/entfernen** Dialogfeld deaktivieren das Kontrollkästchen für die Spalte, die Sie entfernen möchten und klicken Sie dann auf **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Hinzufügen eine zuvor entfernte Spalte  
  
1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.  
  
     \- oder –  
  
     Mit der rechten Maustaste in eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.  
  
2. In der **Spalten hinzufügen/entfernen** Dialogfeld Feld, das Kontrollkästchen für die Spalte, die Sie hinzufügen möchten und klicken Sie dann auf **OK**.  
  
#### <a name="to-rearrange-columns"></a>Um Spalten neu anzuordnen.  
  
1. Klicken Sie auf die **Spalten hinzufügen/entfernen** Schaltfläche.  
  
     \- oder –  
  
     Mit der rechten Maustaste in eine beliebige Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen/entfernen**.  
  
2. In der **Spalten hinzufügen/entfernen** Dialogfeld wählen die Spalte, die Sie verschieben möchten und klicken Sie dann auf, entweder auf den Pfeil nach oben oder auf den Pfeil nach unten.  
  
3. Wenn die Spalte an der gewünschten Position befindet, klicken Sie auf **OK**.  
  
## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Kopieren von Daten in die Zwischenablage oder Excel  
 Sie können auswählen, und eine ausgewählte Zeile von Codemetrikdaten werden in die Zwischenablage kopieren, als eine Zeichenfolge, die eine Zeile für den Namen und den Wert der einzelnen Datenspalten enthält. Sie können auch klicken **Liste in Microsoft Excel öffnen** aller der Codemetrikergebnisse in einem Excel-Arbeitsblatt exportieren  
  
## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Erstellen eines Arbeitselements anhand von Codemetrikergebnissen  
 Sie erstellen eine [!INCLUDE[esprfound](../includes/esprfound-md.md)] führt zu Arbeitsaufgabe, die basierend auf der **Codemetrikergebnisse** Fenster. Wenn das Arbeitselement erstellt wird, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gibt automatisch einen Titel in der **Titel** Feld und die Codemetrikdaten werden unter der **Verlauf** Registerkarte.  
  
 Weitere Informationen zum Arbeitsaufgaben zu erstellen, finden Sie unter [Erstellen einer Arbeitsaufgabe &#91;umgeleitet&#93;](http://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Um eine Arbeitsaufgabe basierend auf ein Ergebnis zu erstellen.  
  
1. Mit der rechten Maustaste in des Ergebnis.  
  
2. Zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ des zu erstellenden Arbeitsaufgabe (**Fehler**, **Aufgabe**usw.).  
  
3. Führen Sie das arbeitselementformular, indem Sie alle erforderlichen Felder ausfüllen.  
  
4. Auf der **Datei** Menü klicken Sie auf **Alles speichern** zum Speichern des Arbeitselements.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>So erstellen Sie einen Fehler basierend auf ein Ergebnis  
  
1. Klicken Sie auf das Ergebnis, um es auszuwählen.  
  
2. Klicken Sie auf die **Arbeitselement erstellen** Schaltfläche.  
  
3. Führen Sie das arbeitselementformular, indem Sie alle erforderlichen Felder ausfüllen.  
  
4. Auf der **Datei** Menü klicken Sie auf **Alles speichern** zum Speichern des Arbeitselements.  
  
## <a name="see-also"></a>Siehe auch  
 [Messen von Komplexität und verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Vorgehensweise: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)
