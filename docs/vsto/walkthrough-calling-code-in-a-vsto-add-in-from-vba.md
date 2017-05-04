---
title: "Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem VSTO-Add-In | Microsoft Docs"
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
  - "VBA [Office-Entwicklung in Visual Studio], Aufrufen von Code in Add-Ins auf Anwendungsebene"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Aufrufen von Code aus anderen Projektmappen"
  - "Gewusst-wie-Videos, Office-Entwicklung in Visual Studio"
  - "Aufrufen von Add-In-Code"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Aufrufen von Code aus anderen Projektmappen"
  - "Interoperabilität [Office-Entwicklung in Visual Studio]"
  - "Aufrufen von Code aus VBA"
ms.assetid: 9c04d1df-0d93-473c-85fd-02dc2e956c9e
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem VSTO-Add-In
  Diese exemplarische Vorgehensweise veranschaulicht, wie ein Objekt in einem VSTO\-Add\-In für andere Microsoft Office\-Projektmappen verfügbar gemacht wird, einschließlich Visual Basic for Applications \(VBA\) und COM\-VSTO\-Add\-Ins.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Obwohl in dieser exemplarischen Vorgehensweise speziell Excel verwendet wird, gelten die veranschaulichten Konzepte für alle VSTO\-Add\-In\-Projektvorlagen, die von Visual Studio bereitgestellt werden.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Definieren einer Klasse, die für andere Office\-Projektmappen verfügbar gemacht werden kann  
  
-   Verfügbarmachen der Klasse für andere Office\-Projektmappen  
  
-   Aufrufen einer Methode der Klasse aus VBA\-Code  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Erstellen des VSTO\-Add\-In\-Projekts  
 Der erste Schritt ist das Erstellen eines VSTO\-Add\-In\-Projekts für Excel.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein VSTO\-Add\-In\-Projekt für Excel namens **ExcelImportData**, indem Sie die Excel\-VSTO\-Add\-In\-Projektvorlage verwenden. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb** und fügt das **ExcelImportData**\-Projekt dem **Projektmappen\-Explorer** hinzu.  
  
