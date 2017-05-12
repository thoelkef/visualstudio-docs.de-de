---
title: "Gewusst wie: Hinzuf&#252;gen von Inhaltssteuerelementen zu Word-Dokumenten"
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
  - "Eingeschränkte Berechtigungen [Office-Entwicklung in Visual Studio]"
  - "DropDownListContentControl, Hinzufügen zu Dokumenten"
  - "BuildingBlockGalleryContentControl, Hinzufügen zu Dokumenten"
  - "Teilweiser Dokumentschutz [Office-Entwicklung in Visual Studio]"
  - "RichTextContentControl, Hinzufügen zu Dokumenten"
  - "Word [Office-Entwicklung in Visual Studio], Teilweiser Dokumentschutz"
  - "Inhaltssteuerelemente [Office-Entwicklung in Visual Studio], Schutz"
  - "PictureContentControl, Hinzufügen zu Dokumenten"
  - "GroupContentControl, Hinzufügen zu Dokumenten"
  - "Dokumentschutz [Office-Entwicklung in Visual Studio]"
  - "PlainTextContentControl, Hinzufügen zu Dokumenten"
  - "Inhaltssteuerelemente [Office-Entwicklung in Visual Studio], hinzufügen"
  - "ComboBoxContentControl, Hinzufügen zu Dokumenten"
  - "DatePickerContentControl, Hinzufügen zu Dokumenten"
  - "Word [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
