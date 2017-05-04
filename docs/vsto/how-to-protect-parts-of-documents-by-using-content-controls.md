---
title: "Gewusst wie: Sch&#252;tzen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen | Microsoft Docs"
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
  - "Inhaltssteuerelemente [Office-Entwicklung in Visual Studio], Dokumentschutz"
  - "Dokumentschutz [Office-Entwicklung in Visual Studio]"
  - "GroupContentControl"
  - "Teilweiser Dokumentschutz [Office-Entwicklung in Visual Studio]"
  - "Eingeschränkte Berechtigungen [Office-Entwicklung in Visual Studio]"
  - "Word [Office-Entwicklung in Visual Studio], Teilweiser Dokumentschutz"
  - "Word [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
ms.assetid: 50d7286a-7746-446f-8eef-06ceeadc94d0
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Gewusst wie: Sch&#252;tzen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen
  Wenn Sie einen Teil eines Dokuments schützen, verhindern Sie, dass Benutzer Inhalte in diesem Teil des Dokuments ändern oder löschen.  Es gibt mehrere Möglichkeiten, Teile eines Microsoft Office Word\-Dokuments mithilfe von Inhaltssteuerelementen zu schützen.  
  
-   Sie können ein Inhaltssteuerelement schützen.  
  
-   Sie können einen Teil eines Dokuments schützen, der nicht in einem Inhaltssteuerelement enthalten ist.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Schützen eines Inhaltssteuerelements  
 Sie können verhindern, dass Benutzer ein Inhaltssteuerelement bearbeiten oder löschen, indem Sie Eigenschaften des Steuerelements in einem Projekt auf Dokumentebene zur Entwurfszeit oder zur Laufzeit festlegen.  
  
 Sie können auch Inhaltssteuerelemente schützen, die Sie einem Dokument zur Laufzeit hinzufügen, indem Sie ein VSTO\-Add\-In\-Projekt verwenden.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
#### So schützen Sie ein Inhaltssteuerelement zur Entwurfszeit  
  
1.  Wählen Sie in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Designer gehosteten Dokument das Inhaltssteuerelement aus, das Sie schützen möchten.  
  
2.  Legen Sie im Fenster **Eigenschaften** eine oder beide der folgenden Eigenschaften fest:  
  
    -   Um zu verhindern, dass Benutzer das Steuerelement bearbeiten, legen Sie **LockContents** auf **True** fest.  
  
    -   Um zu verhindern, dass Benutzer das Steuerelement löschen, legen Sie **LockContentControl** auf **True** fest.  
  
3.  Klicken Sie auf **OK**.  
  
#### So schützen Sie ein Inhaltssteuerelement zur Laufzeit  
  
1.  Legen Sie die `LockContents`\-Eigenschaft des Inhaltssteuerelements auf **true** fest, um zu verhindern, dass Benutzer das Steuerelement bearbeiten, und legen Sie die `LockContentControl`\-Eigenschaft auf **true** fest, um zu verhindern, dass Benutzer das Steuerelement löschen.  
  
     Das folgende Codebeispiel veranschaulicht die Verwendung der <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A>\-Eigenschaft und <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A>\-Eigenschaft zwei verschiedener <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Objekte in einem Projekt auf Dokumentebene.  Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument`\-Klasse in Ihrem Projekt hinzu und rufen die `AddProtectedContentControls`\-Methode aus dem `ThisDocument_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#2)]  
  
     Das folgende Codebeispiel veranschaulicht die Verwendung der <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A>\-Eigenschaft und <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A>\-Eigenschaft zwei verschiedener <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Objekte in einem VSTO\-Add\-In\-Projekt.  Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn`\-Klasse in Ihrem Projekt hinzu und rufen die `AddProtectedContentControls`\-Methode aus dem `ThisAddIn_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_WordAddInDynamicControls#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#14)]  
  
## Schützen eines Teils eines Dokuments, der nicht in einem Inhaltssteuerelement enthalten ist  
 Sie können verhindern, dass Benutzer einen Bereich eines Dokuments ändern, indem Sie ihn in <xref:Microsoft.Office.Tools.Word.GroupContentControl> einfügen.  Dies ist in den folgenden Szenarien nützlich:  
  
-   Sie möchten einen Bereich schützen, der keine Inhaltssteuerelemente enthält.  
  
-   Sie möchten einen Bereich schützen, der bereits Inhaltssteuerelemente enthält, während der Text oder andere Elemente, die Sie schützen möchten, nicht in den Inhaltssteuerelementen enthalten sind.  
  
> [!NOTE]  
>  Wenn Sie ein <xref:Microsoft.Office.Tools.Word.GroupContentControl> erstellen, das eingebettete Inhaltssteuerelemente enthält, sind die eingebetteten Inhaltssteuerelemente nicht automatisch geschützt.  Verwenden Sie die **LockContents**\-Eigenschaft des Steuerelements, um zu verhindern, dass Benutzer ein eingebettetes Inhaltssteuerelement bearbeiten.  
  
#### So schützen Sie einen Bereich eines Dokuments zur Entwurfszeit  
  
1.  Wählen Sie in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Designer gehosteten Dokument den Bereich aus, den Sie schützen möchten.  
  
2.  Klicken Sie im Menüband auf die Registerkarte **Entwickler**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  Klicken Sie in der Gruppe **Steuerelemente** auf die Dropdownschaltfläche **Gruppe**, und klicken Sie dann auf **Gruppe**.  
  
     In der `ThisDocument`\-Klasse in Ihrem Projekt wird automatisch ein <xref:Microsoft.Office.Tools.Word.GroupContentControl> generiert, das den geschützten Bereich enthält.  Zur Entwurfszeit wird ein Rahmen angezeigt, der das Gruppensteuerelement darstellt, der zur Laufzeit allerdings nicht sichtbar ist.  
  
#### So schützen Sie einen Bereich eines Dokuments zur Laufzeit  
  
1.  Wählen Sie den zu schützenden Bereich programmgesteuert aus, und rufen Sie dann die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A>\-Methode auf, um <xref:Microsoft.Office.Tools.Word.GroupContentControl> zu erstellen.  
  
     Im folgenden Codebeispiel für ein Projekt auf Dokumentebene wird dem ersten Absatz des Dokuments Text hinzugefügt, der erste Absatz ausgewählt und dann <xref:Microsoft.Office.Tools.Word.GroupContentControl> instanziiert.  Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument`\-Klasse in Ihrem Projekt hinzu und rufen die `ProtectFirstParagraph`\-Methode aus dem `ThisDocument_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#1)]  
  
     Im folgenden Codebeispiel für ein VSTO\-Add\-In\-Projekt wird dem ersten Absatz des aktiven Dokuments Text hinzugefügt, der erste Absatz ausgewählt und dann <xref:Microsoft.Office.Tools.Word.GroupContentControl> instanziiert.  Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn`\-Klasse in Ihrem Projekt hinzu und rufen die `ProtectFirstParagraph`\-Methode aus dem `ThisAddIn_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_WordAddInDynamicControls#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#15)]  
  
## Siehe auch  
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Inhaltssteuerelemente](../vsto/content-controls.md)   
 [Gewusst wie: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  