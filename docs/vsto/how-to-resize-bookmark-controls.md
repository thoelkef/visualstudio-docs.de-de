---
title: 'Vorgehensweise: Größe von Bookmark-Steuerelementen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 04eefc37162eaa90743982a0039e21d1d9edfb1a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961531"
---
# <a name="how-to-resize-bookmark-controls"></a>Vorgehensweise: Größe von Bookmark-Steuerelementen
  Die Größe eines <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelements legen Sie fest, wenn Sie es einem Microsoft Office Word-Dokument hinzufügen. Sie können dessen Größe aber auch zu einem späteren Zeitpunkt ändern.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Es gibt drei Möglichkeiten, die Größe eines Lesezeichens zu ändern:

- Hinzufügen von Text zu oder Entfernen von Text aus dem <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement.

   Immer dann, wenn Sie einem Lesezeichen Text hinzufügen, wird es automatisch vergrößert, damit es den neuen Text enthält. Wenn Sie Text löschen, wird das Lesezeichen automatisch verkleinert.

- Ändern der <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> - und der <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelements.

   Dies bietet sich an, wenn Sie die Größe nur um wenige Zeichen ändern.

- Neuerstellen des <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelements.

   Dies bietet sich an, wenn sich die Größe oder die Position des Lesezeichens wesentlich geändert hat.

  In Projekten auf Dokumentebene können Sie dem Dokument in Ihrem Projekt zur Entwurfs- oder Laufzeit <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelemente hinzufügen. Sie können in VSTO-Add-in-Projekten hinzufügen <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelementen zu einem beliebigen geöffneten Dokument zur Laufzeit. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="change-the-start-and-end-properties"></a>Ändern Sie die Start- und End-Eigenschaften

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>So ändern Sie zur Entwurfszeit die Größe eines Lesezeichens in einem Projekt auf Dokumentebene

1. Wählen Sie das Lesezeichen im Fenster **Eigenschaften** aus.

2. Vergrößern oder verkleinern Sie den Wert der <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> -Eigenschaft.

3. Vergrößern oder verkleinern Sie den Wert der <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> -Eigenschaft.

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-runtime"></a>Zum Ändern der Größe eines Lesezeichens in einem Projekt auf Dokumentebene zur Laufzeit

1. Ändern der <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> und <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> Eigenschaften eine <xref:Microsoft.Office.Tools.Word.Bookmark> Sie erstellt haben, zur Laufzeit oder zur Entwurfszeit.

     Im folgenden Codebeispiel werden dem Anfang eines Lesezeichens namens `SampleBookmark`fünf Zeichen hinzugefügt. Für diesen Code wird davon ausgegangen, dass sich vor dem Lesezeichen mindestens fünf Textzeichen befinden.

     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]

     Im folgenden Codebeispiel werden am Ende desselben Lesezeichens fünf Zeichen hinzugefügt. Für diesen Code wird davon ausgegangen, dass sich hinter dem Lesezeichen mindestens fünf Textzeichen befinden.

     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]

### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-runtime"></a>Zum Ändern der Größe eines Lesezeichens in einem VSTO-Add-in-Projekt zur Laufzeit

1. Ändern der <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> und <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> Eigenschaften eine <xref:Microsoft.Office.Tools.Word.Bookmark> Sie zur Laufzeit erstellt.

     Im folgenden Codebeispiel wird ein <xref:Microsoft.Office.Tools.Word.Bookmark> -Objekt erstellt, das den Text aus dem ersten Absatz des aktiven Dokuments enthält. Anschließend werden am Anfang und am Ende des <xref:Microsoft.Office.Tools.Word.Bookmark>-Objekts fünf Zeichen entfernt.

     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]

## <a name="recreate-the-bookmark"></a>Das Lesezeichen neu erstellen
 Sie können die Größe eines Lesezeichens in einem Projekt auf Dokumentebene ändern, indem Sie ein neues Lesezeichen hinzufügen, das denselben Namen wie das vorhandene Lesezeichen, aber eine andere Größe hat.

### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>So erstellen Sie zur Entwurfszeit ein Lesezeichen in einem Projekt auf Dokumentebene

1. Markieren Sie den Text, der in das neue <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement eingefügt werden soll.

2. Klicken Sie im Menü **Einfügen** auf **Lesezeichen**.

3. Geben Sie im Dialogfeld **Lesezeichen** den Namen des Lesezeichens ein, dessen Größe Sie ändern möchten, und klicken Sie auf **Hinzufügen**.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Vorgehensweise: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)
- [Vorgehensweise: Größe von ListObject-Steuerelementen](../vsto/how-to-resize-listobject-controls.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
