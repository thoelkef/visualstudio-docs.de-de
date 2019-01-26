---
title: 'Exemplarische Vorgehensweise: Erstellen Sie eine Vorlage mithilfe von Inhaltssteuerelementen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b2bc96a9df16c43c8fe4e66dbed4079a1ae3a40
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874174"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Exemplarische Vorgehensweise: Erstellen Sie eine Vorlage mithilfe von Inhaltssteuerelementen
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine Anpassung auf Dokumentebene erstellt wird, die Inhaltssteuerelemente zum Erstellen strukturierter und wiederverwendbarer Inhalte in einer Microsoft Office Word-Vorlage verwendet.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word können Sie eine Sammlung wiederverwendbarer Dokumentbausteine erstellen *Bausteine*. Diese exemplarische Vorgehensweise veranschaulicht, wie zwei Tabellen als Bausteine erstellt werden. Jede Tabelle enthält mehrere Inhaltssteuerelemente, die unterschiedliche Inhaltstypen aufweisen können, z. B. reinen Text oder Datumsangaben. Eine der Tabellen enthält Informationen über einen Mitarbeiter und die andere Kundenfeedback.  
  
 Nachdem Sie ein Dokument von der Vorlage erstellt haben, können Sie ihm mithilfe mehrerer <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>-Objekte, die die verfügbaren Bausteine in der Vorlage anzeigen, eine der beiden Tabellen hinzufügen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
- Erstellen von Tabellen, die Inhaltssteuerelemente in einer Word-Vorlage enthalten, zur Entwurfszeit  
  
- Programmgesteuertes Auffüllen eines Kombinationsfeld-Inhaltssteuerelements und eines Dropdownlisten-Inhaltssteuerelements  
  
- Verhindern, dass Benutzer eine bestimmte Tabelle bearbeiten  
  
- Hinzufügen von Tabellen zur Bausteinauflistung einer Vorlage  
  
- Erstellen eines Inhaltssteuerelements, das die verfügbaren Bausteine in der Vorlage anzeigt  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-a-new-word-template-project"></a>Erstellen Sie ein neues Word-Vorlagenprojekt  
 Erstellen Sie eine Word-Vorlage, damit Benutzer leicht eigene Kopien erstellen können.  
  
### <a name="to-create-a-new-word-template-project"></a>So erstellen Sie ein neues Word-Vorlagenprojekt  
  
1.  Erstellen Sie ein Word-Vorlagenprojekt mit dem Namen **MyBuildingBlockTemplate**. Erstellen Sie im Assistenten ein neues Dokument in der Projektmappe. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet die neue Word-Vorlage im Designer und fügt die **MyBuildingBlockTemplate** Projekt **Projektmappen-Explorer**.  
  
## <a name="create-the-employee-table"></a>Erstellen Sie die Employee-Tabelle  
 Erstellen Sie eine Tabelle, die vier verschiedene Typen von Inhaltssteuerelementen enthält, in denen der Benutzer Informationen zu einem Mitarbeiter eingeben kann.  
  
### <a name="to-create-the-employee-table"></a>So erstellen Sie die Mitarbeitertabelle  
  
1. In der Word-Vorlage, die in gehostet ist die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf dem Menüband-Designer, klicken Sie auf die **einfügen** Registerkarte.  
  
2. In der **Tabellen** auf **Tabelle**, und fügen Sie eine Tabelle mit zwei Spalten und vier Zeilen.  
  
3. Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:  
  
   ||  
   |-|  
   |**Name des Mitarbeiters**|  
   |**Einstellungsdatum**|  
   |**Titel**|  
   |**Bild**|  
  
4. Klicken Sie in der ersten Zelle in der zweiten Spalte (neben **Mitarbeiternamen**).  
  
5. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .  
  
   > [!NOTE]  
   >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. In der **Steuerelemente** gruppieren, klicken Sie auf die **Text** Schaltfläche ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") Hinzufügen einer <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>bis zur ersten Zelle.  
  
