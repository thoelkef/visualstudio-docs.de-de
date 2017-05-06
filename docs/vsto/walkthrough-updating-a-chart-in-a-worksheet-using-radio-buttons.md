---
title: "Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Aktualisieren von Arbeitsblättern"
  - "Arbeitsblätter, Aktualisieren mit verwalteten Steuerelementen"
  - "Arbeitsblätter, Verwenden von Optionsfeldern"
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern
  In dieser exemplarischen Vorgehensweise werden die Grundlagen der Verwendung von Optionsfeldern in einem Microsoft Office Excel\-Arbeitsblatt erläutert, um dem Benutzer ein rasches Wechseln zwischen Optionen zu ermöglichen.  In diesem Fall ändern die Optionen das Format dieses Diagramms.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Das Ergebnis in einem vollständigen Beispiel finden Sie in dem Beispiel für Excel\-Steuerelemente unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen einer Gruppe von Optionsfeldern zu einem Arbeitsblatt.  
  
-   Ändern des Diagrammformats beim Auswählen einer Option.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Hinzufügen eines Diagramms zu einem Arbeitsblatt  
 Sie können ein Excel\-Arbeitsmappenprojekt erstellen, das eine vorhandene Arbeitsmappe anpasst.  In dieser exemplarischen Vorgehensweise fügen Sie einer Arbeitsmappe ein Diagramm hinzu und verwenden die Arbeitsmappe anschließend in einer neuen Excel\-Projektmappe.  Die Datenquelle in dieser exemplarischen Vorgehensweise ist das Arbeitsblatt **Daten für Diagramm**.  
  
#### So fügen Sie die Daten hinzu  
  
1.  Öffnen Sie Microsoft Excel.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Registerkarte **Tabelle3**, und klicken Sie dann im Kontextmenü auf **Umbenennen**.  
  
3.  Benennen Sie die Tabelle in Daten für Diagramm um.  
  
4.  Fügen Sie die folgenden Daten in **Daten für Diagramm** ein, wobei Zelle A4 die obere linke Ecke und Zelle E8 die untere rechte Ecke ist.  
  
    ||Q1|Q2|Q3|Q4|  
    |-|--------|--------|--------|--------|  
    |Westen|500|550|550|600|  
    |Osten|600|625|675|700|  
    |Norden|450|470|490|510|  
    |Süden|800|750|775|790|  
  
 Fügen Sie im nächsten Schritt dem ersten Arbeitsblatt ein Diagramm hinzu, um die Daten anzuzeigen.  
  
#### So fügen Sie ein Diagramm in Excel hinzu  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** in der Gruppe **Diagramme** auf **Spalte** und anschließend auf **Alle Diagrammtypen**.  
  
2.  Klicken Sie im Dialogfeld **Diagramm einfügen** auf **OK**.  
  
3.  Klicken Sie auf der Registerkarte **Entwurf** in der Gruppe **Daten** auf **Daten auswählen**.  
  
4.  Klicken Sie im Dialogfeld **Datenquelle auswählen** in das Feld **DiagrammDatenbereich**, und deaktivieren Sie alle Standardeinstellungen.  
  
5.  Wählen Sie im Blatt **Daten für Diagramm** den Block von Zellen mit den Zahlen aus, der sich von A4 oben links bis E8 unten rechts erstreckt.  
  
6.  Klicken Sie im Dialogfeld **Datenquelle auswählen** auf **OK**.  
  
7.  Positionieren Sie das Diagramm neu, sodass die obere rechte Ecke an Zelle **E2** ausgerichtet ist.  
  
8.  Speichern Sie die Datei, um Laufwerk C und es zu benennen **ExcelChart.xlsx**.  
  
9. Beenden Sie Excel.  
  
