---
title: "Gewusst wie: &#196;ndern der Gr&#246;&#223;e von Bookmark-Steuerelementen"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Größenänderung"
  - "Bookmark-Steuerelement, Größenänderung"
ms.assetid: 3de1c774-921a-4113-a54a-e3b8d4a65d53
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Gewusst wie: &#196;ndern der Gr&#246;&#223;e von Bookmark-Steuerelementen
  Die Größe eines <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelements legen Sie fest, wenn Sie es einem Microsoft Office Word\-Dokument hinzufügen. Sie können dessen Größe aber auch zu einem späteren Zeitpunkt ändern.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Es gibt drei Möglichkeiten, die Größe eines Lesezeichens zu ändern:  
  
-   Hinzufügen von Text zu oder Entfernen von Text aus dem <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement.  
  
     Immer dann, wenn Sie einem Lesezeichen Text hinzufügen, wird es automatisch vergrößert, damit es den neuen Text enthält. Wenn Sie Text löschen, wird das Lesezeichen automatisch verkleinert.  
  
-   Ändern der <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>\- und der <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>\-Eigenschaft des <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelements.  
  
     Dies bietet sich an, wenn Sie die Größe nur um wenige Zeichen ändern.  
  
-   Neuerstellen des <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelements.  
  
     Dies bietet sich an, wenn sich die Größe oder die Position des Lesezeichens wesentlich geändert hat.  
  
 In Projekten auf Dokumentebene können Sie dem Dokument in Ihrem Projekt zur Entwurfs\- oder Laufzeit <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelemente hinzufügen. In VSTO\-Add\-In\-Projekten können Sie einem beliebigen geöffneten Dokument zur Laufzeit <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelemente hinzufügen. Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Ändern der Start\- und der End\-Eigenschaft  
  
#### So ändern Sie zur Entwurfszeit die Größe eines Lesezeichens in einem Projekt auf Dokumentebene  
  
1.  Wählen Sie das Lesezeichen im Fenster **Eigenschaften** aus.  
  
2.  Vergrößern oder verkleinern Sie den Wert der <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>\-Eigenschaft.  
  
3.  Vergrößern oder verkleinern Sie den Wert der <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>\-Eigenschaft.  
  
#### So ändern Sie zur Laufzeit die Größe eines Lesezeichens in einem Projekt auf Dokumentebene  
  
1.  Ändern Sie die <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>\- und die <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>\-Eigenschaft eines <xref:Microsoft.Office.Tools.Word.Bookmark>\-Objekts, das Sie zur Laufzeit oder zur Entwurfszeit erstellt haben.  
  
     Im folgenden Codebeispiel werden dem Anfang eines Lesezeichens namens `SampleBookmark` fünf Zeichen hinzugefügt. Für diesen Code wird davon ausgegangen, dass sich vor dem Lesezeichen mindestens fünf Textzeichen befinden.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#2)]  
  
     Im folgenden Codebeispiel werden am Ende desselben Lesezeichens fünf Zeichen hinzugefügt. Für diesen Code wird davon ausgegangen, dass sich hinter dem Lesezeichen mindestens fünf Textzeichen befinden.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#3)]  
  
#### So ändern Sie zur Laufzeit die Größe eines Lesezeichens in einem VSTO\-Add\-In\-Projekt  
  
1.  Ändern Sie die <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>\- und die <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>\-Eigenschaft eines <xref:Microsoft.Office.Tools.Word.Bookmark>\-Objekts, das Sie zur Laufzeit erstellt haben.  
  
     Im folgenden Codebeispiel wird ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Objekt erstellt, das den Text aus dem ersten Absatz des aktiven Dokuments enthält. Anschließend werden am Anfang und am Ende des <xref:Microsoft.Office.Tools.Word.Bookmark>\-Objekts fünf Zeichen entfernt.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_WordAddInDynamicControls#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#16)]  
  
## Neuerstellen des Lesezeichens  
 Sie können die Größe eines Lesezeichens in einem Projekt auf Dokumentebene ändern, indem Sie ein neues Lesezeichen hinzufügen, das denselben Namen wie das vorhandene Lesezeichen, aber eine andere Größe hat.  
  
#### So erstellen Sie zur Entwurfszeit ein Lesezeichen in einem Projekt auf Dokumentebene  
  
1.  Markieren Sie den Text, der in das neue <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement eingefügt werden soll.  
  
2.  Klicken Sie im Menü **Einfügen** auf **Lesezeichen**.  
  
3.  Geben Sie im Dialogfeld **Lesezeichen** den Namen des Lesezeichens ein, dessen Größe Sie ändern möchten, und klicken Sie auf **Hinzufügen**.  
  
## Siehe auch  
 [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Gewusst wie: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)   
 [Gewusst wie: Ändern der Größe von ListObject-Steuerelementen](../vsto/how-to-resize-listobject-controls.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  