7. Klicken Sie auf der zweiten Zelle in der zweiten Spalte (neben **Hire Date**).  
  
8. In der **Steuerelemente** gruppieren, klicken Sie auf die **Datumsauswahl** Schaltfläche ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") eine Hinzufügen<xref:Microsoft.Office.Tools.Word.DatePickerContentControl> der zweiten Zelle.  
  
9. Klicken Sie auf die dritte Zelle in der zweiten Spalte (neben **Titel**).  
  
10. In der **Steuerelemente** gruppieren, klicken Sie auf die **Kombinationsfeld** Schaltfläche ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") Hinzufügen einer <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>der dritten Zelle.  
  
11. Klicken Sie auf die letzte Zelle in der zweiten Spalte (neben **Bild**).  
  
12. In der **Steuerelemente** gruppieren, klicken Sie auf die **Bild-Inhaltssteuerelement** Schaltfläche ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") Hinzufügen einer <xref:Microsoft.Office.Tools.Word.PictureContentControl> bis zur letzten Zelle.  
  
## <a name="create-the-customer-feedback-table"></a>Erstellen der Kundenfeedback-Tabelle  
 Erstellen Sie eine Tabelle, die drei verschiedene Typen von Inhaltssteuerelementen enthält, in der der Benutzer Informationen zu Kundenfeedback eingeben kann.  
  
### <a name="to-create-the-customer-feedback-table"></a>So erstellen Sie die Kundenfeedback-Tabelle  
  
1. Klicken Sie in der Word-Vorlage, klicken Sie in der Zeile nach der Employee-Tabelle, die Sie zuvor hinzugefügt haben, und drücken Sie **EINGABETASTE** um einen neuen Absatz hinzuzufügen.  
  
2. Klicken Sie auf dem Menüband auf die **einfügen** Registerkarte.  
  
3. In der **Tabellen** auf **Tabelle**, und fügen Sie eine Tabelle mit zwei Spalten und drei Zeilen.  
  
4. Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:  
  
   ||  
   |-|  
   |**Kundenname**|  
   |**Die Zufriedenheit**|  
   |**Kommentare**|  
  
5. Klicken Sie in der ersten Zelle der zweiten Spalte (neben **Kundenname**).  
  
6. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .  
  
7. In der **Steuerelemente** gruppieren, klicken Sie auf die **Text** Schaltfläche ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") Hinzufügen einer <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>bis zur ersten Zelle.  
  
8. Klicken Sie in der zweiten Zelle der zweiten Spalte (neben **Satisfaction Rating**).  
  
9. In der **Steuerelemente** gruppieren, klicken Sie auf die **Dropdown-Listenfeld** Schaltfläche ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") Hinzufügen einer <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> der zweiten Zelle.  
  
10. Klicken Sie in der letzten Zelle der zweiten Spalte (neben **Kommentare**).  
  
11. In der **Steuerelemente** gruppieren, klicken Sie auf die **Rich-Text** Schaltfläche ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") Hinzufügen einer <xref:Microsoft.Office.Tools.Word.RichTextContentControl>bis zur letzten Zelle.  
  
## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Füllen Sie das Kombinationsfeld und Dropdown-Listenfeld programmgesteuert  
 Sie können Inhaltssteuerelemente zur Entwurfszeit zu initialisieren, mit der **Eigenschaften** -Fensters im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Sie können auch diese zur Laufzeit initialisieren, die Sie deren Anfangszustände dynamisch festlegen können. In dieser exemplarischen Vorgehensweise verwenden Sie Code zum Auffüllen der Einträge in der <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> und <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> zur Laufzeit, damit Sie sehen können, wie diese Objekte funktionieren.  
  
### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>So ändern Sie die Benutzeroberfläche der Inhaltssteuerelemente programmgesteuert  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **ThisDocument.cs** oder **ThisDocument.vb**, und klicken Sie dann auf **Ansichtscode**.  
  
