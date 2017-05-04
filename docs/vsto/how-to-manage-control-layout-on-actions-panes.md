---
title: "Gewusst wie: Verwalten des Steuerelementlayouts in Aktionsbereichen | Microsoft Docs"
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
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Steuerelementlayout"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Layout in Aktionsbereichen"
  - "SmartDocuments [Office-Entwicklung in Visual Studio], Steuerelementlayout"
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Gewusst wie: Verwalten des Steuerelementlayouts in Aktionsbereichen
  Standardmäßig wird ein Aktionsbereich an die rechte Seite eines Dokuments oder Arbeitsblatts angedockt. Er kann jedoch auch links, oben oder unten angedockt werden.  Wenn Sie mehrere Benutzersteuerelemente verwenden, können Sie Code schreiben, um die Benutzersteuerelemente im Aktionsbereich richtig zu stapeln.  Weitere Informationen finden Sie unter [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Die Stapelreihenfolge der Steuerelemente hängt davon ab, ob der Aktionsbereich vertikal oder horizontal angedockt ist.  
  
> [!NOTE]  
>  Sie können die Steuerelemente so einstellen, dass ihre Größe bei einer Änderung der Größe des Aktionsbereichs durch den Benutzer zur Laufzeit mit geändert wird.  Sie können die <xref:System.Windows.Forms.Control.Anchor%2A>\-Eigenschaft eines Windows Forms\-Steuerelements zum Verankern von Steuerelementen im Aktionsbereich verwenden.  Weitere Informationen finden Sie unter [Gewusst wie: Verankern von Steuerelementen in Windows Forms](../Topic/How%20to:%20Anchor%20Controls%20on%20Windows%20Forms.md).  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So legen Sie die Stapelreihenfolge der Aktionsbereich\-Steuerelemente fest  
  
1.  Öffnen Sie ein Projekt auf Dokumentebene für Microsoft Office Word, das einen Aktionsbereich mit mehreren Benutzersteuerelementen oder geschachtelten Aktionsbereich\-Steuerelementen umfasst.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **ThisDocument.cs** bzw. **ThisDocument.vb**, und klicken Sie dann auf **Code anzeigen**.  
  
3.  Überprüfen Sie im <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>\-Ereignishandler des Aktionsbereichs, ob der Aktionsbereich horizontal ausgerichtet ist.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#30)]  
  
4.  Bei horizontaler Ausrichtung des Aktionsbereichs stapeln Sie die Aktionsbereich\-Steuerelemente von links, sonst von oben.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#31)]  
  
5.  In C\# müssen Sie für das `ActionsPane`\-Element einen Ereignishandler zum <xref:Microsoft.Office.Tools.Word.Document.Startup>\-Ereignishandler hinzufügen.  Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#32)]  
  
6.  Führen Sie das Projekt aus, und stellen Sie sicher, dass die Aktionsbereich\-Steuerelemente von links nach rechts gestapelt werden, wenn der Aktionsbereich am oberen Rand des Dokuments angedockt ist, und von oben nach unten, wenn der Aktionsbereich am rechten Rand des Dokuments angedockt ist.  
  
## Beispiel  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#29)]  
  
## Kompilieren des Codes  
 Dieses Beispiel setzt Folgendes voraus:  
  
-   Ein Projekt auf Dokumentebene für Word mit einem Aktionsbereich, der mehrere Benutzersteuerelemente oder geschachtelte Aktionsbereich\-Steuerelemente umfasst.  
  
## Siehe auch  
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  