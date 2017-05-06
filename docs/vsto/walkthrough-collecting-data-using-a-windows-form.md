---
title: "Exemplarische Vorgehensweise: Erfassen von Daten mit einem Windows&#160;Form"
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
  - "Daten [Office-Entwicklung in Visual Studio], Windows Forms"
  - "Windows Forms [Office-Entwicklung in Visual Studio], Erfassen von Daten"
  - "Formulare [Office-Entwicklung in Visual Studio], Exemplarische Vorgehensweisen"
  - "Arbeitsblätter [Office-Entwicklung in Visual Studio], Erfassen von Daten"
ms.assetid: 40e87f7f-cfbb-4761-bf1b-d042f45f4f09
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Exemplarische Vorgehensweise: Erfassen von Daten mit einem Windows&#160;Form
  In dieser exemplarischen Vorgehensweise wird das Öffnen eines Windows Form aus einer Anpassung auf Dokumentebene für Microsoft Office Excel, das Abfragen von Benutzerinformationen und das Schreiben dieser Informationen in eine Zelle des Arbeitsblatts beschrieben.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Obwohl in dieser exemplarischen Vorgehensweise speziell ein Projekt auf Dokumentebene für Excel verwendet wird, gelten die Konzepte in dieser exemplarischen Vorgehensweise auch für andere Office\-Projekte.  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio\-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Erstellen eines neuen Projekts  
 Zunächst müssen Sie ein Excel\-Arbeitsmappenprojekt erstellen.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel\-Arbeitsmappenprojekt mit dem Namen **WinFormInput**, und wählen Sie im Assistenten **Neues Dokument erstellen** aus. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel\-Arbeitsmappe im Designer und fügt dem **Projektmappen\-Explorer** das **WinFormInput**\-Projekt hinzu.  
  
## Hinzufügen eines NamedRange\-Steuerelements zum Arbeitsblatt  
  
#### So fügen Sie Blatt1 einen benannten Bereich hinzu  
  
1.  Wählen Sie in `Sheet1` die Zelle **A1** aus.  
  
2.  Geben Sie im Feld **Name** die Zeichenfolge **formInput** ein.  
  
     Das Feld **Name** befindet sich links neben der Bearbeitungsleiste, genau über der Spalte **A** des Arbeitsblatts.  
  
3.  Drücken Sie die EINGABETASTE.  
  
     Der Zelle **A1** wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement hinzugefügt. Auf dem Arbeitsblatt gibt es dafür keinen sichtbaren Hinweis, aber wenn Zelle **A1** ausgewählt ist, wird **formInput** im Feld **Name** \(auf der linken Seite direkt über dem Arbeitsblatt\) und im Fenster **Eigenschaften** angezeigt.  
  
## Hinzufügen eines Windows Form zum Projekt  
 Erstellen Sie ein Windows Form, in dem die Benutzer zur Eingabe von Informationen aufgefordert werden.  
  
#### So fügen Sie ein Windows Form hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt **WinFormInput** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Windows Form hinzufügen**.  
  
3.  Nennen Sie das Formular **GetInputString.vb** bzw. **GetInputString.cs**, und klicken Sie anschließend auf **Hinzufügen**.  
  
     Das neue Formular wird im Designer geöffnet.  
  
4.  Fügen Sie dem Formular eine <xref:System.Windows.Forms.TextBox> und eine <xref:System.Windows.Forms.Button> hinzu.  
  
5.  Markieren Sie die Schaltfläche, suchen Sie im Fenster **Eigenschaften** die Eigenschaft **Text**, und ändern Sie den Text in **OK**.  
  
 Fügen Sie anschließend `ThisWorkbook.vb` oder `ThisWorkbook.cs` Code hinzu, um die Benutzerinformationen abzufragen.  
  
## Anzeigen des Windows Form und Abfragen von Informationen  
 Erstellen Sie eine Instanz des Windows Form `GetInputString`, zeigen Sie diese an, und schreiben Sie dann die Benutzerinformationen in eine Zelle im Arbeitsblatt.  
  
#### So zeigen Sie das Formular an und fragen die Informationen ab  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **ThisWorkbook.vb** bzw. **ThisWorkbook.cs**, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Workbook.Open>\-Ereignishandler von `ThisWorkbook` den folgenden Code hinzu, um für das Formular `GetInputString` eine Variable zu deklarieren und anschließend das Formular anzuzeigen.  
  
    > [!NOTE]  
    >  In C\# müssen Sie einen Ereignishandler hinzufügen, wie im <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>\-Ereignis unten dargestellt. Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/ThisWorkbook.vb#1)]  
  
3.  Erstellen Sie eine Methode mit dem Namen `WriteStringToCell`, die Text in einen benannten Bereich schreibt. Diese Methode wird vom Formular aufgerufen, und die Benutzereingabe wird an das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement `formInput` in Zelle **A1** übergeben.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/ThisWorkbook.vb#2)]  
  
 Fügen Sie dem Formular anschließend Code hinzu, um das Klickereignis der Schaltfläche zu behandeln.  
  
## Senden von Informationen an das Arbeitsblatt  
  
#### So senden Sie Informationen an das Arbeitsblatt  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **GetInputString**, und klicken Sie dann auf **Ansicht\-Designer**.  
  
2.  Doppelklicken Sie auf die Schaltfläche, um die Codedatei mit dem hinzugefügten <xref:System.Windows.Forms.Control.Click>\-Ereignishandler der Schaltfläche zu öffnen.  
  
3.  Fügen Sie dem Ereignishandler Code hinzu, um die Eingabe im Textfeld zu an die `WriteStringToCell`\-Funktion zu senden, und schließen Sie dann das Formular.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/GetInputString.vb#3)]  
  
## Test  
 Sie können das Projekt jetzt ausführen. Das Windows Form wird angezeigt, und die Eingabe wird im Arbeitsblatt angezeigt.  
  
#### So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Überprüfen Sie, ob das Windows Form angezeigt wird.  
  
3.  Geben Sie im Textfeld **Hallo Welt** ein, und klicken Sie dann auf **OK**.  
  
4.  Überprüfen Sie, ob in Zelle **A1** im Arbeitsblatt **Hallo Welt** angezeigt wird.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen für das Anzeigen eines Windows Form und das Übergeben von Daten an ein Arbeitsblatt beschrieben. Andere Aufgaben in diesem Zusammenhang sind:  
  
-   Verwenden von Windows Forms\-Steuerelementen in einer Excel\-Arbeitsmappe bzw. einem Word\-Dokument. Weitere Informationen finden Sie unter [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Ändern der Benutzeroberfläche einer Microsoft Office\-Anwendung von einer Anpassung auf Dokumentebene bzw. einem VSTO\-Add\-In aus. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## Siehe auch  
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Exemplarische Vorgehensweisen in Word](../vsto/walkthroughs-using-word.md)   
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)  
  
  