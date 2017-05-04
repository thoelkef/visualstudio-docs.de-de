---
title: "Gewusst wie: Hinzuf&#252;gen von NamedRange-Steuerelementen zu Arbeitsbl&#228;ttern | Microsoft Docs"
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
  - "Bereiche, Hinzufügen zu Arbeitsblättern"
  - "NamedRange-Steuerelement, Hinzufügen zu Arbeitsblättern"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Gewusst wie: Hinzuf&#252;gen von NamedRange-Steuerelementen zu Arbeitsbl&#228;ttern
  Sie können <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelemente in einem Microsoft Office Excel\-Arbeitsblatt zur Entwurfszeit und zur Laufzeit in Projekten auf Dokumentebene hinzufügen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können auch <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelemente zur Laufzeit in VSTO\-Add\-In\-Projekten hinzufügen.  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Hinzufügen von NamedRange\-Steuerelementen zur Entwurfszeit](#designtime)  
  
-   [Hinzufügen von NamedRange\-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)  
  
-   [Hinzufügen von NamedRange\-Steuerelementen zur Laufzeit in einem VSTO\-Add\-In\-Projekt](#runtimeaddin)  
  
 Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelementen finden Sie unter [NamedRange-Steuerelement](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Hinzufügen von NamedRange\-Steuerelementen zur Entwurfszeit  
 Es gibt verschiedene Möglichkeiten zum Hinzufügen von <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelementen zur Entwurfszeit zu Arbeitsblättern in einem Projekt auf Dokumentebene: in Excel, über die **Toolbox** von Visual Studio oder im Fenster **Datenquellen**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### So fügen Sie ein NamedRange\-Steuerelement mit dem Feld „Name“ zu einem Arbeitsblatt in Excel hinzu  
  
1.  Wählen Sie die Zelle oder die Zellen aus, die Sie in den benannten Bereich einbinden möchten.  
  
2.  Geben Sie im **Namenfeld** einen Namen für den Bereich ein, und drücken Sie die EINGABETASTE.  
  
     Das **Namenfeld** befindet sich neben der Bearbeitungsleiste genau über Spalte **A** des Arbeitsblatts.  
  
#### So fügen Sie ein NamedRange\-Steuerelement mit der Toolbox zu einem Arbeitsblatt hinzu  
  
1.  Öffnen Sie die **Toolbox**, und klicken Sie auf die Registerkarte **Excel\-Steuerelemente**.  
  
2.  Klicken Sie auf <xref:Microsoft.Office.Tools.Excel.NamedRange>, und ziehen Sie es in ein Arbeitsblatt.  
  
     Das Dialogfeld **Benannten Bereich hinzufügen** wird angezeigt.  
  
3.  Wählen Sie die Zelle oder die Zellen aus, die Sie in den benannten Bereich einbinden möchten.  
  
4.  Klicken Sie auf **OK**.  
  
     Wenn Sie nicht den Standardnamen für das Steuerelement verwenden möchten, können Sie den Namen im **Eigenschaftenfenster** ändern.  
  
#### So fügen Sie ein NamedRange\-Steuerelement über das Fenster „Datenquellen“ zu einem Arbeitsblatt hinzu  
  
1.  Öffnen Sie das Fenster **Datenquellen**, und erstellen Sie für Ihr Projekt eine Datenquelle. Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
2.  Ziehen Sie ein einzelnes Feld aus dem Fenster **Datenquellen** in das Arbeitsblatt.  
  
     Ein datengebundenes <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement wird dem Arbeitsblatt hinzugefügt. Weitere Informationen finden Sie unter [Datenbindung und Windows Forms](../Topic/Data%20Binding%20and%20Windows%20Forms.md).  
  
##  <a name="runtimedoclevel"></a> Hinzufügen von NamedRange\-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene  
 Sie können ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement programmgesteuert zur Laufzeit zum Arbeitsblatt hinzufügen. So können Sie Hoststeuerelemente als Antwort auf Ereignisse erstellen. Dynamisch erstellte benannte Bereiche werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### So fügen Sie einem Arbeitsblatt ein NamedRange\-Steuerelement programmgesteuert hinzu  
  
1.  Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignishandler von `Sheet1` den folgenden Code hinzu, um das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement zu Zelle **A1** hinzuzufügen, und legen Sie dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>\-Eigenschaft auf `Hello world!` fest.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Hinzufügen von NamedRange\-Steuerelementen zur Laufzeit in einem VSTO\-Add\-In\-Projekt  
 Sie können ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement programmgesteuert jedem geöffneten Arbeitsblatt in einem VSTO\-Add\-In\-Projekt hinzufügen. Dynamisch erstellte benannte Bereiche werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### So fügen Sie einem Arbeitsblatt ein NamedRange\-Steuerelement programmgesteuert hinzu  
  
1.  Der folgende Code generiert ein Arbeitsblatthostelement, das auf dem geöffneten Arbeitsblatt basiert, und fügt dann ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement zur Zelle **A1** hinzu, und legen Sie dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>\-Eigenschaft auf `Hello world` fest.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#7)]  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Gewusst wie: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  