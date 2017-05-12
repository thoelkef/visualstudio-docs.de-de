---
title: "Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfl&#228;che"
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
  - "Text [Office-Entwicklung in Visual Studio], Anzeigen von Arbeitsblättern"
  - "Text [Office-Entwicklung in Visual Studio], Textfelder"
  - "Textfelder, Anzeigen von Text in Arbeitsblättern"
  - "Arbeitsblätter, Anzeigen von Text"
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Arbeitsblatt mithilfe einer Schaltfl&#228;che
  Diese exemplarische Vorgehensweise erläutert die Grundlagen der Verwendung von Schaltflächen und Textfeldern auf Microsoft Office Excel\-Arbeitsblättern sowie die Erstellung von Excel\-Projekten mit Office\-Entwicklungstools in Visual Studio.  Das Ergebnis in einem vollständigen Beispiel finden Sie in dem Beispiel für Excel\-Steuerelemente unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt.  
  
-   Füllen eines Textfelds beim Klick auf eine Schaltfläche.  
  
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
  
1.  Erstellen Sie ein Excel\-Arbeitsmappenprojekt mit dem Namen My Excel Button.  Stellen Sie sicher, dass **Neues Dokument erstellen** ausgewählt ist.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel\-Arbeitsmappe im Designer und fügt dem **Projektmappen\-Explorer** das **My Excel Button**\-Projekt hinzu.  
  
## Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Für diese exemplarische Vorgehensweise muss das erste Arbeitsblatt eine Schaltfläche und ein Textfeld enthalten.  
  
#### So fügen Sie eine Schaltfläche und ein Textfeld hinzu  
  
1.  Überprüfen Sie, ob die **My Excel Button.xlsx** Arbeitsmappe im Visual Studio\-Designer geöffnet ist, mit `Sheet1` angezeigt.  
  
2.  Ziehen Sie in der Toolbox von der Registerkarte **Allgemeine Steuerelemente** ein <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> auf `Sheet1`.  
  
3.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.  
  
4.  Stellen Sie sicher, dass im Dropdownfeld des **EigenschaftenfenstersTextBox1** sichtbar ist, und ändern Sie die **Name**\-Eigenschaft in **displayText**.  
  
5.  Ziehen Sie ein **Button**\-Steuerelement auf `Sheet1`, und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**insertText**|  
    |**Text**|Text einfügen|  
  
 Schreiben Sie den beim Klicken auf die Schaltfläche auszuführenden Code.  
  
## Auffüllen des Textfelds beim Klicken auf die Schaltfläche  
 Immer wenn der Benutzer auf die Schaltfläche klickt, wird **Hallo Welt \!** an das Textfeld angehängt.  
  
#### So schreiben Sie beim Klicken auf die Schaltfläche in das Textfeld  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Sheet1**, und klicken Sie dann im Kontextmenü auf **Code anzeigen**.  
  
2.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignishandler der Schaltfläche folgenden Code hinzu:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#11)]  
  
3.  In C\# müssen Sie einen Ereignishandler zum <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignis hinzufügen, wie unten dargestellt.  Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#12)]  
  
## Testen der Anwendung  
 Sie können die Arbeitsmappe jetzt testen, um sicherzustellen, dass die Meldung **Hallo Welt \!** im Textfeld angezeigt wird, wenn Sie auf die Schaltfläche klicken.  
  
#### So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Klicken Sie auf die Schaltfläche.  
  
3.  Überprüfen Sie, ob **Hallo Welt \!** im Textfeld angezeigt wird.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Excel\-Arbeitsblättern erläutert.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Bereitstellen des Projekts.  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
-   Verwenden von Kontrollkästchen zum Ändern der Formatierung.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ändern der Arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## Siehe auch  
 [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  