---
title: "Exemplarische Vorgehensweise: Erstellen einer Vorlage mithilfe von Inhaltssteuerelementen"
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
  - "Bausteine [Office-Entwicklung in Visual Studio]"
  - "Inhaltssteuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Dokumenten"
  - "Word [Office-Entwicklung in Visual Studio], Erstellen von Dokumenten"
ms.assetid: 88fb9a60-dcc3-4a5f-a8c9-7aff01ca4b4b
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Exemplarische Vorgehensweise: Erstellen einer Vorlage mithilfe von Inhaltssteuerelementen
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine Anpassung auf Dokumentebene erstellt wird, die Inhaltssteuerelemente zum Erstellen strukturierter und wiederverwendbarer Inhalte in einer Microsoft Office Word\-Vorlage verwendet.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Mithilfe von Word können Sie eine Auflistung wiederverwendbarer Dokumentbausteine erstellen, die als *Bausteine* bezeichnet werden.  Diese exemplarische Vorgehensweise veranschaulicht, wie zwei Tabellen als Bausteine erstellt werden.  Jede Tabelle enthält mehrere Inhaltssteuerelemente, die unterschiedliche Inhaltstypen aufweisen können, z. B. reinen Text oder Datumsangaben.  Eine der Tabellen enthält Informationen über einen Mitarbeiter und die andere Kundenfeedback.  
  
 Nachdem Sie ein Dokument von der Vorlage erstellt haben, können Sie ihm mithilfe mehrerer <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>\-Objekte, die die verfügbaren Bausteine in der Vorlage anzeigen, eine der beiden Tabellen hinzufügen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen von Tabellen, die Inhaltssteuerelemente in einer Word\-Vorlage enthalten, zur Entwurfszeit  
  
-   Programmgesteuertes Auffüllen eines Kombinationsfeld\-Inhaltssteuerelements und eines Dropdownlisten\-Inhaltssteuerelements  
  
-   Verhindern, dass Benutzer eine bestimmte Tabelle bearbeiten  
  
-   Hinzufügen von Tabellen zur Bausteinauflistung einer Vorlage  
  
-   Erstellen eines Inhaltssteuerelements, das die verfügbaren Bausteine in der Vorlage anzeigt  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Erstellen eines neuen Word\-Vorlagenprojekts  
 Erstellen Sie eine Word\-Vorlage, damit Benutzer leicht eigene Kopien erstellen können.  
  
#### So erstellen Sie ein neues Word\-Vorlagenprojekt  
  
1.  Erstellen Sie ein Word\-Vorlagenprojekt mit dem Namen "MyBuildingBlockTemplate".  Erstellen Sie im Assistenten ein neues Dokument in der Projektmappe.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die neue Word\-Vorlage im Designer und fügt dem **Projektmappen\-Explorer** das Projekt **MyBuildingBlockTemplate** hinzu.  
  
## Erstellen der Mitarbeitertabelle  
 Erstellen Sie eine Tabelle, die vier verschiedene Typen von Inhaltssteuerelementen enthält, in denen der Benutzer Informationen zu einem Mitarbeiter eingeben kann.  
  
#### So erstellen Sie die Mitarbeitertabelle  
  
1.  Klicken Sie in der Word\-Vorlage, die im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Designer gehostet wird, im Menüband auf die Registerkarte **Einfügen**.  
  
2.  Klicken Sie in der Gruppe **Tabellen** auf **Tabelle**, und fügen Sie eine Tabelle mit 2 Spalten und 4 Zeilen ein.  
  
3.  Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:  
  
    ||  
    |-|  
    |Employee Name|  
    |Hire Date|  
    |Title|  
    |Picture|  
  
4.  Klicken Sie in die erste Zelle in der zweiten Spalte \(neben**Employee Name**\).  
  
5.  Klicken Sie im Menüband auf die Registerkarte **Entwickler**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Klicken Sie in der Gruppe **Steuerelemente** auf die Schaltfläche **Text** ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl"), um der ersten Zelle <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> hinzuzufügen.  
  
7.  Klicken Sie in die zweite Zelle in der zweiten Spalte \(neben**Hire Date**\).  
  
