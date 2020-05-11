---
title: 'Exemplarische Vorgehensweise: Erstellen einer Margin-Glyphe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697703"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Exemplarische Vorgehensweise: Erstellen einer Rand-Glyphe
Sie können die Darstellung von Editorrändern mithilfe benutzerdefinierter Editorerweiterungen anpassen. In dieser exemplarischen Vorgehensweise wird eine benutzerdefinierte Glyphe auf den Indikatorrand gesetzt, wenn das Wort "todo" in einem Codekommentar angezeigt wird.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `TodoGlyphTest`die Lösung .

2. Fügen Sie ein Editor-Klassifier-Projektelement hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="define-the-glyph"></a>Definieren der Glyphe
 Definieren Sie eine <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> Glyphe, indem Sie die Schnittstelle ausführen.

### <a name="to-define-the-glyph"></a>So definieren Sie die Glyphe

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TodoGlyphFactory`.

2. Fügen Sie den folgenden Code mithilfe von Deklarationen hinzu.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Fügen Sie `TodoGlyphFactory` eine Klasse <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>mit dem Namen hinzu, die implementiert.

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Fügen Sie ein privates Feld hinzu, das die Dimensionen der Glyphe definiert.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementieren `GenerateGlyph` Sie, indem Sie das Glyphenbenutzeroberflächenelement (UI) definieren. `TodoTag`wird später in dieser exemplarischen Vorgehensweise definiert.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Fügen Sie `TodoGlyphFactoryProvider` eine Klasse <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>mit dem Namen hinzu, die implementiert. Exportieren Sie diese <xref:Microsoft.VisualStudio.Utilities.NameAttribute> Klasse mit einem <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> einem von After <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> VsTextMarker, einem von "code", und einem von TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implementieren <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Sie die Methode, `TodoGlyphFactory`indem Sie die instanziieren.

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definieren eines Todo-Tags und -Taggers
 Definieren Sie die Beziehung zwischen dem UI-Element, das Sie in den vorherigen Schritten definiert haben, und dem Indikatorrand. Erstellen Sie einen Tag-Typ und einen Tagger, und exportieren Sie ihn mithilfe eines Tagger-Anbieters.

### <a name="to-define-a-todo-tag-and-tagger"></a>So definieren Sie ein Todo-Tag und einen Tagger

1. Fügen Sie dem Projekt eine neue `TodoTagger`Klassendatei hinzu, und benennen Sie sie .

2. Fügen Sie die folgenden Importe hinzu.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Fügen Sie eine Klasse namens `TodoTag`hinzu.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Ändern Sie `TodoTagger` die Klasse <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> mit `TodoTag`dem Namen, die vom Typ implementiert.

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Fügen `TodoTagger` Sie der Klasse private <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Felder für einen und für den Text hinzu, der in den Klassifizierungssspannen gesucht werden soll.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Fügen Sie einen Konstruktor hinzu, der den Klassifier festlegt.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Sie die Methode, indem Sie alle Klassifizierungsspannen finden, deren Namen das Wort "Kommentar" und dessen Text den Suchtext enthält. Wenn der Suchtext gefunden wird, <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> geben `TodoTag`Sie einen neuen Typ zurück.

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Deklarieren Sie ein `TagsChanged` Ereignis.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Fügen Sie `TodoTaggerProvider` eine Klasse <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>mit dem Namen <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> hinzu, die <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> implementiert, und exportieren Sie sie mit einem von "code" und einem von TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importieren <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>Sie die .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Sie die Methode, `TodoTagger`indem Sie die instanziieren.

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die TodoGlyphTest-Lösung, und führen Sie sie in der experimentellen Instanz aus.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>So erstellen und testen Sie die TodoGlyphTest-Lösung

1. Erstellen Sie die Projektmappe.

2. Führen Sie das Projekt aus, indem Sie **F5**drücken. Eine zweite Instanz von Visual Studio wird gestartet.

3. Stellen Sie sicher, dass die Indikatormarge angezeigt wird. (Klicken Sie im Menü **Extras** auf **Optionen**. Stellen Sie auf der Seite **Texteditor** sicher, dass der **Indikatorrand** ausgewählt ist.)

4. Öffnen Sie eine Codedatei mit Kommentaren. Fügen Sie einem der Kommentarabschnitte das Wort "todo" hinzu.

5. Ein hellblauer Kreis mit einem dunkelblauen Umriss erscheint am Indikatorrand links vom Codefenster.