## Definieren einer Klasse, die für andere Office\-Projektmappen verfügbar gemacht werden kann  
 Der Zweck dieser exemplarischen Vorgehensweise besteht im Aufrufen der `ImportData`\-Methode einer Klasse mit dem Namen `AddInUtilities` in Ihrem VSTO\-Add\-In aus VBA\-Code. Mit dieser Methode wird eine Zeichenfolge in die Zelle A1 des aktiven Arbeitsblatts geschrieben.  
  
 Um die `AddInUtilities`\-Klasse für andere Office\-Projektmappen verfügbar zu machen, müssen Sie die Klasse öffentlich und für COM sichtbar machen. Außerdem müssen Sie die [IDispatch](http://msdn.microsoft.com/de-de/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)\-Schnittstelle in der Klasse verfügbar machen. Mit dem Code in der folgenden Prozedur wird eine Möglichkeit zum Erfüllen dieser Anforderungen veranschaulicht. Weitere Informationen finden Sie unter [Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### So definieren Sie eine Klasse, die für andere Office\-Projektmappen verfügbar gemacht werden kann  
  
1.  Klicken Sie im Menü **Projekt** auf **Klasse hinzufügen**.  
  
2.  Ändern Sie im Dialogfeld  **Neues Element hinzufügen**  den Namen der neuen Klasse in **AddInUtilities**, und klicken Sie auf **Hinzufügen**.  
  
     Die Datei **AddInUtilities.cs** oder **AddInUtilities.vb** wird im Code\-Editor geöffnet.  
  
3.  Fügen Sie am Anfang der Datei die folgenden Anweisungen ein.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#2)]  
  
4.  Ersetzen Sie die `AddInUtilities`\-Klasse durch den folgenden Code.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#3)]  
  
     Mit diesem Code wird die `AddInUtilities`\-Klasse für COM sichtbar, und die `ImportData`\-Methode wird der Klasse hinzugefügt. Zum Verfügbarmachen der [IDispatch](http://msdn.microsoft.com/de-de/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)\-Schnittstelle verfügt die `AddInUtilities`\-Klasse auch über das <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>\-Attribut und implementiert eine Schnittstelle, die für COM sichtbar ist.  
  
## Verfügbarmachen der Klasse für andere Office\-Projektmappen  
 Um die `AddInUtilities`\-Klasse für andere Office\-Projektmappen verfügbar zu machen, setzen Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>\-Methode in der `ThisAddIn`\-Klasse außer Kraft. Geben Sie bei der Außerkraftsetzung eine Instanz der `AddInUtilities`\-Klasse zurück.  
  
#### So machen Sie die AddInUtilities\-Klasse für andere Office\-Projektmappen verfügbar  
  
1.  Erweitern Sie im **Projektmappen\-Explorer** die Option **Excel**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **ThisAddIn.cs** bzw. **ThisAddIn.vb**, und klicken Sie dann auf **Code anzeigen**.  
  
3.  Fügen Sie der `ThisAddIn`\-Klasse folgenden Code hinzu.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/ThisAddIn.vb#1)]  
  
4.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Überprüfen Sie, ob die Lösung ohne Fehler erstellt wurde.  
  
## Testen des VSTO\-Add\-Ins  
 Sie können die `AddInUtilities`\-Klasse aus unterschiedlichen Arten von Office\-Projektmappen aufrufen. In dieser exemplarischen Vorgehensweise verwenden Sie VBA\-Code in einer Excel\-Arbeitsmappe. Weitere Informationen zu anderen Typen von Office\-Projektmappen, die Sie ebenfalls verwenden können, finden Sie unter [Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### So testen Sie Ihr VSTO\-Add\-In  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Speichern Sie in Excel die aktive Arbeitsmappe als Excel\-Arbeitsmappe mit Makros \(\*.xlsm\). Speichern Sie sie an einem geeigneten Speicherort, z. B. auf dem Desktop.  
  
3.  Klicken Sie im Menüband auf die Registerkarte **Entwickler**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Klicken Sie in der Gruppe **Code** auf **Visual Basic**.  
  
     Der Visual Basic\-Editor wird geöffnet.  
  
5.  Doppelklicken Sie im **Projektfenster** auf **DieseArbeitsmappe**.  
  
     Die Codedatei für das `ThisWorkbook`\-Objekt wird geöffnet.  
  
6.  Fügen Sie der Codedatei den folgenden VBA\-Code hinzu. Mit diesem Code wird zuerst ein COMAddIn\-Objekt abgerufen, das dem VSTO\-Add\-In **ExcelImportData** entspricht. Anschließend verwendet der Code die Object\-Eigenschaft des COMAddIn\-Objekts, um die `ImportData`\-Methode aufzurufen.  
  
    ```  
    Sub CallVSTOMethod() Dim addIn As COMAddIn Dim automationObject As Object Set addIn = Application.COMAddIns("ExcelImportData") Set automationObject = addIn.Object automationObject.ImportData End Sub  
    ```  
  
7.  Drücken Sie F5.  
  
8.  Überprüfen Sie, ob der Arbeitsmappe ein neues Arbeitsblatt mit dem Namen **Imported Data** hinzugefügt wurde. Überprüfen Sie auch, ob die Zelle A1 die Zeichenfolge **This is my data** enthält.  
  
9. Beenden Sie Excel.  
  
## Nächste Schritte  
 In den folgenden Themen erhalten Sie weitere Informationen zum Programmieren von VSTO\-Add\-Ins:  
  
-   Verwenden Sie die `ThisAddIn`\-Klasse zum Automatisieren der Hostanwendung und zum Durchführen anderer Aufgaben in VSTO\-Add\-In\-Projekten. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Erstellen Sie einen benutzerdefinierten Aufgabenbereich in einem VSTO\-Add\-In. Weitere Informationen finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md) und [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Passen Sie das Menüband in einem VSTO\-Add\-In an. Weitere Informationen finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md) und [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## Siehe auch  
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  