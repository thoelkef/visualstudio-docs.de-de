---
title: 'Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in VSTO-add-in-Projekt'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c6f972f2daa734bbabcea39ada9270acb7644db6
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767334"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-runtime-in-vsto-add-in-project"></a>Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in VSTO-add-in-Projekt
  Sie können einem beliebigen geöffneten Arbeitblatt Steuerelemente mithilfe eines Excel-VSTO-Add-In hinzufügen. Diese exemplarische Vorgehensweise veranschaulicht, wie Benutzer einem Arbeitsblatt mithilfe des Menübands ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> und <xref:Microsoft.Office.Tools.Excel.ListObject> hinzufügen können. Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Gilt für:** die Informationen in diesem Thema betreffen VSTO-Add-in-Projekte für Excel. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Bereitstellen einer Benutzeroberfläche (UI) zum Hinzufügen von Steuerelementen zum Arbeitsblatt  
  
-   Hinzufügen von Steuerelementen zum Arbeitsblatt  
  
-   Entfernen von Steuerelementen aus dem Arbeitsblatt  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="create-a-new-excel-vsto-add-in-project"></a>Erstellen eines neuen Excel-VSTO-Add-in-Projekts  
 Beginnen Sie mit der Erstellung eines Excel VSTO-Add-In-Projekts.  
  
### <a name="to-create-a-new-excel-vsto-add-in-project"></a>So erstellen Sie ein neues Excel-VSTO-Add-In-Projekt  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], erstellen Sie ein Excel-VSTO-Add-in-Projekt mit dem Namen **"ExcelDynamicControls"**. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Hinzufügen eines Verweises auf die **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** Assembly. Dieser Verweis ist erforderlich, um einem Arbeitsblatt ein Windows Forms-Steuerelement in dieser exemplarischen Vorgehensweise später programmgesteuert hinzuzufügen.  
  
## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Geben Sie eine Benutzeroberfläche zum Hinzufügen von Steuerelementen zu einem Arbeitsblatt  
 Fügen Sie dem Excel-Menüband eine benutzerdefinierte Registerkarte hinzu. Benutzer können Kontrollkästchen auf der Registerkarte aktivieren, um einem Arbeitsblatt Steuerelemente hinzuzufügen.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>So stellen Sie eine Benutzeroberfläche zum Hinzufügen von Steuerelementen zu einem Arbeitsblatt bereit  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Menüband (visueller Designer)**, und klicken Sie dann auf **hinzufügen**.  
  
     Eine Datei namens **Ribbon1.cs** oder **Ribbon1.vb** im Menüband-Designer wird geöffnet und zeigt eine standardmäßige Registerkarte und Gruppe.  
  
3.  Aus der **Steuerelemente für Office-Menübänder** auf der Registerkarte die **Toolbox**, ziehen Sie ein CheckBox-Steuerelement auf **group1**.  
  
4.  Klicken Sie auf **CheckBox1** , um dieses Steuerelement auszuwählen.  
  
5.  Ändern Sie im Fenster **Eigenschaften** die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**Button** (Schaltfläche)|  
    |**Bezeichnung**|**Button** (Schaltfläche)|  
  
6.  Fügen Sie **group1**ein zweites Kontrollkästchen hinzu, und ändern Sie dann die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**NamedRange**|  
    |**Bezeichnung**|**NamedRange**|  
  
7.  Fügen Sie ein drittes Kontrollkästchen hinzu **group1**, und klicken Sie dann die folgenden Eigenschaften ändern.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**ListObject**|  
    |**Bezeichnung**|**ListObject**|  
  
## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Verwaltete Steuerelemente können nur Hostelementen hinzugefügt werden, die als Container fungieren. Da VSTO-Add-in-Projekte mit allen geöffneten Arbeitsmappen funktionieren, konvertiert das VSTO-Add-In das Arbeitsblatt in ein Hostelement oder ruft ein vorhandenes Hostelement ab, bevor das Steuerelement hinzugefügt wird. Fügen Sie den Click-Ereignishandlern jedes Steuerelements Code hinzu, um ein auf dem geöffneten Arbeitsblatt basierendes <xref:Microsoft.Office.Tools.Excel.Worksheet>-Hostelement zu generieren. Fügen Sie dann ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> und <xref:Microsoft.Office.Tools.Excel.ListObject> an der aktuellen Auswahlposition in das Arbeitsblatt ein.  
  
### <a name="to-add-controls-to-a-worksheet"></a>So fügen Sie einem Arbeitsblatt Steuerelemente hinzu  
  
1.  Doppelklicken Sie im Menüband-Designer auf **Schaltfläche**.  
  
     Die <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> -Ereignishandler, der die **Schaltfläche** Kontrollkästchen wird im Code-Editor geöffnet.  
  
2.  Ersetzen Sie den `Button_Click`-Ereignishandler durch den folgenden Code.  
  
     Dieser Code verwendet die `GetVstoObject`-Methode, um ein Hostelement abzurufen, das das erste Arbeitsblatt in der Arbeitsmappe darstellt, und fügt der aktuell ausgewählten Zelle dann ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>-Steuerelement hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  In **Projektmappen-Explorer**Option *Ribbon1.cs* oder *Ribbon1.vb*.  
  