ms.assetid: 68ddb24e-71c6-46f7-8e11-c9899d7814df
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Gewusst wie: Hinzuf&#252;gen von Inhaltssteuerelementen zu Word-Dokumenten
  In Word\-Projekten auf Dokumentebene können Sie dem Dokument in Ihrem Projekt zur Entwurfszeit oder Laufzeit Inhaltssteuerelemente hinzufügen. In Word\-VSTO\-Add\-In\-Projekten können Sie einem beliebigen geöffneten Dokument zur Laufzeit Inhaltssteuerelemente hinzufügen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Hinzufügen von Inhaltssteuerelementen zur Entwurfszeit](#designtime)  
  
-   [Hinzufügen von Inhaltssteuerelementen in einem Projekt auf Dokumentebene zur Laufzeit](#runtimedoclevel)  
  
-   [Hinzufügen von Inhaltssteuerelementen in einem VSTO\-Add\-In\-Projekt zur Laufzeit](#runtimeaddin)  
  
 Informationen zu Inhaltssteuerelementen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Hinzufügen von Inhaltssteuerelementen zur Entwurfszeit  
 Es gibt mehrere Möglichkeiten zum Hinzufügen von Inhaltssteuerelementen zum Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit:  
  
-   Fügen Sie ein Inhaltssteuerelement von der Registerkarte **Word\-Steuerelemente** der **Toolbox** hinzu.  
  
-   Fügen Sie Ihrem Dokument ein Inhaltssteuerelement auf die gleiche Weise wie ein systemeigenes Inhaltssteuerelement in Word hinzu.  
  
-   Ziehen Sie ein Inhaltssteuerelement aus dem Fenster **Datenquellen** in Ihr Dokument. Dies ist hilfreich, wenn Sie das Steuerelement während der Erstellung an Daten binden möchten. Weitere Informationen finden Sie unter [Gewusst wie: Auffüllen von Dokumenten mit Daten von Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md) und [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### So fügen Sie einem Dokument ein Inhaltssteuerelement mithilfe der Toolbox hinzu  
  
1.  Platzieren Sie den Cursor in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Designer gehosteten Dokument an der Stelle, an der das Inhaltssteuerelement hinzugefügt werden soll, oder wählen Sie den Text aus, den das Inhaltssteuerelement ersetzen soll.  
  
2.  Öffnen Sie die **Toolbox**, und klicken Sie auf die Registerkarte **Word\-Steuerelemente**.  
  
3.  Sie haben folgende Möglichkeiten, um das Steuerelement hinzuzufügen:  
  
    -   Doppelklicken Sie auf ein Inhaltssteuerelement in der **Toolbox**.  
  
         oder  
  
    -   Klicken Sie auf ein Inhaltssteuerelement in der **Toolbox**, und drücken Sie dann die EINGABETASTE.  
  
         oder  
  
    -   Ziehen Sie ein Inhaltssteuerelement aus der **Toolbox** in das Dokument. Das Inhaltssteuerelement wird an der aktuellen Auswahl im Dokument und nicht an der Position des Mauszeigers hinzugefügt.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.GroupContentControl> kann nicht über die **Toolbox** hinzugefügt werden. Sie können <xref:Microsoft.Office.Tools.Word.GroupContentControl> nur in Word oder zur Laufzeit hinzufügen.  
  
> [!NOTE]  
>  Visual Studio bietet in der Toolbox kein Kontrollkästchen\-Inhaltssteuerelement. Um dem Dokument ein Kontrollkästchen\-Inhaltssteuerelement hinzuzufügen, müssen Sie ein <xref:Microsoft.Office.Tools.Word.ContentControl>\-Objekt programmgesteuert erstellen. Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
#### So fügen Sie einem Dokument in Word ein Inhaltssteuerelement hinzu  
  
1.  Platzieren Sie den Cursor in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Designer gehosteten Dokument an der Stelle, an der das Inhaltssteuerelement hinzugefügt werden soll, oder wählen Sie den Text aus, den das Inhaltssteuerelement ersetzen soll.  
  
2.  Klicken Sie im Menüband auf die Registerkarte **Entwickler**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  Klicken Sie in der Gruppe **Steuerelemente** auf das Symbol für das Inhaltssteuerelement, das Sie hinzufügen möchten.  
  
##  <a name="runtimedoclevel"></a> Hinzufügen von Inhaltssteuerelementen in einem Projekt auf Dokumentebene zur Laufzeit  
 Sie können einem Dokument Inhaltssteuerelemente programmgesteuert zur Laufzeit hinzufügen, indem Sie Methoden der <xref:Microsoft.Office.Tools.Word.Document.Controls%2A>\-Eigenschaft der `ThisDocument`\-Klasse im Projekt verwenden. Jede Methode verfügt über drei Überladungen, mit denen Sie auf folgende Weisen ein Inhaltssteuerelement hinzufügen können:  
  
-   Fügen Sie ein Steuerelement an der aktuellen Auswahl hinzu.  
  
-   Fügen Sie ein Steuerelement in einem angegebenen Bereich hinzu.  
  
-   Fügen Sie ein Steuerelement hinzu, das auf einem systemeigenen Inhaltssteuerelement im Dokument basiert.  
  
 Dynamisch erstellte Inhaltssteuerelemente werden nicht dauerhaft im Dokument gespeichert, wenn das Dokument geschlossen wird. Ein systemeigenes Inhaltssteuerelement bleibt jedoch im Dokument erhalten. Wenn das Dokument das nächste Mal geöffnet wird, können Sie ein Inhaltssteuerelement neu erstellen, das auf einem systemeigenen Inhaltssteuerelement basiert. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Um einem Dokument in einem Word 2010\-Projekt ein Kontrollkästchen\-Inhaltssteuerelement hinzuzufügen, müssen Sie ein <xref:Microsoft.Office.Tools.Word.ContentControl>\-Objekt erstellen. Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
#### So fügen Sie ein Steuerelement an der aktuellen Auswahl hinzu  
  
1.  Verwenden Sie eine <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Methode, die über den Namen `Add`\<*Steuerelementklasse*\> verfügt \(wobei *Steuerelementklasse* der Klassenname des hinzuzufügenden Inhaltssteuerelements ist, z. B. <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) und einen einzelnen Parameter für den Namen des neuen Steuerelements aufweist.  
  
     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\-Methode verwendet, um am Anfang des Dokuments ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument`\-Klasse in Ihrem Projekt hinzu und rufen die `AddRichTextControlAtSelection`\-Methode aus dem `ThisDocument_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_ContentControlReference#700](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#700)]  
  
#### So fügen Sie ein Steuerelement in einem angegebenen Bereich hinzu  
  
1.  Verwenden Sie eine <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Methode, die über den Namen `Add`\<*Steuerelementklasse*\> verfügt \(wobei *Steuerelementklasse* der Name der hinzuzufügenden Inhaltssteuerelementklasse ist, z. B. <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) und einen <xref:Microsoft.Office.Interop.Word.Range>\-Parameter aufweist.  
  
     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\-Methode verwendet, um am Anfang des Dokuments ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument`\-Klasse in Ihrem Projekt hinzu und rufen die `AddRichTextControlAtRange`\-Methode aus dem `ThisDocument_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_ContentControlReference#701](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#701)]  
  
#### So fügen Sie ein Steuerelement hinzu, das auf einem systemeigenen Inhaltssteuerelement basiert  
  
1.  Verwenden Sie eine <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Methode, die über den Namen `Add`\<*Steuerelementklasse*\> verfügt \(wobei *Steuerelementklasse* der Name der hinzuzufügenden Inhaltssteuerelementklasse ist, z. B. <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) und einen Microsoft.Office.Interop.Word.ContentControl\-Parameter aufweist.  
  
     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\-Methode verwendet, um für jedes im Dokument enthaltene systemeigene Rich\-Text\-Steuerelement ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> zu erstellen. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument`\-Klasse in Ihrem Projekt hinzu und rufen die `CreateRichTextControlsFromNativeControls`\-Methode aus dem `ThisDocument_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_ContentControlReference#702](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Hinzufügen von Inhaltssteuerelementen in einem VSTO\-Add\-In\-Projekt zur Laufzeit  
 Sie können einem beliebigen geöffneten Dokument mithilfe eines VSTO\-Add\-Ins zur Laufzeit programmgesteuert Inhaltssteuerelemente hinzufügen. Zu diesem Zweck generieren Sie ein <xref:Microsoft.Office.Tools.Word.Document>\-Hostelement, das auf einem geöffneten Dokument basiert, und verwenden dann die Methoden der <xref:Microsoft.Office.Tools.Word.Document.Controls%2A>\-Eigenschaft dieses Hostelements. Jede Methode verfügt über drei Überladungen, mit denen Sie auf folgende Weisen ein Inhaltssteuerelement hinzufügen können:  
  
-   Fügen Sie ein Steuerelement an der aktuellen Auswahl hinzu.  
  
-   Fügen Sie ein Steuerelement in einem angegebenen Bereich hinzu.  
  
-   Fügen Sie ein Steuerelement hinzu, das auf einem systemeigenen Inhaltssteuerelement im Dokument basiert.  
  
 Dynamisch erstellte Inhaltssteuerelemente werden nicht dauerhaft im Dokument gespeichert, wenn das Dokument geschlossen wird. Ein systemeigenes Inhaltssteuerelement bleibt jedoch im Dokument erhalten. Wenn das Dokument das nächste Mal geöffnet wird, können Sie ein Inhaltssteuerelement neu erstellen, das auf einem systemeigenen Inhaltssteuerelement basiert. Weitere Informationen finden Sie unter [Beibehalten von dynamischen Steuerelementen in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Weitere Informationen zum Generieren von Hostelementen in VSTO\-Add\-In\-Projekten finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Um einem Dokument ein Kontrollkästchen\-Inhaltssteuerelement hinzuzufügen, müssen Sie ein <xref:Microsoft.Office.Tools.Word.ContentControl>\-Objekt erstellen. Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).  
  
#### So fügen Sie ein Steuerelement an der aktuellen Auswahl hinzu  
  
1.  Verwenden Sie eine <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Methode, die über den Namen `Add`\<*Steuerelementklasse*\> verfügt \(wobei *Steuerelementklasse* der Klassenname des hinzuzufügenden Inhaltssteuerelements ist, z. B. <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) und einen einzelnen Parameter für den Namen des neuen Steuerelements aufweist.  
  
     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\-Methode verwendet, um am Anfang des aktiven Dokuments ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn`\-Klasse in Ihrem Projekt hinzu und rufen die `AddRichTextControlAtSelection`\-Methode aus dem `ThisAddIn_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
#### So fügen Sie ein Steuerelement in einem angegebenen Bereich hinzu  
  
1.  Verwenden Sie eine <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Methode, die über den Namen `Add`\<*Steuerelementklasse*\> verfügt \(wobei *Steuerelementklasse* der Name der hinzuzufügenden Inhaltssteuerelementklasse ist, z. B. <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) und einen <xref:Microsoft.Office.Interop.Word.Range>\-Parameter aufweist.  
  
     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\-Methode verwendet, um am Anfang des aktiven Dokuments ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn`\-Klasse in Ihrem Projekt hinzu und rufen die `AddRichTextControlAtRange`\-Methode aus dem `ThisAddIn_Startup`\-Ereignishandler auf.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
#### So fügen Sie ein Steuerelement hinzu, das auf einem systemeigenen Inhaltssteuerelement basiert  
  
1.  Verwenden Sie eine <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Methode, die über den Namen `Add`\<*Steuerelementklasse*\> verfügt \(wobei *Steuerelementklasse* der Name der hinzuzufügenden Inhaltssteuerelementklasse ist, z. B. <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) und einen Microsoft.Office.Interop.Word.ContentControl\-Parameter aufweist.  
  
     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\-Methode verwendet, um für jedes in einem Dokument enthaltene systemeigene Rich\-Text\-Steuerelement ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> zu erstellen, nachdem das Dokument geöffnet wurde. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn`\-Klasse im Projekt hinzu.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
     Bei C\# müssen Sie auch den `Application_DocumentOpen`\-Ereignishandler an das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>\-Ereignis anfügen.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#6)]  
  
## Siehe auch  
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)  
  
  