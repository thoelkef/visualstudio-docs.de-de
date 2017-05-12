---
title: "Exemplarische Vorgehensweise: &#196;ndern der Arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
  - "Arbeitsblätter, Ändern der Formatierung mit verwalteten Steuerelementen"
  - "Arbeitsblätter, Kontrollkästchen-Steuerelemente"
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Exemplarische Vorgehensweise: &#196;ndern der Arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen
  In dieser exemplarischen Vorgehensweise werden die Grundlagen zum Ändern der Formatierung mithilfe von Kontrollkästchen in einem Microsoft Office Excel\-Arbeitsblatt beschrieben.  Sie verwenden Office\-Entwicklungstools in Visual Studio, um Code zu erstellen und dem Projekt hinzuzufügen.  Das Ergebnis in einem vollständigen Beispiel finden Sie in dem Beispiel für Excel\-Steuerelemente unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen von Text und Steuerelementen zu einem Arbeitsblatt.  
  
-   Formatieren des Texts beim Auswählen einer Option.  
  
-   Testen des Projekts.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Erstellen des Projekts  
 In diesem Schritt erstellen Sie mit Visual Studio ein Excel\-Arbeitsmappenprojekt.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel\-Arbeitsmappenprojekt mit dem Namen My Excel Formatting.  Stellen Sie sicher, dass **Neues Dokument erstellen** ausgewählt ist.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel\-Arbeitsmappe im Designer und fügt dem **Projektmappen\-Explorer** das **My Excel Formatting**\-Projekt hinzu.  
  
## Hinzufügen von Text und Steuerelementen zum Arbeitsblatt  
 In dieser exemplarischen Vorgehensweise werden drei <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>\-Steuerelemente und ein Text in einem <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement benötigt.  
  
#### So fügen Sie drei Kontrollkästchen hinzu  
  
1.  Überprüfen Sie, ob die Arbeitsmappe und `Sheet1` im Visual Studio\-Designer geöffnet sind.  
  
2.  Ziehen Sie in der **Toolbox** von der Registerkarte **Allgemeine Steuerelemente** ein <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>\-Steuerelement auf **Sheet1** in oder in die Nähe von Zelle **B2**.  
  
3.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.  
  
4.  Stellen Sie sicher, dass im **Eigenschaftenfenster** im Objektnamen\-Listenfeld **Checkbox1** angezeigt wird, und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|Fett|  
  
5.  Ziehen Sie ein zweites Kontrollkästchen in oder in die Nähe von Zelle **B4**, und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|Kursiv|  
  
6.  Ziehen Sie ein drittes Kontrollkästchen in oder in die Nähe von Zelle **B6**, und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|Unterstreichen|  
  
7.  Wählen Sie alle drei Kontrollkästchen\-Steuerelemente aus, indem Sie STRG gedrückt halten.  
  
8.  In der Anordnens\-Gruppe der Formatregisterkarte in Excel, klicken Sie auf **Ausrichten** und dann auf **Linksbündig**.  
  
     Die drei Kontrollkästchen\-Steuerelemente sind auf die linke Seite, an der Position des ersten Steuerelements ausgerichtet, das Sie ausgewählt haben.  
  
     Ziehen Sie als Nächstes ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement auf das Arbeitsblatt.  
  
    > [!NOTE]  
    >  Sie können auch das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement hinzufügen, indem Sie in das Feld **NametextFont** eingeben.  
  
#### So fügen Sie einem NamedRange\-Steuerelement Text hinzu  
  
1.  Ziehen Sie von der Registerkarte **Excel\-Steuerelemente** der Toolbox ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement auf die Zelle **B9**.  
  
2.  Stellen Sie sicher, dass im bearbeitbaren Textfeld **$B$9** angezeigt wird und dass die Zelle **B9** ausgewählt ist.  Wenn dies nicht der Fall ist, klicken Sie auf die Zelle **B9**, um diese auszuwählen.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Zelle **B9** wird zum Bereich `NamedRange1`.  
  
     Auf dem Arbeitsblatt gibt es dafür keinen sichtbaren Hinweis, aber wenn Zelle **B9** ausgewählt ist, wird `NamedRange1` im Feld **Name** \(auf der linken Seite direkt über dem Arbeitsblatt\) angezeigt.  
  
5.  Stellen Sie sicher, dass im **Eigenschaftenfenster** im Objektnamen\-Listenfeld **NamedRange1** angezeigt wird, und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**textFont**|  
    |**Value2**|Klicken Sie auf ein Kontrollkästchen, um die Formatierung des Texts zu ändern.|  
  
 Als Nächstes schreiben Sie Code, der den Text beim Auswählen einer Option formatiert.  
  
## Formatieren des Texts beim Auswählen einer Option  
 In diesem Abschnitt schreiben Sie Code, der beim Auswählen einer Formatierungsoption durch den Benutzer das Textformat im Arbeitsblatt ändert.  
  
#### So ändern Sie die Formatierung beim Aktivieren eines Kontrollkästchens  
  
1.  Klicken Sie mit der rechten Maustaste auf **Sheet1**, und klicken Sie anschließend im Kontextmenü auf **Code anzeigen**.  
  
2.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignishandler des `applyBoldFont`\-Kontrollkästchens den folgenden Code hinzu:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#7)]  
  
3.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignishandler des `applyItalicFont`\-Kontrollkästchens den folgenden Code hinzu:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#8)]  
  
4.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignishandler des `applyUnderlineFont`\-Kontrollkästchens den folgenden Code hinzu:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#9)]  
  
5.  In C\# müssen Sie, wie im Folgenden gezeigt, Ereignishandler für die Kontrollkästchen zum <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignis hinzufügen.  Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#10)]  
  
## Testen der Anwendung  
 Sie können die Arbeitsmappe nun testen, um sicherzustellen, dass der Text beim Aktivieren bzw. Deaktivieren eines Kontrollkästchens richtig formatiert wird.  
  
#### So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Aktivieren bzw. deaktivieren Sie ein Kontrollkästchen.  
  
3.  Überprüfen Sie, ob der Text richtig formatiert ist.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen für die Verwendung von Kontrollkästchen und das Formatieren von Texten in Excel\-Arbeitsblättern erläutert.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Bereitstellen des Projekts.  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Verwenden einer Schaltfläche zum Auffüllen eines Textfelds.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  