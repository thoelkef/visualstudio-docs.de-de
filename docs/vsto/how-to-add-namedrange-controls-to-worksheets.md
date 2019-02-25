---
title: 'Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee3e0b6f06e25fdefbcf6decdd64c5de7cd94273
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597581"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern
  Sie können hinzufügen <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelementen zu einem Microsoft Office Excel-Arbeitsblatt zur Entwurfszeit und zur Laufzeit in Projekten auf Dokumentebene.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Sie können auch hinzufügen <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelementen zur Laufzeit in VSTO-Add-in-Projekte.

 In diesem Thema werden die folgenden Aufgaben beschrieben:

- [Hinzufügen von NamedRange-Steuerelementen zur Entwurfszeit](#designtime)

- [Hinzufügen von NamedRange-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)

- [Hinzufügen von NamedRange-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)

  Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelemente finden Sie [NamedRange-Steuerelement](../vsto/namedrange-control.md).

##  <a name="designtime"></a> Hinzufügen von NamedRange-Steuerelementen zur Entwurfszeit
 Es gibt verschiedene Möglichkeiten zum Hinzufügen von <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelementen zur Entwurfszeit zu Arbeitsblättern in einem Projekt auf Dokumentebene: in Excel, über die **Toolbox**von Visual Studio oder im Fenster **Datenquellen** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>So fügen Sie ein NamedRange-Steuerelement mit dem Feld „Name“ zu einem Arbeitsblatt in Excel hinzu

1.  Wählen Sie die Zelle oder die Zellen aus, die Sie in den benannten Bereich einbinden möchten.

2.  In der **Namenfeld**, geben Sie einen Namen für den Bereich, und drücken Sie **EINGABETASTE**.

     Das **Namenfeld** befindet sich neben der Bearbeitungsleiste genau über Spalte **A** des Arbeitsblatts.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>So fügen Sie ein NamedRange-Steuerelement mit der Toolbox zu einem Arbeitsblatt hinzu

1.  Öffnen Sie die **Toolbox** , und klicken Sie auf die Registerkarte **Excel-Steuerelemente** .

2.  Klicken Sie auf <xref:Microsoft.Office.Tools.Excel.NamedRange> , und ziehen Sie es in ein Arbeitsblatt.

     Das Dialogfeld **Benannten Bereich hinzufügen** wird angezeigt.

3.  Wählen Sie die Zelle oder die Zellen aus, die Sie in den benannten Bereich einbinden möchten.

4.  Klicken Sie auf **OK**.

     Wenn Sie nicht den Standardnamen für das Steuerelement verwenden möchten, können Sie den Namen im **Eigenschaftenfenster** ändern.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>So fügen Sie ein NamedRange-Steuerelement über das Fenster „Datenquellen“ zu einem Arbeitsblatt hinzu

1.  Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Datenquelle. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

2.  Ziehen Sie ein einzelnes Feld aus dem Fenster **Datenquellen** in das Arbeitsblatt.

     Ein datengebundenes <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement wird dem Arbeitsblatt hinzugefügt. Weitere Informationen finden Sie unter [Datenbindung und Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

##  <a name="runtimedoclevel"></a> Hinzufügen von NamedRange-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene
 Sie können Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement programmgesteuert in das Arbeitsblatt zur Laufzeit. So können Sie Hoststeuerelemente als Antwort auf Ereignisse erstellen. Dynamisch erstellte benannte Bereiche werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein NamedRange-Steuerelement programmgesteuert hinzu

1.  Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> -Ereignishandler von `Sheet1`den folgenden Code hinzu, um das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zu Zelle **A1** hinzuzufügen, und legen Sie dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft auf `Hello world!`fest.

     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]

##  <a name="runtimeaddin"></a> Hinzufügen von NamedRange-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt
 Sie können ein <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelement programmgesteuert jedem geöffneten Arbeitsblatt in einem VSTO-Add-In-Projekt hinzufügen. Dynamisch erstellte benannte Bereiche werden im Arbeitsblatt nicht dauerhaft als Hoststeuerelemente gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein NamedRange-Steuerelement programmgesteuert hinzu

1.  Der folgende Code generiert ein Arbeitsblatthostelement, das auf dem geöffneten Arbeitsblatt basiert, und fügt dann ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **A1** hinzu, und legen Sie dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft auf `Hello world`fest.

     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]

## <a name="see-also"></a>Siehe auch
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [NamedRange-Steuerelement](../vsto/namedrange-control.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Vorgehensweise: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
