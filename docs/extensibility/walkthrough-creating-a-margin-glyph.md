---
title: 'Exemplarische Vorgehensweise: Erstellen einer Randglyphe | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51dea272a595f56abe254eda74dea67415f157a6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020242"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Exemplarische Vorgehensweise: Erstellen einer randglyphe
Sie können die Darstellung der Editor Ränder anpassen, mithilfe von benutzerdefinierten Editor-Erweiterungen. In dieser exemplarischen Vorgehensweise legt ein benutzerdefiniertes Symbol auf der Indikatorrand, wenn das Wort "Todo" in einem Codekommentar angezeigt wird.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `TodoGlyphTest`.  
  
2.  Fügen Sie einem Projektelement-Editor-Klassifizierung hinzu. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="define-the-glyph"></a>Definieren Sie das Symbol  
 Definieren Sie ein Symbol, indem Sie Ausführung der <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> Schnittstelle.  
  
### <a name="to-define-the-glyph"></a>Das Symbol definiert.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TodoGlyphFactory`.  
  
2.  Fügen Sie den folgenden Code mithilfe von Deklarationen hinzu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Fügen Sie eine Klasse, die mit dem Namen `TodoGlyphFactory` implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Fügen Sie ein privates Feld, das die Abmessungen des Symbols definiert.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementieren `GenerateGlyph` durch die Definition der Symbol-Benutzeroberflächenelement (UI). `TodoTag` weiter unten in dieser exemplarischen Vorgehensweise wird definiert werden.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Fügen Sie eine Klasse, die mit dem Namen `TodoGlyphFactoryProvider` implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exportieren dieser Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "TodoGlyph", ein <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von nach VsTextMarker eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Code", und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Methode durch die Instanziierung der `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="define-a-todo-tag-and-tagger"></a>Definieren Sie einen Todo-Tag und einen tagger  
 Definieren Sie die Beziehung zwischen der UI-Element, das Sie in den vorherigen Schritten definiert und der Indikatorrand. Erstellen Sie eine Tag-Typ und den Tagger und exportieren Sie es mithilfe eines Taggers Datenanbieters.  
  
### <a name="to-define-a-todo-tag-and-tagger"></a>Um ein Todo-Tag und einen Tagger zu definieren.  
  
1.  Fügen Sie dem Projekt eine neue Klassendatei hinzu, und nennen Sie sie `TodoTagger`.  
  
2.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Fügen Sie eine Klasse, die mit dem Namen `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Ändern Sie die Klasse, die mit dem Namen `TodoTagger` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> des Typs `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Um die `TodoTagger` -Klasse, fügen Sie private Felder für eine <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> und für der Text finden Sie in der Klassifizierung umfasst.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Fügen Sie einen Konstruktor, der die Klassifizierung festlegt.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode, indem Sie die Suche nach allen die Klassifizierung umfasst, deren Namen das Wort enthalten "comment" und, dessen Text den Suchtext enthält. Yield zurück, wenn der Suchtext gefunden wird, ein neues <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> des Typs `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Deklarieren Sie eine `TagsChanged` Ereignis.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Fügen Sie eine Klasse, die mit dem Namen `TodoTaggerProvider` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Code" und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importieren der <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode durch die Instanziierung der `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe TodoGlyphTest, und führen Sie es in der experimentellen Instanz.  
  
### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Zum Erstellen und Testen der Lösung TodoGlyphTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Führen Sie das Projekt durch Drücken von **F5**. Eine zweite Instanz von Visual Studio wird gestartet.  
  
3.  Stellen Sie sicher, dass der Indikatorrand angezeigt wird. (Auf der **Tools** Menü klicken Sie auf **Optionen**. Auf der **Text-Editor** Seite, stellen Sie sicher, dass **Indikatorrand** ausgewählt ist.)  
  
4.  Öffnen Sie eine Codedatei, die Kommentare. Fügen Sie das Wort "Todo", auf einen der Kommentarabschnitte.  
  
5.  Im Indikatorrand auf der linken Seite des Code-Fensters wird ein heller blauer Kreis farbig dunkel und blau angezeigt.