## Erstellen eines neuen Projekts  
 In diesem Schritt erstellen Sie basierend auf der Arbeitsmappe **ExcelChart** ein Excel\-Arbeitsmappenprojekt.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen ein Excel\-Arbeitsmappenprojekt mit dem Namen **Mein Excel\-Diagramm**.  Wählen Sie im Assistenten **Vorhandenes Dokument kopieren**.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie auf das **Durchsuchen**  buttonand  Durchsuchen der Arbeitsmappe, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben.  
  
3.  Klicken Sie auf **OK**.  
  
     In Visual Studio wird eine neue Excel\-Arbeitsmappe im Designer geöffnet, und im **Projektmappen\-Explorer** wird das Projekt **Mein Excel\-Diagramm** hinzugefügt.  
  
## Festlegen von Eigenschaften des Diagramms  
 Wenn Sie mithilfe einer vorhandenen Arbeitsmappe ein neues Excel\-Arbeitsmappenprojekt erstellen, werden für alle in der Arbeitsmappe vorhandenen benannten Bereiche, Listenobjekte und Diagramme automatisch Hoststeuerelemente erstellt.  Sie können den Namen des <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelements mithilfe des Fensters **Eigenschaften** ändern.  
  
#### So ändern Sie den Namen des Chart\-Steuerelements  
  
1.  Wählen Sie das <xref:Microsoft.Office.Tools.Excel.Chart>\-Steuerelement im Designer aus, und ändern Sie im Fenster **Eigenschaften** die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## Hinzufügen von Steuerelementen  
 In diesem Arbeitsblatt ermöglichen Optionsfelder eine rasche Änderung des Diagrammstils.  Allerdings müssen Optionsfelder exklusiv sein &ndash; beim Klicken auf eine Schaltfläche kann nicht gleichzeitig auf eine andere Schaltfläche in der Gruppe geklickt werden.  Dieses Verhalten entspricht nicht dem Standardverhalten beim Hinzufügen mehrerer Optionsfelder zu einem Arbeitsblatt.  
  
 Eine Methode zum Hinzufügen dieses Verhaltens besteht darin, die Optionsfelder auf einem Benutzersteuerelement zu gruppieren, den Code hinter das Benutzersteuerelement zu schreiben und anschließend dem Arbeitsblatt das Benutzersteuerelement hinzuzufügen.  
  
#### So fügen Sie ein Benutzersteuerelement hinzu  
  
1.  Wählen Sie das Projekt **Mein Excel\-Diagramm** im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Benutzersteuerelement**, weisen Sie dem Steuerelement den Namen **ChartOptions** zu, und klicken Sie auf **Hinzufügen**.  
  
#### So fügen Sie dem Benutzersteuerelement Optionsfelder hinzu  
  
1.  Wenn das Benutzersteuerelement im Designer nicht sichtbar ist, doppelklicken Sie im **Projektmappen\-Explorer** auf **ChartOptions**.  
  
2.  Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein **Optionsfeld**\-Steuerelement auf das Benutzersteuerelement, und ändern Sie folgende Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**columnChart**|  
    |**Text**|Column Chart|  
  
3.  Fügen Sie dem Benutzersteuerelement ein zweites Optionsfeld hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**barChart**|  
    |**Text**|Bar Chart|  
  
4.  Fügen Sie dem Benutzersteuerelement ein drittes Optionsfeld hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**lineChart**|  
    |**Text**|Line Chart|  
  
5.  Fügen Sie dem Benutzersteuerelement ein viertes Optionsfeld hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**areaBlockChart**|  
    |**Text**|Area Block Chart|  
  
 Schreiben Sie anschließend den Code, durch den das Diagramm beim Klicken auf ein Optionsfeld aktualisiert wird.  
  
## Ändern des Diagrammstils beim Auswählen eines Optionsfelds  
 Nun kann der Code zum Ändern des Diagrammstils hinzugefügt werden.  Erstellen Sie dazu ein öffentliches Ereignis für das Benutzersteuerelement, fügen Sie eine Eigenschaft hinzu, um den Auswahltyp festzulegen, und erstellen Sie einen Ereignishandler für das `CheckedChanged`\-Ereignis jedes Optionsfelds.  
  