4.  Auf der **Ansicht** Menü klicken Sie auf **Designer**.  
  
5.  Doppelklicken Sie im Menüband-Designer auf **NamedRange**.  
  
6.  Ersetzen Sie den `NamedRange_Click`-Ereignishandler durch den folgenden Code.  
  
     Dieser Code verwendet die `GetVstoObject`-Methode, um ein Hostelement abzurufen, das das erste Arbeitsblatt in der Arbeitsmappe darstellt, und fügt der oder den aktuell ausgewählten Zellen dann ein <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelement hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  Doppelklicken Sie im Menüband-Designer auf **ListObject**.  
  
8.  Ersetzen Sie den `ListObject_Click`-Ereignishandler durch den folgenden Code.  
  
     Dieser Code verwendet die `GetVstoObject`-Methode, um ein Hostelement abzurufen, das das erste Arbeitsblatt in der Arbeitsmappe darstellt, und fügt der oder den aktuell ausgewählten Zellen dann ein <xref:Microsoft.Office.Tools.Excel.ListObject> hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. Fügen Sie am Anfang der Menüband-Codedatei die folgenden Anweisungen hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="remove-controls-from-the-worksheet"></a>Entfernen Sie Steuerelemente aus dem Arbeitsblatt  
 Steuerelemente werden nicht beibehalten, wenn das Arbeitsblatt gespeichert und geschlossen wird. Sie sollten alle generierten Windows Forms-Steuerelemente programmgesteuert entfernen, bevor das Arbeitsblatt gespeichert wird, ansonsten wird beim erneuten Öffnen der Arbeitsmappe nur ein Umriss des Steuerelements angezeigt. Fügen Sie dem <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>-Ereignis Code hinzu, durch den Windows Forms-Steuerelemente aus der Steuerelementauflistung des generierten Hostelements entfernt werden. Weitere Informationen finden Sie unter [beibehalten von dynamische Steuerelementen in Office-Dokumente](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
### <a name="to-remove-controls-from-the-worksheet"></a>So entfernen Sie Steuerelemente aus dem Arbeitsblatt  
  
1.  In **Projektmappen-Explorer**Option *"ThisAddIn.cs"* oder *"ThisAddIn.vb"*.  
  
2.  Auf der **Ansicht** Menü klicken Sie auf **Code**.  
  
3.  Fügen Sie der `ThisAddIn` -Klasse die folgende Methode hinzu. Durch diesen Code wird das erste Arbeitsblatt in der Arbeitsmappe abgerufen und dann anhand der `HasVstoObject`-Methode überprüft, ob das Arbeitsblatt über ein generiertes Arbeitsblattobjekt verfügt. Wenn das generierte Arbeitsblattobjekt über Steuerelemente verfügt, ruft der Code das Arbeitsblattobjekt ab und durchläuft die Steuerelementauflistung, um Steuerelemente zu entfernen.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  In C# müssen Sie einen Ereignishandler für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>-Ereignis erstellen. Sie können diesen Code in der `ThisAddIn_Startup`-Methode positionieren. Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md). Ersetzen Sie die `ThisAddIn_Startup` -Methode durch folgenden Code:  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="test-the-solution"></a>Testen der Lösung  
 Fügen Sie Steuerelemente zu einem Arbeitsblatt, indem Sie sie von einer benutzerdefinierten Registerkarte auf dem Menüband auswählen. Diese Steuerelemente werden beim Speichern des Arbeitsblatts entfernt.  
  
### <a name="to-test-the-solution"></a>So testen Sie die Projektmappe  
  
1.  Drücken Sie **F5** um das Projekt auszuführen.  
  
2.  Wählen Sie eine beliebige Zelle in Tabelle1 aus.  
  
3.  Klicken Sie auf die Registerkarte **Add-Ins** .  
  
4.  In der **group1** zu gruppieren, klicken Sie auf **Schaltfläche**.  
  
     In der ausgewählten Zelle wird eine Schaltfläche angezeigt.  
  
5.  Wählen Sie eine andere Zelle in Tabelle1 aus.  
  
6.  In der **group1** zu gruppieren, klicken Sie auf **NamedRange**.  
  
     Für die ausgewählte Zelle wird ein benannter Bereich definiert.  
  
7.  Wählen Sie eine Reihe von Zellen in Tabelle1 aus.  
  
8.  In der **group1** zu gruppieren, klicken Sie auf **ListObject**.  
  
     Für die ausgewählten Zellen wird ein Listenobjekt hinzugefügt.  
  
9. Speichern Sie das Arbeitsblatt.  
  
     Die Steuerelemente, die Sie Tabelle1 hinzugefügt haben, werden nicht mehr angezeigt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Im folgenden Thema erfahren Sie mehr über Steuerelemente in Excel-VSTO-Add-In-Projekten:  
  
-   Um weitere Informationen zum Speichern von Steuerelementen zu einem Arbeitsblatt finden Sie in der Excel-VSTO-Add-in Beispiel für dynamische Steuerelemente unter [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Excel-Projektmappen](../vsto/excel-solutions.md)   
 [Windows forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)  
  
  