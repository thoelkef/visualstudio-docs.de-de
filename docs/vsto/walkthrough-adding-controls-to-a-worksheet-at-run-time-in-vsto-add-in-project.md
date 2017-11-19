---
title: "Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in einem VSTO-add-in-Projekt | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bae6ff23763300a4baa748479c609217123c765c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in einem VSTO-Add-In-Projekt
  Sie können einem beliebigen geöffneten Arbeitblatt Steuerelemente mithilfe eines Excel-VSTO-Add-In hinzufügen. Diese exemplarische Vorgehensweise veranschaulicht, wie Benutzer einem Arbeitsblatt mithilfe des Menübands ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> und <xref:Microsoft.Office.Tools.Excel.ListObject> hinzufügen können. Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Gilt für:** die Informationen in diesem Thema betreffen VSTO-Add-in-Projekte für Excel. Weitere Informationen finden Sie unter [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Bereitstellen einer Benutzeroberfläche (UI) zum Hinzufügen von Steuerelementen zum Arbeitsblatt  
  
-   Hinzufügen von Steuerelementen zum Arbeitsblatt  
  
-   Entfernen von Steuerelementen aus dem Arbeitsblatt  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="creating-a-new-excel-vsto-add-in-project"></a>Erstellen eines neuen Excel-VSTO-Add-In-Projekts  
 Beginnen Sie mit der Erstellung eines Excel VSTO-Add-In-Projekts.  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project"></a>So erstellen Sie ein neues Excel-VSTO-Add-In-Projekt  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], erstellen Sie ein Excel-VSTO-Add-in-Projekt mit dem Namen **"ExcelDynamicControls"**. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Hinzufügen eines Verweises auf die **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** Assembly. Dieser Verweis ist erforderlich, um einem Arbeitsblatt ein Windows Forms-Steuerelement in dieser exemplarischen Vorgehensweise später programmgesteuert hinzuzufügen.  
  
## <a name="providing-a-ui-to-add-controls-to-a-worksheet"></a>Bereitstellen einer Benutzeroberfläche zum Hinzufügen von Steuerelementen zu einem Arbeitsblatt  
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
  
## <a name="adding-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Verwaltete Steuerelemente können nur Hostelementen hinzugefügt werden, die als Container fungieren. Da VSTO-Add-in-Projekte mit allen geöffneten Arbeitsmappen funktionieren, konvertiert das VSTO-Add-In das Arbeitsblatt in ein Hostelement oder ruft ein vorhandenes Hostelement ab, bevor das Steuerelement hinzugefügt wird. Fügen Sie den Click-Ereignishandlern jedes Steuerelements Code hinzu, um ein auf dem geöffneten Arbeitsblatt basierendes <xref:Microsoft.Office.Tools.Excel.Worksheet>-Hostelement zu generieren. Fügen Sie dann ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> und <xref:Microsoft.Office.Tools.Excel.ListObject> an der aktuellen Auswahlposition in das Arbeitsblatt ein.  
  
#### <a name="to-add-controls-to-a-worksheet"></a>So fügen Sie einem Arbeitsblatt Steuerelemente hinzu  
  
1.  Doppelklicken Sie im Menüband-Designer auf **Schaltfläche**.  
  
     Die <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> -Ereignishandler, der die **Schaltfläche** Kontrollkästchen wird im Code-Editor geöffnet.  
  
2.  Ersetzen Sie den `Button_Click`-Ereignishandler durch den folgenden Code.  
  
     Dieser Code verwendet die `GetVstoObject`-Methode, um ein Hostelement abzurufen, das das erste Arbeitsblatt in der Arbeitsmappe darstellt, und fügt der aktuell ausgewählten Zelle dann ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>-Steuerelement hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  In **Projektmappen-Explorer**, wählen Sie Ribbon1.cs oder Ribbon1.vb aus.  
  
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
  
## <a name="removing-controls-from-the-worksheet"></a>Entfernen von Steuerelementen aus dem Arbeitsblatt  
 Steuerelemente werden nicht beibehalten, wenn das Arbeitsblatt gespeichert und geschlossen wird. Sie sollten alle generierten Windows Forms-Steuerelemente programmgesteuert entfernen, bevor das Arbeitsblatt gespeichert wird, ansonsten wird beim erneuten Öffnen der Arbeitsmappe nur ein Umriss des Steuerelements angezeigt. Fügen Sie dem <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>-Ereignis Code hinzu, durch den Windows Forms-Steuerelemente aus der Steuerelementauflistung des generierten Hostelements entfernt werden. Weitere Informationen finden Sie unter [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### <a name="to-remove-controls-from-the-worksheet"></a>So entfernen Sie Steuerelemente aus dem Arbeitsblatt  
  
1.  In **Projektmappen-Explorer**, wählen Sie "ThisAddIn.cs" oder "ThisAddIn.vb".  
  
2.  Auf der **Ansicht** Menü klicken Sie auf **Code**.  
  
3.  Fügen Sie der ThisAddin-Klasse die folgende Methode hinzu. Durch diesen Code wird das erste Arbeitsblatt in der Arbeitsmappe abgerufen und dann anhand der `HasVstoObject`-Methode überprüft, ob das Arbeitsblatt über ein generiertes Arbeitsblattobjekt verfügt. Wenn das generierte Arbeitsblattobjekt über Steuerelemente verfügt, ruft der Code das Arbeitsblattobjekt ab und durchläuft die Steuerelementauflistung, um Steuerelemente zu entfernen.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  In C# müssen Sie einen Ereignishandler für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>-Ereignis erstellen. Sie können diesen Code in der `ThisAddIn_Startup`-Methode positionieren. Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md). Ersetzen Sie die `ThisAddIn_Startup` -Methode durch folgenden Code:  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="testing-the-solution"></a>Testen der Projektmappe  
 Fügen Sie einem Arbeitsblatt Steuerelemente hinzu, indem Sie sie von einer benutzerdefinierten Registerkarte des Menübands auswählen. Diese Steuerelemente werden beim Speichern des Arbeitsblatts entfernt.  
  
#### <a name="to-test-the-solution"></a>So testen Sie die Projektmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
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
  
-   Um weitere Informationen zum Speichern von Steuerelementen zu einem Arbeitsblatt finden Sie in der Excel-VSTO-Add-in Beispiel für dynamische Steuerelemente unter [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Excel-Projektmappen](../vsto/excel-solutions.md)   
 [Windows Forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)  
  
  