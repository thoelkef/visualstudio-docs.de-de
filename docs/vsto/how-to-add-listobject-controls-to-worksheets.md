---
title: "Gewusst wie: Hinzuf&#252;gen von ListObject-Steuerelementen zu Arbeitsbl&#228;ttern"
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
  - "ListObject-Steuerelement, Hinzufügen zu Arbeitsblättern"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Gewusst wie: Hinzuf&#252;gen von ListObject-Steuerelementen zu Arbeitsbl&#228;ttern
  Sie können <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelemente in einem Microsoft Office Excel\-Arbeitsblatt zur Entwurfszeit und zur Laufzeit in Projekten auf Dokumentebene hinzufügen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können auch <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelementen zur Laufzeit in VSTO\-Add\-In\-Projekte hinzufügen.  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Hinzufügen von ListObject\-Steuerelementen zur Entwurfszeit](#designtime)  
  
-   [Hinzufügen von ListObject\-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)  
  
-   [Hinzufügen von ListObject\-Steuerelementen zur Laufzeit in einem VSTO\-Add\-In\-Projekt](#runtimeaddin)  
  
 Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelementen finden Sie unter [ListObject-Steuerelement](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Hinzufügen von ListObject\-Steuerelementen zur Entwurfszeit  
 Es gibt verschiedene Möglichkeiten zum Hinzufügen von <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelementen zur Entwurfszeit zu Arbeitsblättern in einem Projekt auf Dokumentebene: in Excel, über die **Toolbox** von Visual Studio oder im Fenster **Datenquellen**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### So verwenden Sie das Menüband in Excel  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Tabellen** auf **Tabelle**.  
  
2.  Wählen Sie die Zelle\(n\) aus, die Sie zur Liste hinzufügen möchten, und klicken Sie auf **OK**.  
  
#### So verwenden Sie die Toolbox  
  
1.  Ziehen Sie aus der Registerkarte **Excel\-Steuerelemente** der **Toolbox** ein <xref:Microsoft.Office.Tools.Excel.ListObject> in das Arbeitsblatt.  
  
     Das Dialogfeld **ListObject\-Steuerelement hinzufügen** wird angezeigt.  
  
2.  Wählen Sie die Zelle\(n\) aus, die Sie zur Liste hinzufügen möchten, und klicken Sie auf **OK**.  
  
     Wenn Sie nicht den Standardnamen beibehalten möchten, können Sie den Namen im Fenster **Eigenschaften** ändern.  
  
#### So verwenden Sie das Fenster „Datenquellen“  
  
1.  Öffnen Sie das Fenster **Datenquellen**, und erstellen Sie für Ihr Projekt eine Datenquelle. Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
2.  Ziehen Sie eine Tabelle aus dem Fenster **Datenquellen** in das Arbeitsblatt.  
  
     Ein datengebundenes <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement wird dem Arbeitsblatt hinzugefügt. Weitere Informationen finden Sie unter [Datenbindung und Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
##  <a name="runtimedoclevel"></a> Hinzufügen von ListObject\-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene  
 Sie können das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement dynamisch zur Laufzeit hinzufügen. So können Sie Hoststeuerelemente als Antwort auf Ereignisse erstellen. Dynamisch erstellte Listenobjekte werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### So fügen Sie einem Arbeitsblatt ein ListObject\-Steuerelement programmgesteuert hinzu  
  
1.  Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignishandler von `Sheet1` den folgenden Code hinzu, um ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement zu den Zellen **A1** bis **A4** hinzuzufügen:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Hinzufügen von ListObject\-Steuerelementen zur Laufzeit in einem VSTO\-Add\-In\-Projekt  
 Sie können ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement programmgesteuert jedem geöffneten Arbeitsblatt in einem VSTO\-Add\-In\-Projekt hinzufügen. Dynamisch erstellte Listenobjekte werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt gespeichert und geschlossen wird. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### So fügen Sie einem Arbeitsblatt ein ListObject\-Steuerelement programmgesteuert hinzu  
  
1.  Der folgende Code generiert ein Arbeitsblatthostelement, das auf dem geöffneten Arbeitsblatt basiert, und fügt dann ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement zu den Zellen **A1** bis **A4** hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#8)]  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Gewusst wie: Ändern der Größe von ListObject-Steuerelementen](../vsto/how-to-resize-listobject-controls.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  