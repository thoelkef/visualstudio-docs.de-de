---
title: 'Vorgehensweise: Schützen von Teilen von Dokumenten mithilfe von Inhalts Steuerelementen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 129962209d8cfa541a34bc1575a73382cd63d7c4
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254668"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Vorgehensweise: Schützen von Teilen von Dokumenten mithilfe von Inhalts Steuerelementen
  Wenn Sie einen Teil eines Dokuments schützen, verhindern Sie, dass Benutzer Inhalte in diesem Teil des Dokuments ändern oder löschen. Es gibt mehrere Möglichkeiten, Teile eines Microsoft Office Word-Dokuments mithilfe von Inhaltssteuerelementen zu schützen.

- Sie können ein Inhaltssteuerelement schützen.

- Sie können einen Teil eines Dokuments schützen, der nicht in einem Inhaltssteuerelement enthalten ist.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="EditDeleteControl"></a>Schützen eines Inhalts Steuer Elements
 Sie können verhindern, dass Benutzer ein Inhaltssteuerelement bearbeiten oder löschen, indem Sie Eigenschaften des Steuerelements in einem Projekt auf Dokumentebene zur Entwurfszeit oder zur Laufzeit festlegen.

 Sie können auch Inhaltssteuerelemente schützen, die Sie einem Dokument zur Laufzeit hinzufügen, indem Sie ein VSTO-Add-In-Projekt verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Inhalts Steuerelementen](../vsto/how-to-add-content-controls-to-word-documents.md)zu Word-Dokumenten.

### <a name="to-protect-a-content-control-at-design-time"></a>So schützen Sie ein Inhaltssteuerelement zur Entwurfszeit

1. Wählen Sie in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Designer gehosteten Dokument das Inhaltssteuerelement aus, das Sie schützen möchten.

2. Legen Sie im **Eigenschaften** Fenster eine oder beide der folgenden Eigenschaften fest:

    - Um zu verhindern, dass Benutzer das Steuerelement bearbeiten, legen Sie **lockcontent** auf **true**fest.

    - Legen Sie **LockContentControl** auf **true**fest, um zu verhindern, dass Benutzer das Steuerelement löschen.

3. Klicken Sie auf **OK**.

### <a name="to-protect-a-content-control-at-run-time"></a>So schützen Sie ein Inhaltssteuerelement zur Laufzeit

1. Legen Sie `LockContents` die-Eigenschaft des Inhalts Steuer Elements auf **true** fest, um zu verhindern, dass Benutzer das `LockContentControl` Steuerelement bearbeiten, und legen Sie die-Eigenschaft auf **true** fest, um zu verhindern, dass Benutzer das

     Das folgende Codebeispiel veranschaulicht die Verwendung der <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A>-Eigenschaft und <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A>-Eigenschaft zwei verschiedener <xref:Microsoft.Office.Tools.Word.RichTextContentControl>-Objekte in einem Projekt auf Dokumentebene. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument` -Klasse in Ihrem Projekt hinzu und rufen die `AddProtectedContentControls` -Methode aus dem `ThisDocument_Startup` -Ereignishandler auf.

     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]

     Das folgende Codebeispiel veranschaulicht die Verwendung der <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A>-Eigenschaft und <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A>-Eigenschaft zwei verschiedener <xref:Microsoft.Office.Tools.Word.RichTextContentControl>-Objekte in einem VSTO-Add-In-Projekt. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn` -Klasse in Ihrem Projekt hinzu und rufen die `AddProtectedContentControls` -Methode aus dem `ThisAddIn_Startup` -Ereignishandler auf.

     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Einen Teil eines Dokuments schützen, der nicht in einem Inhalts Steuerelement enthalten ist
 Sie können verhindern, dass Benutzer einen Bereich eines Dokuments ändern, indem Sie ihn in <xref:Microsoft.Office.Tools.Word.GroupContentControl> einfügen. Dies ist in den folgenden Szenarien nützlich:

- Sie möchten einen Bereich schützen, der keine Inhaltssteuerelemente enthält.

- Sie möchten einen Bereich schützen, der bereits Inhaltssteuerelemente enthält, während der Text oder andere Elemente, die Sie schützen möchten, nicht in den Inhaltssteuerelementen enthalten sind.

> [!NOTE]
> Wenn Sie ein <xref:Microsoft.Office.Tools.Word.GroupContentControl> erstellen, das eingebettete Inhaltssteuerelemente enthält, sind die eingebetteten Inhaltssteuerelemente nicht automatisch geschützt. Um zu verhindern, dass Benutzer ein eingebettetes Inhalts Steuerelement bearbeiten, verwenden Sie die **lockcontent** -Eigenschaft des Steuer Elements.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>So schützen Sie einen Bereich eines Dokuments zur Entwurfszeit

1. Wählen Sie in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Designer gehosteten Dokument den Bereich aus, den Sie schützen möchten.

2. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler"](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)im Menüband.

3. Klicken Sie in der Gruppe Steuer **Elemente** auf die Dropdown Schaltfläche **Gruppe** , und klicken Sie dann auf **Gruppe**.

     In der `ThisDocument`-Klasse in Ihrem Projekt wird automatisch ein <xref:Microsoft.Office.Tools.Word.GroupContentControl> generiert, das den geschützten Bereich enthält. Zur Entwurfszeit wird ein Rahmen angezeigt, der das Gruppensteuerelement darstellt, der zur Laufzeit allerdings nicht sichtbar ist.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>So schützen Sie einen Bereich eines Dokuments zur Laufzeit

1. Wählen Sie den zu schützenden Bereich programmgesteuert aus, und rufen Sie dann die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A>-Methode auf, um <xref:Microsoft.Office.Tools.Word.GroupContentControl> zu erstellen.

     Im folgenden Codebeispiel für ein Projekt auf Dokumentebene wird dem ersten Absatz des Dokuments Text hinzugefügt, der erste Absatz ausgewählt und dann <xref:Microsoft.Office.Tools.Word.GroupContentControl> instanziiert. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument` -Klasse in Ihrem Projekt hinzu und rufen die `ProtectFirstParagraph` -Methode aus dem `ThisDocument_Startup` -Ereignishandler auf.

     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]

     Im folgenden Codebeispiel für ein VSTO-Add-In-Projekt wird dem ersten Absatz des aktiven Dokuments Text hinzugefügt, der erste Absatz ausgewählt und dann <xref:Microsoft.Office.Tools.Word.GroupContentControl> instanziiert. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn` -Klasse in Ihrem Projekt hinzu und rufen die `ProtectFirstParagraph` -Methode aus dem `ThisAddIn_Startup` -Ereignishandler auf.

     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]

## <a name="see-also"></a>Siehe auch
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Inhalts Steuerelemente](../vsto/content-controls.md)
- [Vorgehensweise: Hinzufügen von Inhalts Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
