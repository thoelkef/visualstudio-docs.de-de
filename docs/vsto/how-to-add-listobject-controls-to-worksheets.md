---
title: 'Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ce398f18913063d770aa180a06ff8e2017aebd86
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672672"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern
  Sie können hinzufügen <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelementen zu einem Microsoft Office Excel-Arbeitsblatt zur Entwurfszeit und zur Laufzeit in Projekten auf Dokumentebene.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können auch hinzufügen <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelementen zur Laufzeit in VSTO-Add-in-Projekte.  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Hinzufügen von ListObject-Steuerelementen zur Entwurfszeit](#designtime)  
  
-   [Hinzufügen von ListObject-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)  
  
-   [Hinzufügen von ListObject-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)  
  
 Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelemente finden Sie [ListObject-Steuerelement](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Hinzufügen von ListObject-Steuerelementen zur Entwurfszeit  
 Es gibt verschiedene Möglichkeiten zum Hinzufügen von <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelementen zur Entwurfszeit zu Arbeitsblättern in einem Projekt auf Dokumentebene: in Excel, über die **Toolbox**von Visual Studio oder im Fenster **Datenquellen** .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-use-the-ribbon-in-excel"></a>So verwenden Sie das Menüband in Excel  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Tabellen** auf **Tabelle**.  
  
2.  Wählen Sie die Zelle(n) aus, die Sie zur Liste hinzufügen möchten, und klicken Sie auf **OK**.  
  
#### <a name="to-use-the-toolbox"></a>So verwenden Sie die Toolbox  
  
1.  Ziehen Sie aus der Registerkarte **Excel-Steuerelemente** der **Toolbox**ein <xref:Microsoft.Office.Tools.Excel.ListObject> in das Arbeitsblatt.  
  
     Das Dialogfeld **ListObject-Steuerelement hinzufügen** wird angezeigt.  
  
2.  Wählen Sie die Zelle(n) aus, die Sie zur Liste hinzufügen möchten, und klicken Sie auf **OK**.  
  
     Wenn Sie nicht den Standardnamen beibehalten möchten, können Sie den Namen im Fenster **Eigenschaften** ändern.  
  
#### <a name="to-use-the-data-sources-window"></a>So verwenden Sie das Fenster „Datenquellen“  
  
1.  Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Datenquelle. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
2.  Ziehen Sie eine Tabelle aus dem Fenster **Datenquellen** in das Arbeitsblatt.  
  
     Ein datengebundenes <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement wird dem Arbeitsblatt hinzugefügt. Weitere Informationen finden Sie unter [Datenbindung und Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Hinzufügen von ListObject-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene  
 Sie können hinzufügen, die <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement dynamisch zur Laufzeit. So können Sie Hoststeuerelemente als Antwort auf Ereignisse erstellen. Dynamisch erstellte Listenobjekte werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein ListObject-Steuerelement programmgesteuert hinzu  
  
1.  Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> -Ereignishandler von `Sheet1`den folgenden Code hinzu, um ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement zu den Zellen **A1** bis **A4**hinzuzufügen:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Hinzufügen von ListObject-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt  
 Sie können ein <xref:Microsoft.Office.Tools.Excel.ListObject>-Steuerelement programmgesteuert jedem geöffneten Arbeitsblatt in einem VSTO-Add-In-Projekt hinzufügen. Dynamisch erstellte Listenobjekte werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt gespeichert und geschlossen wird. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein ListObject-Steuerelement programmgesteuert hinzu  
  
1.  Der folgende Code generiert ein Arbeitsblatthostelement, das auf dem geöffneten Arbeitsblatt basiert, und fügt dann ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement zu den Zellen **A1** bis **A4**hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Gewusst wie: Ändern der Größe ListObject-Steuerelementen](../vsto/how-to-resize-listobject-controls.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  