8.  Klicken Sie in der Gruppe **Steuerelemente** auf die Schaltfläche **Datumsauswahl** ![DatePickerContentControl](../vsto/media/datepicker.png "DatePickerContentControl"), um der zweiten Zelle <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> hinzuzufügen.  
  
9. Klicken Sie in die dritte Zelle in der zweiten Spalte \(neben**Title**\).  
  
10. Klicken Sie in der Gruppe **Steuerelemente** auf die Schaltfläche **Kombinationsfeld** ![ComboBoxContentControl](../vsto/media/combobox.png "ComboBoxContentControl"), um der dritten Zelle <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> hinzuzufügen.  
  
11. Klicken Sie in die letzte Zelle in der zweiten Spalte \(neben**Picture**\).  
  
12. Klicken Sie in der Gruppe **Steuerelemente** auf die Schaltfläche **Bild\-Inhaltssteuerelement** ![PictureContentControl](../vsto/media/pictcontentcontrol.png "PictureContentControl"), um der letzten Zelle <xref:Microsoft.Office.Tools.Word.PictureContentControl> hinzuzufügen.  
  
## Erstellen der Kundenfeedback\-Tabelle  
 Erstellen Sie eine Tabelle, die drei verschiedene Typen von Inhaltssteuerelementen enthält, in der der Benutzer Informationen zu Kundenfeedback eingeben kann.  
  
#### So erstellen Sie die Kundenfeedback\-Tabelle  
  
1.  Klicken Sie in der Word\-Vorlage in die Zeile nach der Mitarbeitertabelle, die Sie zuvor hinzugefügt haben, und drücken Sie EINGABE, um einen neuen Absatz hinzuzufügen.  
  
2.  Klicken Sie im Menüband auf die Registerkarte **Einfügen**.  
  
3.  Klicken Sie in der Gruppe **Tabellen** auf **Tabelle**, und fügen Sie eine Tabelle mit 2 Spalten und 3 Zeilen ein.  
  
4.  Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:  
  
    ||  
    |-|  
    |Customer Name|  
    |Satisfaction Rating|  
    |Comments|  
  
5.  Klicken Sie in die erste Zelle der zweiten Spalte \(neben**Customer Name**\).  
  
6.  Klicken Sie im Menüband auf die Registerkarte **Entwickler**.  
  
7.  Klicken Sie in der Gruppe **Steuerelemente** auf die Schaltfläche **Text** ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl"), um der ersten Zelle <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> hinzuzufügen.  
  
8.  Klicken Sie in die zweite Zelle der zweiten Spalte \(neben**Satisfaction Rating**\).  
  
9. Klicken Sie in der Gruppe **Steuerelemente** auf die Schaltfläche **Dropdownliste** ![DropDownListContentControl](../vsto/media/dropdownlist.png "DropDownListContentControl"), um der zweiten Zelle <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> hinzuzufügen.  
  
10. Klicken Sie in die letzte Zelle der zweiten Spalte \(neben **Comments**\).  
  
11. Klicken Sie in der Gruppe **Steuerelemente** auf die Schaltfläche **Rich\-Text** ![RichTextContentControl](../vsto/media/richtextcontrol.png "RichTextContentControl"), um der letzten Zelle <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen.  
  
## Programmgesteuertes Auffüllen des Kombinationsfelds und der Dropdownliste  
 Sie können Inhaltssteuerelemente zur Entwurfszeit über das Fenster **Eigenschaften** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] initialisieren.  Sie können sie auch zur Laufzeit initialisieren, wodurch Sie deren Anfangszustände dynamisch festlegen können.  In dieser exemplarischen Vorgehensweise verwenden Sie Code zum Auffüllen der Einträge in <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> und <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> zur Laufzeit, damit Sie sehen können, wie diese Objekte funktionieren.  
  
#### So ändern Sie die Benutzeroberfläche der Inhaltssteuerelemente programmgesteuert  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **ThisDocument.cs** oder **ThisDocument.vb**, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Fügen Sie der `ThisDocument`\-Klasse folgenden Code hinzu.  Dieser Code deklariert mehrere Objekte, die Sie später in dieser exemplarischen Vorgehensweise verwenden.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  Fügen Sie der `ThisDocument_Startup`\-Methode der `ThisDocument`\-Klasse den folgenden Code hinzu.  Durch diesen Code werden <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> und <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> in den Tabellen Einträge hinzugefügt und der Platzhaltertext festgelegt, der in den einzelnen Steuerelementen angezeigt wird, bevor sie vom Benutzer bearbeitet werden.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#2)]  
  
