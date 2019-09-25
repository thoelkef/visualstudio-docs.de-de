---
title: 'Vorgehensweise: Hinzufügen von Inhalts Steuerelementen zu Word-Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c84ae02bd2cafde7b6232c73bc75f0976e81bd0
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254366"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Vorgehensweise: Hinzufügen von Inhalts Steuerelementen zu Word-Dokumenten
  In Word-Projekten auf Dokumentebene können Sie dem Dokument in Ihrem Projekt zur Entwurfszeit oder Laufzeit Inhaltssteuerelemente hinzufügen. In Word-VSTO-Add-In-Projekten können Sie einem beliebigen geöffneten Dokument zur Laufzeit Inhaltssteuerelemente hinzufügen.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 In diesem Thema werden die folgenden Aufgaben beschrieben:

- [Hinzufügen von Inhalts Steuerelementen zur Entwurfszeit](#designtime)

- [Hinzufügen von Inhalts Steuerelementen in einem Projekt auf Dokument Ebene zur Laufzeit](#runtimedoclevel)

- [Hinzufügen von Inhalts Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)

  Weitere Informationen zu Inhalts Steuerelementen finden Sie unter [Inhalts Steuerelemente](../vsto/content-controls.md).

## <a name="designtime"></a>Hinzufügen von Inhalts Steuerelementen zur Entwurfszeit
 Es gibt mehrere Möglichkeiten zum Hinzufügen von Inhaltssteuerelementen zum Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit:

- Fügen Sie ein Inhaltssteuerelement von der Registerkarte **Word-Steuerelemente** der **Toolbox**hinzu.

- Fügen Sie Ihrem Dokument ein Inhaltssteuerelement auf die gleiche Weise wie ein systemeigenes Inhaltssteuerelement in Word hinzu.

- Ziehen Sie ein Inhaltssteuerelement aus dem Fenster **Datenquellen** in Ihr Dokument. Dies ist hilfreich, wenn Sie das Steuerelement während der Erstellung an Daten binden möchten. Weitere Informationen finden Sie unter [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md) und [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>So fügen Sie einem Dokument ein Inhaltssteuerelement mithilfe der Toolbox hinzu

1. Platzieren Sie den Cursor in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Designer gehosteten Dokument an der Stelle, an der das Inhaltssteuerelement hinzugefügt werden soll, oder wählen Sie den Text aus, den das Inhaltssteuerelement ersetzen soll.

2. Öffnen Sie die **Toolbox** , und klicken Sie auf die Registerkarte **Word-Steuerelemente** .

3. Sie haben folgende Möglichkeiten, um das Steuerelement hinzuzufügen:

    - Doppelklicken Sie auf ein Inhaltssteuerelement in der **Toolbox**.

         oder

    - Klicken Sie in der **Toolbox** auf ein Inhalts Steuerelement, und drücken Sie dann die **Eingabe** Taste.

         oder

    - Ziehen Sie ein Inhaltssteuerelement aus der **Toolbox** in das Dokument. Das Inhaltssteuerelement wird an der aktuellen Auswahl im Dokument und nicht an der Position des Mauszeigers hinzugefügt.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.GroupContentControl> kann nicht über die **Toolbox**hinzugefügt werden. Sie können <xref:Microsoft.Office.Tools.Word.GroupContentControl> nur in Word oder zur Laufzeit hinzufügen.

> [!NOTE]
> Visual Studio bietet in der Toolbox kein Kontrollkästchen-Inhaltssteuerelement. Um dem Dokument ein Kontrollkästchen-Inhaltssteuerelement hinzuzufügen, müssen Sie ein <xref:Microsoft.Office.Tools.Word.ContentControl> -Objekt programmgesteuert erstellen. Weitere Informationen finden Sie unter [Inhalts Steuerelemente](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>So fügen Sie einem Dokument in Word ein Inhaltssteuerelement hinzu

1. Platzieren Sie den Cursor in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Designer gehosteten Dokument an der Stelle, an der das Inhaltssteuerelement hinzugefügt werden soll, oder wählen Sie den Text aus, den das Inhaltssteuerelement ersetzen soll.

2. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler"](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)im Menüband.

3. Klicken Sie in der Gruppe **Steuerelemente** auf das Symbol für das Inhaltssteuerelement, das Sie hinzufügen möchten.

## <a name="runtimedoclevel"></a>Hinzufügen von Inhalts Steuerelementen in einem Projekt auf Dokument Ebene zur Laufzeit
 Sie können einem Dokument Inhaltssteuerelemente programmgesteuert zur Laufzeit hinzufügen, indem Sie Methoden der <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> -Eigenschaft der `ThisDocument` -Klasse im Projekt verwenden. Jede Methode verfügt über drei Überladungen, mit denen Sie auf folgende Weisen ein Inhaltssteuerelement hinzufügen können:

- Fügen Sie ein Steuerelement an der aktuellen Auswahl hinzu.

- Fügen Sie ein Steuerelement in einem angegebenen Bereich hinzu.

- Fügen Sie ein Steuerelement hinzu, das auf einem systemeigenen Inhaltssteuerelement im Dokument basiert.

  Dynamisch erstellte Inhaltssteuerelemente werden nicht dauerhaft im Dokument gespeichert, wenn das Dokument geschlossen wird. Ein systemeigenes Inhaltssteuerelement bleibt jedoch im Dokument erhalten. Wenn das Dokument das nächste Mal geöffnet wird, können Sie ein Inhaltssteuerelement neu erstellen, das auf einem systemeigenen Inhaltssteuerelement basiert. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

> [!NOTE]
> Um einem Dokument in einem Word 2010-Projekt ein Kontrollkästchen-Inhaltssteuerelement hinzuzufügen, müssen Sie ein <xref:Microsoft.Office.Tools.Word.ContentControl> -Objekt erstellen. Weitere Informationen finden Sie unter [Inhalts Steuerelemente](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>So fügen Sie ein Steuerelement an der aktuellen Auswahl hinzu

1. Verwenden Sie <xref:Microsoft.Office.Tools.Word.ControlCollection> eine Methode, die die `Add`Name \<- *Steuerelement Klasse*> (wobei die *Steuerelement Klasse* der Klassenname <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>des Inhalts Steuer Elements ist, das Sie hinzufügen möchten, z. b.), und das über einen einzelnen Parameter für das der Name des neuen Steuer Elements.

     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> -Methode verwendet, um am Anfang des Dokuments ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument` -Klasse in Ihrem Projekt hinzu und rufen die `AddRichTextControlAtSelection` -Methode aus dem `ThisDocument_Startup` -Ereignishandler auf.

     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>So fügen Sie ein Steuerelement in einem angegebenen Bereich hinzu

1. Verwenden Sie <xref:Microsoft.Office.Tools.Word.ControlCollection> eine Methode, die über `Add`die Name \<- *Steuerelement Klasse*verfügt > (wobei *Control-Klasse* der Name der Inhalts Steuerelement Klasse ist, die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>Sie hinzufügen <xref:Microsoft.Office.Interop.Word.Range> möchten, z. b.). Parame.

     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> -Methode verwendet, um am Anfang des Dokuments ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument` -Klasse in Ihrem Projekt hinzu und rufen die `AddRichTextControlAtRange` -Methode aus dem `ThisDocument_Startup` -Ereignishandler auf.

     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>So fügen Sie ein Steuerelement hinzu, das auf einem systemeigenen Inhaltssteuerelement basiert

1. Verwenden Sie <xref:Microsoft.Office.Tools.Word.ControlCollection> eine Methode, die über `Add`die Name \<- *Steuerelement Klasse*verfügt > (wobei *Control-Klasse* der Name der Inhalts Steuerelement Klasse ist, die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>Sie hinzufügen `Microsoft.Office.Interop.Word.ContentControl` möchten, z. b.). Parame.

     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> -Methode verwendet, um für jedes im Dokument enthaltene systemeigene Rich-Text-Steuerelement ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> zu erstellen. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument` -Klasse in Ihrem Projekt hinzu und rufen die `CreateRichTextControlsFromNativeControls` -Methode aus dem `ThisDocument_Startup` -Ereignishandler auf.

     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]

## <a name="runtimeaddin"></a>Hinzufügen von Inhalts Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt
 Sie können einem beliebigen geöffneten Dokument mithilfe eines VSTO-Add-Ins zur Laufzeit programmgesteuert Inhaltssteuerelemente hinzufügen. Zu diesem Zweck generieren Sie ein <xref:Microsoft.Office.Tools.Word.Document> -Hostelement, das auf einem geöffneten Dokument basiert, und verwenden dann die Methoden der <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> -Eigenschaft dieses Hostelements. Jede Methode verfügt über drei Überladungen, mit denen Sie auf folgende Weisen ein Inhaltssteuerelement hinzufügen können:

- Fügen Sie ein Steuerelement an der aktuellen Auswahl hinzu.

- Fügen Sie ein Steuerelement in einem angegebenen Bereich hinzu.

- Fügen Sie ein Steuerelement hinzu, das auf einem systemeigenen Inhaltssteuerelement im Dokument basiert.

  Dynamisch erstellte Inhaltssteuerelemente werden nicht dauerhaft im Dokument gespeichert, wenn das Dokument geschlossen wird. Ein systemeigenes Inhaltssteuerelement bleibt jedoch im Dokument erhalten. Wenn das Dokument das nächste Mal geöffnet wird, können Sie ein Inhaltssteuerelement neu erstellen, das auf einem systemeigenen Inhaltssteuerelement basiert. Weitere Informationen finden Sie unter persistente [dynamische Steuerelemente in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Weitere Informationen zum Erstellen von Host Elementen in VSTO-Add-in-Projekten finden Sie [unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

> [!NOTE]
> Um einem Dokument ein Kontrollkästchen-Inhaltssteuerelement hinzuzufügen, müssen Sie ein <xref:Microsoft.Office.Tools.Word.ContentControl> -Objekt erstellen. Weitere Informationen finden Sie unter [Inhalts Steuerelemente](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>So fügen Sie ein Steuerelement an der aktuellen Auswahl hinzu

1. Verwenden Sie <xref:Microsoft.Office.Tools.Word.ControlCollection> eine Methode, die die `Add`Name \<- *Steuerelement Klasse*> (wobei die *Steuerelement Klasse* der Klassenname <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>des Inhalts Steuer Elements ist, das Sie hinzufügen möchten, z. b.), und das über einen einzelnen Parameter für das der Name des neuen Steuer Elements.

     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> -Methode verwendet, um am Anfang des aktiven Dokuments ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn` -Klasse in Ihrem Projekt hinzu und rufen die `AddRichTextControlAtSelection` -Methode aus dem `ThisAddIn_Startup` -Ereignishandler auf.

     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>So fügen Sie ein Steuerelement in einem angegebenen Bereich hinzu

1. Verwenden Sie <xref:Microsoft.Office.Tools.Word.ControlCollection> eine Methode, die über `Add`die Name \<- *Steuerelement Klasse*verfügt > (wobei *Control-Klasse* der Name der Inhalts Steuerelement Klasse ist, die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>Sie hinzufügen <xref:Microsoft.Office.Interop.Word.Range> möchten, z. b.). Parame.

     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> -Methode verwendet, um am Anfang des aktiven Dokuments ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzuzufügen. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn` -Klasse in Ihrem Projekt hinzu und rufen die `AddRichTextControlAtRange` -Methode aus dem `ThisAddIn_Startup` -Ereignishandler auf.

     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>So fügen Sie ein Steuerelement hinzu, das auf einem systemeigenen Inhaltssteuerelement basiert

1. Verwenden Sie <xref:Microsoft.Office.Tools.Word.ControlCollection> eine Methode, die über `Add`die Name \<- *Steuerelement Klasse*verfügt > (wobei *Control-Klasse* der Name der Inhalts Steuerelement Klasse ist, die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>Sie hinzufügen `Microsoft.Office.Interop.Word.ContentControl` möchten, z. b.). Parame.

     Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> -Methode verwendet, um für jedes in einem Dokument enthaltene systemeigene Rich-Text-Steuerelement ein neues <xref:Microsoft.Office.Tools.Word.RichTextContentControl> zu erstellen, nachdem das Dokument geöffnet wurde. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn` -Klasse im Projekt hinzu.

     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]

     Bei C# müssen Sie auch den `Application_DocumentOpen` -Ereignishandler an das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> -Ereignis anfügen.

     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]

## <a name="see-also"></a>Siehe auch
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