#### So erstellen Sie ein Ereignis und eine Eigenschaft für ein Benutzersteuerelement  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Benutzersteuerelement, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Fügen Sie der `ChartOptions`\-Klasse Code hinzu, um ein `SelectionChanged`\-Ereignis und die `Selection`\-Eigenschaft zu erstellen.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#13)]  
  
#### So behandeln Sie das CheckedChanged\-Ereignis der Optionsfelder  
  
1.  Legen Sie den Diagrammtyp im `CheckedChanged`\-Ereignishandler des Optionsfelds `areaBlockChart` fest, und lösen Sie anschließend das Ereignis aus.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#14)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#14)]  
  
2.  Legen Sie den Diagrammtyp im `CheckedChanged`\-Ereignishandler des Optionsfelds `barChart` fest.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#15)]  
  
3.  Legen Sie den Diagrammtyp im `CheckedChanged`\-Ereignishandler des Optionsfelds `columnChart` fest.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#16)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#16)]  
  
4.  Legen Sie den Diagrammtyp im `CheckedChanged`\-Ereignishandler des Optionsfelds `lineChart` fest.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#17)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#17)]  
  
5.  In C\# müssen Sie Ereignishandler für die Optionsfelder hinzufügen.  Sie können den Code zum `ChartOptions`\-Konstruktor hinzufügen, unterhalb des Aufrufs von `InitializeComponent`.  Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#18)]  
  
## Hinzufügen des Benutzersteuerelements zum Arbeitsblatt  
 Beim Erstellen der Projektmappe wird das neue Benutzersteuerelement der **Toolbox** automatisch hinzugefügt.  Dann können Sie das Steuerelement von der **Toolbox** auf das Arbeitsblatt ziehen.  
  
#### So fügen Sie dem Arbeitsblatt das Benutzersteuerelement hinzu  
  
1.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Der **Toolbox** wird das **ChartOptions**\-Benutzersteuerelement hinzugefügt.  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie anschließend auf **Ansicht\-Designer**.  
  
3.  Ziehen Sie das **ChartOptions**\-Steuerelement aus der **Toolbox** auf das Arbeitsblatt.  
  
     Das neue Steuerelement `my_Excel_Chart_ChartOptions1` wird dem Projekt hinzugefügt.  
  
4.  Geben Sie dem Steuerelement den neuen Namen ChartOptions1.  
  
## Ändern des Diagrammtyps  
 Erstellen Sie zum Ändern des Diagrammtyps einen Ereignishandler, mit dem der Stil entsprechend der im Benutzersteuerelement ausgewählten Option geändert wird.  
  
#### So ändern Sie den Diagrammtyp, der im Arbeitsblatt angezeigt wird  
  
1.  Fügen Sie der `Sheet1`\-Klasse den folgenden Ereignishandler hinzu.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#19)]  
  
2.  In C\# müssen Sie dem <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignis einen Ereignishandler für das Benutzersteuerelement hinzufügen, wie im Folgenden dargestellt.  Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#20)]  
  
## Testen der Anwendung  
 Sie können die Arbeitsmappe jetzt testen, um sicherzustellen, dass das Diagramm beim Auswählen eines Optionsfelds richtig formatiert wird.  
  
#### So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Wählen Sie verschiedene Optionsfelder aus.  
  
3.  Überprüfen Sie, ob der Diagrammstil entsprechend der Auswahl geändert wurde.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen der Verwendung von Optionsfeldern und Diagrammstilen in Arbeitsblättern erläutert.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Bereitstellen des Projekts.  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
-   Verwenden einer Schaltfläche zum Auffüllen eines Textfelds.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Ändern der Formatierung in einem Arbeitsblatt mithilfe von Kontrollkästchen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ändern der Arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)  
  
  