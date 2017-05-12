---
title: "Gewusst wie: Hinzuf&#252;gen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung"
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
  - "Benutzerdefinierte Aufgabenbereiche [Office-Entwicklung in Visual Studio], Hinzufügen zur Anwendung"
  - "Aufgabenbereiche [Office-Entwicklung in Visual Studio], Hinzufügen zur Anwendung"
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Gewusst wie: Hinzuf&#252;gen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung
  Sie können den oben aufgeführten Anwendungen mithilfe des VSTO\-Add\-Ins einen benutzerdefinierten Aufgabenbereich hinzufügen.  Weitere Informationen finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Diese Elemente sind von der jeweiligen Visual Studio\-Version und den verwendeten Einstellungen abhängig.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung  
  
#### So fügen Sie einer Anwendung einen benutzerdefinierten Aufgabenbereich hinzu  
  
1.  Öffnen oder erstellen Sie ein VSTO\-Add\-In\-Projekt für eine der oben aufgeführten Anwendungen.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
3.  Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen des neuen Benutzersteuerelements in **MyUserControl**, und klicken Sie dann auf **Hinzufügen**.  
  
     Das Benutzersteuerelement wird im Designer geöffnet.  
  
4.  Fügen Sie dem Benutzersteuerelement mindestens ein Windows Forms\-Steuerelement aus der**Toolbox** hinzu.  
  
5.  Öffnen Sie die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb**.  
  
6.  Fügen Sie der `ThisAddIn`\-Klasse folgenden Code hinzu.  Dieser Code deklariert Instanzen von `MyUserControl` und <xref:Microsoft.Office.Tools.CustomTaskPane> als Member der `ThisAddIn`\-Klasse.  
  
     [!code-csharp[Trin_TaskPaneBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#1)]  
  
7.  Fügen Sie dem `ThisAddIn_Startup`\-Ereignishandler den folgenden Code hinzu.  Durch diesen Code wird ein neuer <xref:Microsoft.Office.Tools.CustomTaskPane> erstellt, indem der `CustomTaskPanes`\-Auflistung das `MyUserControl`\-Objekt hinzugefügt wird.  Durch den Code wird auch der Aufgabenbereich angezeigt.  
  
     [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
    > [!NOTE]  
    >  Durch diesen Code wird dem aktiven Fenster in der Anwendung der benutzerdefinierte Aufgabenbereich zugeordnet.  Bei einigen Anwendungen ist es u. U. sinnvoll, diesen Code zu ändern, um sicherzustellen, dass der Aufgabenbereich mit anderen Dokumenten oder Elementen in der Anwendung angezeigt wird.  Weitere Informationen finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
## Siehe auch  
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)   
 [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  