2.  Fügen Sie der `ThisDocument` -Klasse folgenden Code hinzu. Dieser Code deklariert mehrere Objekte, die Sie später in dieser exemplarischen Vorgehensweise verwenden.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse den folgenden Code hinzu. Durch diesen Code werden <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> und <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> in den Tabellen Einträge hinzugefügt und der Platzhaltertext festgelegt, der in den einzelnen Steuerelementen angezeigt wird, bevor sie vom Benutzer bearbeitet werden.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="prevent-users-from-editing-the-employee-table"></a>Verhindern Sie, dass Benutzer die Mitarbeitertabelle bearbeiten  
 Verwenden Sie das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.GroupContentControl>-Objekt, um die Mitarbeitertabelle zu schützen. Nachdem Sie die Tabelle geschützt haben, können Benutzer die Inhaltssteuerelemente in der Tabelle immer noch bearbeiten. Allerdings können sie in der ersten Spalte keinen Text bearbeiten oder die Tabelle auf andere Weise ändern, z. B. Zeilen und Spalten hinzufügen oder löschen. Weitere Informationen zur Verwendung einer <xref:Microsoft.Office.Tools.Word.GroupContentControl> einen Teil eines Dokuments schützen, finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
### <a name="to-prevent-users-from-editing-the-employee-table"></a>So verhindern Sie, dass Benutzer die Mitarbeitertabelle bearbeiten  
  
1.  Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu. Dieser Code verhindert, dass Benutzer die Mitarbeitertabelle bearbeiten, indem die Tabelle in das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.GroupContentControl>-Objekt eingefügt wird.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="add-the-tables-to-the-building-block-collection"></a>Fügen Sie Tabellen bausteinauflistung  
 Fügen Sie die Tabellen einer Auflistung von Dokumentbausteinen in der Vorlage hinzu, sodass Benutzer die Tabellen, die Sie erstellt haben, in das Dokument einfügen können. Weitere Informationen zu Dokumentbausteinen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>So fügen Sie die Tabellen den Bausteinen in der Vorlage hinzu  
  
1.  Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu. Dieser Code fügt die neuen Bausteine, die die Tabellen in der Auflistung Microsoft.Office.Interop.Word.BuildingBlockEntries enthalten, die alle wiederverwendbaren Bausteine in der Vorlage enthält. Die neuen Bausteine werden in eine neue Kategorie mit dem Namen definiert **Employee and Customer Information** und den Bausteintyp zugewiesen sind `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu. Dieser Code löscht die Tabellen aus der Vorlage. Die Tabellen sind nicht mehr erforderlich, da Sie sie dem Katalog wiederverwendbarer Bausteine in der Vorlage hinzugefügt haben. Durch den Code wird das Dokument zuerst in den Entwurfsmodus versetzt, sodass die geschützte Mitarbeitertabelle gelöscht werden kann.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Erstellen Sie ein Inhaltssteuerelement, das die Bausteine anzeigt  
 Erstellen Sie ein Inhaltssteuerelement, das den Zugriff auf die Bausteine (d. h. die Tabellen) ermöglicht, die Sie zuvor erstellt haben. Benutzer können auf dieses Steuerelement klicken, um die Tabellen dem Dokument hinzuzufügen.  
  
### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>So erstellen Sie ein Inhaltssteuerelement, das die Bausteine anzeigt  
  
1.  Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu. Dieser Code initialisiert das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>-Objekt. Die <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> zeigt alle Bausteine, die in der Kategorie definiert sind **Employee and Customer Information** und bei denen den Bausteintyp `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="test-the-project"></a>Testen Sie das Projekt  
 Benutzer können auf die Steuerelemente im Bausteinkatalog im Dokument klicken, um die Mitarbeiter- oder Kundenfeedback-Tabelle einzufügen. Benutzer können in den Inhaltssteuerelementen in beiden Tabellen Antworten eingeben oder auswählen. Benutzer können andere Teile der Kundenfeedback-Tabelle ändern, sollten aber nicht in der Lage sein, andere Teile der Mitarbeitertabelle zu ändern.  
  
### <a name="to-test-the-employee-table"></a>So testen Sie die Mitarbeitertabelle  
  