## Verhindern, dass Benutzer die Mitarbeitertabelle bearbeiten  
 Verwenden Sie das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.GroupContentControl>\-Objekt, um die Mitarbeitertabelle zu schützen.  Nachdem Sie die Tabelle geschützt haben, können Benutzer die Inhaltssteuerelemente in der Tabelle immer noch bearbeiten.  Allerdings können sie in der ersten Spalte keinen Text bearbeiten oder die Tabelle auf andere Weise ändern, z. B. Zeilen und Spalten hinzufügen oder löschen.  Weitere Informationen dazu, wie Sie Teile eines Dokuments mithilfe von <xref:Microsoft.Office.Tools.Word.GroupContentControl> schützen, finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
#### So verhindern Sie, dass Benutzer die Mitarbeitertabelle bearbeiten  
  
1.  Fügen Sie der `ThisDocument_Startup`\-Methode der `ThisDocument`\-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu.  Dieser Code verhindert, dass Benutzer die Mitarbeitertabelle bearbeiten, indem die Tabelle in das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.GroupContentControl>\-Objekt eingefügt wird.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#3)]  
  
## Hinzufügen der Tabellen zur Bausteinauflistung  
 Fügen Sie die Tabellen einer Auflistung von Dokumentbausteinen in der Vorlage hinzu, sodass Benutzer die Tabellen, die Sie erstellt haben, in das Dokument einfügen können.  Weitere Informationen zu Dokumentbausteinen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
#### So fügen Sie die Tabellen den Bausteinen in der Vorlage hinzu  
  
1.  Fügen Sie der `ThisDocument_Startup`\-Methode der `ThisDocument`\-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu.  Durch diesen Code werden neue Bausteine, die die Tabellen enthalten, der Microsoft.Office.Interop.Word.BuildingBlockEntries\-Auflistung hinzugefügt, die alle wiederverwendbaren Bausteine in der Vorlage enthält.  Die neuen Bausteine werden in einer neuen Kategorie mit dem Namen **Employee and Customer Information** definiert, und ihnen wird der Bausteintyp Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1 zugewiesen.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#4)]  
  
2.  Fügen Sie der `ThisDocument_Startup`\-Methode der `ThisDocument`\-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu.  Dieser Code löscht die Tabellen aus der Vorlage.  Die Tabellen sind nicht mehr erforderlich, da Sie sie dem Katalog wiederverwendbarer Bausteine in der Vorlage hinzugefügt haben.  Durch den Code wird das Dokument zuerst in den Entwurfsmodus versetzt, sodass die geschützte Mitarbeitertabelle gelöscht werden kann.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#5)]  
  
## Erstellen eines Inhaltssteuerelements, das die Bausteine anzeigt  
 Erstellen Sie ein Inhaltssteuerelement, das den Zugriff auf die Bausteine \(d. h. die Tabellen\) ermöglicht, die Sie zuvor erstellt haben.  Benutzer können auf dieses Steuerelement klicken, um die Tabellen dem Dokument hinzuzufügen.  
  
#### So erstellen Sie ein Inhaltssteuerelement, das die Bausteine anzeigt  
  
1.  Fügen Sie der `ThisDocument_Startup`\-Methode der `ThisDocument`\-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu.  Dieser Code initialisiert das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>\-Objekt.  In <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> werden alle Bausteine angezeigt, die in der Kategorie **Employee and Customer Information** definiert sind und über den Bausteintyp Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1 verfügen.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#6)]  
  
## Testen des Projekts  
 Benutzer können auf die Steuerelemente im Bausteinkatalog im Dokument klicken, um die Mitarbeiter\- oder Kundenfeedback\-Tabelle einzufügen.  Benutzer können in den Inhaltssteuerelementen in beiden Tabellen Antworten eingeben oder auswählen.  Benutzer können andere Teile der Kundenfeedback\-Tabelle ändern, sollten aber nicht in der Lage sein, andere Teile der Mitarbeitertabelle zu ändern.  
  
