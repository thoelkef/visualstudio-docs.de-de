---
title: "Arbeiten mit Codemetrikdaten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codemetrics.output"
helpviewer_keywords: 
  - "Codemetrikergebnisse"
  - "Codemetrikergebnisfenster"
  - "Ergebnisfenster, Codemetrik"
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 17
caps.handback.revision: 17
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Arbeiten mit Codemetrikdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Fenster **Codemetrikergebnisse** zeigt die Daten an, die von der Codemetrikanalyse generiert werden.  Weitere Informationen zu Datenwerten der Codemetrik finden Sie unter [Codemetrikwerte](../code-quality/code-metrics-values.md).  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Fenster Codemetrikergebnisse](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Anzeigen von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtern von Codemetrikergebnissen](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Hinzufügen, Entfernen und Neuanordnen von Datenspalten](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Kopieren von Daten in die Zwischenablage oder in Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Erstellen einer Arbeitsaufgabe auf Basis Codemetrik-Ergebnisse](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Fenster Codemetrikergebnisse  
 Das Fenster **Codemetrikergebnisse** zeigt oben eine Symbolleiste sowie Spalten, in denen die berechneten Ergebnisse angezeigt werden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Hierarchie**|In der Spalte **Hierarchie** wird eine Strukturansicht der Codehierarchie angezeigt, die Sie je nach gewünschter Detailebene erweitern oder reduzieren können.  In den übrigen Spalten werden die berechneten Ergebnisse angezeigt.  Sie können die Ergebnisspalten beliebig ausblenden oder anordnen.|  
|**Einfache Verwaltung**|Die Spalte **Verwaltbarkeit** enthält zusätzlich zum numerischen Ergebnis ein Symbol.  Ein grünes Symbol weist auf einen relativ hohen Grad an Verwaltbarkeit hin.  Ein gelbes Symbol gibt eine mäßige Verwaltbarkeit an.  Ein rotes Symbol deutet auf geringe Verwaltbarkeit und potenzielle Problemstellen hin.  Diese Farbindikatoren entsprechen Schweregradkategorien, die von der FxCop\-Regel AvoidUnmaintainableCode verwendet werden.  Diese Regel löst einen Fehler aus, wenn der Wartbarkeitsindex niedriger als 10 ist, eine Warnung, wenn der Index zwischen 10 und 20 ist, und weder einen Fehler noch eine Warnung, wenn der Index höher als 20 ist.  Der Wartbarkeitsindex ist eine Synthese aus drei Metriken: zyklomatische Komplexität, Codezeilen und Rechenkomplexität.  Die Werte werden nicht in Einheiten ausgedrückt.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a> Anzeigen von Codemetrikergebnissen  
 Das Fenster Codemetrikergebnisse wird automatisch angezeigt, wenn Sie Codemetrikergebnisse generieren.  Sie können das Fenster auch jederzeit selbst aufrufen.  
  
#### So zeigen Sie das Fenster Codemetrikergebnisse an  
  
-   Klicken Sie im Menü **Analyse**  auf **Fenster**  und dann auf **Codemetrikergebnisse**.  
  
     – oder –  
  
-   Zeigen Sie im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **Codemetrikergebnisse**.  
  
     Das Fenster Codemetrikergebnisse wird angezeigt, auch wenn es keine Ergebnisse enthält.  
  
#### So zeigen Sie Codemetrikdetails an  
  
-   Erweitern Sie die Struktur in der Spalte **Hierarchie**, falls Codemetrikergebnisse generiert wurden.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a> Filtern von Codemetrikergebnissen  
 Mithilfe der Symbolleiste im oberen Bereich können Sie die im Fenster **Codemetrikergebnisse** angezeigten Ergebnisse filtern.  Beispielsweise können Sie nur die Ergebnisse mit einem Wartbarkeitsindex unter 65 anzeigen.  
  
 Das Dropdownfeld **Filter** enthält die Namen der Ergebnisspalten.  Wenn ein Filter definiert wird, wird er mit einem Einzug versehen und am Ende der Liste eingefügt.  Die Liste kann die letzten zehn definierten Filter enthalten.  
  
#### So filtern Sie die Codemetrikergebnisse  
  
1.  Wählen Sie aus der Liste **Filter** den Spaltennamen aus.  
  
2.  Geben Sie unter **Min.** den Mindestwert ein, der angezeigt werden soll.  
  
3.  Geben Sie unter **Max.** den Maximalwert ein, der angezeigt werden soll.  
  
4.  Klicken Sie auf die Schaltfläche **Filter anwenden**.  
  
5.  Um die Ergebnisdetails anzuzeigen, erweitern Sie die Hierarchiestruktur.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Hinzufügen, Entfernen und Neuanordnen von Datenspalten  
 Sie können Ergebnisspalten im Fenster **Codemetrikergebnisse** entfernen und hinzufügen.  Außerdem können Sie Ergebnisspalten neu anordnen, damit sie in der gewünschten Reihenfolge angezeigt werden.  
  
#### So entfernen Sie eine Spalte  
  
1.  Klicken Sie auf die Schaltfläche **Spalten hinzufügen\/entfernen**.  
  
     – oder –  
  
     Klicken Sie mit der rechten Maustaste auf eine Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen\/entfernen**.  
  
2.  Deaktivieren Sie im Dialogfeld **Spalten hinzufügen\/entfernen** das Kontrollkästchen der Spalte, die entfernt werden soll, und klicken Sie dann auf **OK**.  
  
#### So fügen Sie eine zuvor entfernte Spalte hinzu  
  
1.  Klicken Sie auf die Schaltfläche **Spalten hinzufügen\/entfernen**.  
  
     – oder –  
  
     Klicken Sie mit der rechten Maustaste auf eine Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen\/entfernen**.  
  
2.  Aktivieren Sie im Dialogfeld **Spalten hinzufügen\/entfernen** das Kontrollkästchen der Spalte, die hinzugefügt werden soll, und klicken Sie dann auf **OK**.  
  
#### So ordnen Sie Spalten neu an  
  
1.  Klicken Sie auf die Schaltfläche **Spalten hinzufügen\/entfernen**.  
  
     – oder –  
  
     Klicken Sie mit der rechten Maustaste auf eine Spaltenüberschrift, und klicken Sie dann auf **Spalten hinzufügen\/entfernen**.  
  
2.  Wählen Sie im Dialogfeld **Spalten hinzufügen\/entfernen** die Spalte aus, die verschoben werden soll, und klicken Sie anschließend auf den Aufwärtspfeil oder den Abwärtspfeil.  
  
3.  Sobald sich die Spalte an der gewünschten Position befindet, klicken Sie auf **OK**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Kopieren von Daten in die Zwischenablage oder in Excel  
 Sie können eine ausgewählte Zeile von Codemetrikdaten die Zwischenablage als Textzeichenfolge auswählen und kopieren, die eine Zeile für den Namen und Wert jeder Datenspalte.  Sie können auch auf **Liste in Microsoft Excel öffnen** klicken, um alle Codemetrikergebnisse in einem Excel\-Arbeitsblatt zu exportieren  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Erstellen einer Arbeitsaufgabe auf Basis Codemetrik\-Ergebnisse  
 Sie können eine [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] \- Arbeitsaufgabe erstellen, die auf Ergebnissen im Fenster **Codemetrikergebnisse** ist.  Wenn die Arbeitsaufgabe erstellt wird, gibt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatisch ein Titel im Feld **Titel** und die Codemetrikdaten werden in die Registerkarte **Verlauf** ein.  
  
 Weitere Informationen zum Erstellen von Arbeitsaufgaben finden Sie unter [Create a work item &#91;redirected&#93;](http://msdn.microsoft.com/de-de/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### So erstellen Sie eine Arbeitsaufgabe auf der Grundlage eines Ergebnisses  
  
1.  Klicken Sie mit der rechten Maustaste auf das Ergebnis.  
  
2.  Zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie auf den Typ der zu erstellenden Arbeitsaufgabe \(**Fehler**, **Aufgabe** usw.\).  
  
3.  Füllen Sie das Arbeitsaufgabenformular aus, indem Sie alle Pflichtfelder ausfüllen.  
  
4.  Klicken Sie im Menü **Datei** auf **Alle speichern**, um die Arbeitsaufgabe zu speichern.  
  
#### So erstellen Sie einen Fehler auf der Grundlage eines Ergebnisses  
  
1.  Klicken Sie auf das Ergebnis, um es auszuwählen.  
  
2.  Klicken Sie auf die Schaltfläche **Arbeitsaufgabe erstellen**.  
  
3.  Füllen Sie das Arbeitsaufgabenformular aus, indem Sie alle Pflichtfelder ausfüllen.  
  
4.  Klicken Sie im Menü **Datei** auf **Alle speichern**, um die Arbeitsaufgabe zu speichern.  
  
## Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Gewusst wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)