1.  Drücken Sie **F5**, um das Projekt auszuführen.  
  
2.  Klicken Sie auf **ersten Baustein auswählen** auf das erste Steuerelement für Inhalt anzuzeigen.  
  
3.  Klicken Sie auf den Dropdownpfeil neben der **benutzerdefinierter Katalog 1** Überschrift im Steuerelement, und wählen Sie **Mitarbeitertabelle**.  
  
4.  Klicken Sie auf die Zelle rechts neben der **Mitarbeiternamen** Zelle und geben Sie einen Namen.  
  
     Stellen Sie sicher, dass Sie dieser Zelle nur Text hinzufügen können. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> ermöglicht es Benutzern, nur Text und keine anderen Inhaltstypen wie Grafiken oder Tabellen hinzuzufügen.  
  
5.  Klicken Sie auf die Zelle rechts neben der **Hire Date** Zelle, und wählen Sie in der Datumsauswahl ein Datum.  
  
6.  Klicken Sie auf die Zelle rechts neben der **Titel** Zelle, und wählen Sie eine der Berufsbezeichnungen im Kombinationsfeld.  
  
     Geben Sie optional eine Berufsbezeichnung ein, die nicht in der Liste enthalten ist. Dies ist möglich, weil <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> Benutzern die Auswahl aus einer Liste von Einträgen oder die Eingabe eigener Einträge ermöglicht.  
  
7.  Klicken Sie auf das Symbol in der Zelle rechts neben der **Bild** Zelle, und navigieren Sie zu einem Bild, um es anzuzeigen.  
  
8.  Versuchen Sie, der Tabelle Zeilen oder Spalten hinzuzufügen und Zeilen und Spalten aus der Tabelle zu löschen. Vergewissern Sie sich, dass Sie die Tabelle nicht ändern können. <xref:Microsoft.Office.Tools.Word.GroupContentControl> verhindert, dass Sie Änderungen vornehmen.  
  
### <a name="to-test-the-customer-feedback-table"></a>So testen Sie die Kundenfeedback-Tabelle  
  
1.  Klicken Sie auf **zweiten Baustein auswählen** auf das zweite Steuerelement für Inhalt anzuzeigen.  
  
2.  Klicken Sie auf den Dropdownpfeil neben der **benutzerdefinierter Katalog 1** Überschrift im Steuerelement, und wählen Sie **Customer-Tabelle**.  
  
3.  Klicken Sie auf die Zelle rechts neben der **Kundenname** Zelle und geben Sie einen Namen.  
  
4.  Klicken Sie auf die Zelle rechts neben der **Satisfaction Rating** Zelle, und wählen Sie eine der verfügbaren Optionen.  
  
     Stellen Sie sicher, dass Sie ihren eigenen Eintrag nicht eingeben können. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ermöglicht Benutzern nur die Auswahl aus einer Liste von Einträgen.  
  
5.  Klicken Sie auf die Zelle rechts neben der **Kommentare** Zelle und geben Sie Kommentare.  
  
     Fügen Sie optional andere Inhalte als Text hinzu, z. B. Grafiken oder eine eingebettete Tabelle. Dies ist möglich, weil <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Benutzern das Hinzufügen anderer Inhalt als Text ermöglicht.  
  
6.  Vergewissern Sie sich, dass Sie der Tabelle Zeilen oder Spalten hinzufügen und Zeilen und Spalten aus der Tabelle löschen können. Dies ist möglich, da Sie die Tabelle nicht geschützt haben, indem Sie sie in <xref:Microsoft.Office.Tools.Word.GroupContentControl> eingefügt haben.  
  
7.  Schließen Sie die Vorlage.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Weitere Informationen zur Verwendung von Inhaltssteuerelementen finden Sie in diesem Thema:  
  
-   Binden von Inhaltssteuerelementen an XML-Elemente (werden auch als benutzerdefinierte XML-Teile bezeichnet), die in ein Dokument eingebettet sind Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [ContentControl-Elemente](../vsto/content-controls.md)   
 [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Vorgehensweise: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