#### So testen Sie die Mitarbeitertabelle  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Klicken Sie auf **Ersten Baustein auswählen**, um das erste Inhaltssteuerelement aus dem Bausteinkatalog anzuzeigen.  
  
3.  Klicken Sie auf den Dropdownpfeil neben der Überschrift **Benutzerdefinierter Katalog 1** im Steuerelement, und wählen Sie **Employee Table** aus.  
  
4.  Klicken Sie in die Zelle rechts neben der Zelle "Employee Name", und geben Sie einen Namen ein.  
  
     Stellen Sie sicher, dass Sie dieser Zelle nur Text hinzufügen können.  <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> ermöglicht es Benutzern, nur Text und keine anderen Inhaltstypen wie Grafiken oder Tabellen hinzuzufügen.  
  
5.  Klicken Sie in die Zelle rechts neben der Zelle "Hire Date", und wählen Sie in der Datumsauswahl ein Datum aus.  
  
6.  Klicken Sie in die Zelle rechts neben der Zelle "Title", und wählen Sie im Kombinationsfeld eine der Berufsbezeichnungen aus.  
  
     Geben Sie optional eine Berufsbezeichnung ein, die nicht in der Liste enthalten ist.  Dies ist möglich, weil <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> Benutzern die Auswahl aus einer Liste von Einträgen oder die Eingabe eigener Einträge ermöglicht.  
  
7.  Klicken Sie auf das Symbol in der Zelle rechts neben der Zelle "Picture", und navigieren Sie zu einem Bild, um es anzuzeigen.  
  
8.  Versuchen Sie, der Tabelle Zeilen oder Spalten hinzuzufügen und Zeilen und Spalten aus der Tabelle zu löschen.  Vergewissern Sie sich, dass Sie die Tabelle nicht ändern können.  <xref:Microsoft.Office.Tools.Word.GroupContentControl> verhindert, dass Sie Änderungen vornehmen.  
  
#### So testen Sie die Kundenfeedback\-Tabelle  
  
1.  Klicken Sie auf **Zweiten Baustein auswählen**, um das zweite Inhaltssteuerelement aus dem Bausteinkatalog anzuzeigen.  
  
2.  Klicken Sie auf den Dropdownpfeil neben der Überschrift **Benutzerdefinierter Katalog 1** im Steuerelement, und wählen Sie **Customer Table** aus.  
  
3.  Klicken Sie in die Zelle rechts neben der Zelle "Customer Name", und geben Sie einen Namen ein.  
  
4.  Klicken Sie in die Zelle rechts neben der Zelle "Satisfaction Rating", und wählen Sie eine der verfügbaren Optionen aus.  
  
     Stellen Sie sicher, dass Sie ihren eigenen Eintrag nicht eingeben können.  <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ermöglicht Benutzern nur die Auswahl aus einer Liste von Einträgen.  
  
5.  Klicken Sie in die Zelle rechts neben der Zelle "Comments", und geben Sie Kommentare ein.  
  
     Fügen Sie optional andere Inhalte als Text hinzu, z. B. Grafiken oder eine eingebettete Tabelle.  Dies ist möglich, weil <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Benutzern das Hinzufügen anderer Inhalt als Text ermöglicht.  
  
6.  Vergewissern Sie sich, dass Sie der Tabelle Zeilen oder Spalten hinzufügen und Zeilen und Spalten aus der Tabelle löschen können.  Dies ist möglich, da Sie die Tabelle nicht geschützt haben, indem Sie sie in <xref:Microsoft.Office.Tools.Word.GroupContentControl> eingefügt haben.  
  
7.  Schließen Sie die Vorlage.  
  
## Nächste Schritte  
 Weitere Informationen zur Verwendung von Inhaltssteuerelementen finden Sie in diesem Thema:  
  
-   Binden von Inhaltssteuerelementen an XML\-Elemente \(werden auch als benutzerdefinierte XML\-Teile bezeichnet\), die in ein Dokument eingebettet sind  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## Siehe auch  
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Inhaltssteuerelemente](../vsto/content-controls.md)   
 [Gewusst wie: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Gewusst wie: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  