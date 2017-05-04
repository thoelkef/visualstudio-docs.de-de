---
title: "Gewusst wie: Hinzuf&#252;gen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen | Microsoft Docs"
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
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Hinzufügen von Steuerelementen"
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Erstellen in Word"
  - "SmartDocuments [Office-Entwicklung in Visual Studio], Hinzufügen von Steuerelementen"
  - "SmartDocuments [Office-Entwicklung in Visual Studio], Erstellen in Word"
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Gewusst wie: Hinzuf&#252;gen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen
  Um Aktionsbereich einem Microsoft Office Word\-Dokument oder eine Microsoft Excel\-Arbeitsmappe hinzuzufügen, erstellen Sie zuerst ein Windows Forms\-Benutzersteuerelement.  Fügen Sie dann das Benutzersteuerelement der <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>\-Eigenschaft des `ThisDocument.ActionsPane` Felds \(Word\) oder des `ThisWorkbook.ActionsPane` Felds \(Excel\) im Projekt hinzu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Erstellen des Benutzersteuerelements  
 Im folgenden Verfahren wird veranschaulicht, wie ein Benutzersteuerelement in Word oder in einem Excel\-Projekt erstellt.  Außerdem wird dem Benutzersteuerelement eine Schaltfläche hinzugefügt, das Text auf das Dokument oder die Arbeitsmappe schreibt, wenn darauf geklickt wird.  
  
#### So erstellen Sie das Benutzersteuerelement  
  
1.  Öffnen Sie das Projekt für Word oder Excel auf Dokumentebene in Visual Studio.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Aktionsbereich\-Steuerelement**, nennen Sie es **HelloControl**, und klicken Sie auf **Hinzufügen**.  
  
    > [!NOTE]  
    >  Sie können dem Projekt alternativ ein Benutzersteuerelement hinzufügen.  Die vom Aktionsbereich\-Steuerelement generierten Klassen und Benutzersteuerelemente sind funktional äquivalent.  
  
4.  Ziehen Sie von der Registerkarte **Windows Forms** der **Toolbox** ein **Button**\-Steuerelement auf das Steuerelement.  
  
    > [!NOTE]  
    >  Wenn das Steuerelement im Designer nicht angezeigt wird, doppelklicken Sie im **Projektmappen\-Explorer** auf **HelloControl**.  
  
5.  Fügen Sie den Code <xref:System.Windows.Forms.Control.Click> dem \- Ereignishandler der Schaltfläche hinzu.  Das folgende Beispiel zeigt Code für ein Microsoft Office Word\-Dokument.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/HelloControl.vb#12)]  
  
6.  In C\# müssen Sie einen Ereignishandler für Klickereignisse auf Schaltflächen hinzufügen.  Sie können diesen Code nach dem Aufruf von `IntializeComponent` in den `HelloControl`\-Konstruktor einfügen.  
  
     Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#13)]  
  
## Hinzufügen des Benutzersteuerelements zum Aktionsbereich  
 Um den Aktionsbereich anzuzeigen, fügen Sie das Benutzersteuerelement der <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>\-Eigenschaft des `ThisDocument.ActionsPane` Felds \(Word\) oder des Felds `ThisWorkbook.ActionsPane` hinzu \(Excel\).  
  
#### So fügen Sie dem Aktionsbereich das Benutzersteuerelement hinzu  
  
1.  Fügen Sie den folgenden Code der `ThisDocument` oder `ThisWorkbook`\-Klasse als Deklaration auf Klassenebene hinzu \(fügen Sie diesen Code nicht zu einer Methode hinzu\).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#14)]  
  
2.  Fügen Sie folgenden Code zum \- Ereignishandler der `ThisDocument_Startup``ThisDocument`\-Klasse oder dem `ThisWorkbook_Startup`\-Ereignishandler der `ThisWorkbook`\-Klasse hinzu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#15)]  
  
## Siehe auch  
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Gewusst wie: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  