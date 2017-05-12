---
title: "Gewusst wie: Hinzuf&#252;gen von Diagrammsteuerelementen zu Arbeitsbl&#228;ttern"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Chart-Steuerelement [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Gewusst wie: Hinzuf&#252;gen von Diagrammsteuerelementen zu Arbeitsbl&#228;ttern
  Sie können <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelemente in einem Microsoft Office Excel\-Arbeitsblatt zur Entwurfszeit und zur Laufzeit in Anpassungen auf Dokumentebene hinzufügen.  Sie können auch <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelementen zur Laufzeit in VSTO\-Add\-Ins hinzufügen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Hinzufügen von Chart\-Steuerelementen zur Entwurfszeit](#designtime)  
  
-   [Hinzufügen von Chart\-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)  
  
-   [Hinzufügen von Chart\-Steuerelementen zur Laufzeit in einem VSTO\-Add\-In\-Projekt](#runtimeaddin)  
  
 Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelementen finden Sie unter [Chart-Steuerelement](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Hinzufügen von Chart\-Steuerelementen zur Entwurfszeit  
 Sie können das <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelement Ihrem Arbeitsblatt auf die gleiche Weise wie ein Diagramm innerhalb der Anwendung hinzufügen.  
  
> [!NOTE]  
>  Das <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelement ist über die **Toolbox** oder das Fenster **Datenquellen** nicht verfügbar.  
  
#### So fügen Sie einem Arbeitsblatt in Excel ein Chart\-Hoststeuerelement hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** der Gruppe **Diagramme** auf **Spalte**, klicken Sie auf eine Diagrammkategorie, und klicken Sie dann auf den Typ des gewünschten Diagramms.  
  
2.  Klicken Sie im Dialogfeld **Diagramm einfügen** auf **OK**.  
  
3.  Klicken Sie auf der Registerkarte **Entwurf** in der Gruppe **Daten** auf **Daten auswählen**.  
  
4.  Klicken Sie im Dialogfeld **Datenquelle auswählen**  im Feld **Diagrammdatenbereich**, und deaktivieren Sie die Standardauswahl.  
  
5.  Wählen Sie auf dem Blatt **Daten für Diagramm** den Zellbereich aus, der Daten für das Diagramm enthält \(Zellen **A5** bis **D8**\).  
  
6.  Klicken Sie im Dialogfeld **Datenquelle auswählen** auf **OK**.  
  
##  <a name="runtimedoclevel"></a> Hinzufügen von Chart\-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene  
 Sie können das <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelement dynamisch zur Laufzeit hinzufügen.  Dynamisch erstellte Diagramme werden nicht im Dokument wie Hoststeuerelemente dauerhaft gespeichert, wenn das Dokument geschlossen wird.  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### So fügen Sie einem Arbeitsblatt ein Chart\-Steuerelement programmgesteuert hinzu  
  
1.  Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignishandler von `Sheet1` den folgenden Code hinzu, um das <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelement hinzuzufügen:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Hinzufügen von Chart\-Steuerelementen zur Laufzeit in einem VSTO\-Add\-In\-Projekt  
 Sie können ein <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelement programmgesteuert jedem geöffneten Arbeitsblatt in einem VSTO\-Add\-In\-Projekt hinzufügen.  Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Dynamisch erstellte Chart\-Steuerelemente werden nicht im Arbeitsblatt wie Hoststeuerelemente dauerhaft gespeichert, wenn das Arbeitsblatt geschlossen wird.  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### So fügen Sie einem Arbeitsblatt ein Chart\-Steuerelement programmgesteuert hinzu  
  
1.  Der folgende Code generiert ein Arbeitsblatt\-Hostelement, das auf dem geöffneten Arbeitsblatt basiert, und fügt dann ein <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelement hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#9)]  
  
## Kompilieren des Codes  
 Für dieses Beispiel gelten die folgenden Anforderungen:  
  
-   Die Daten für das Diagramm sind im Bereich von A5 bis D8 im Arbeitsblatt gespeichert.  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Chart-Steuerelement](../vsto/chart-control.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  