---
title: 'Exemplarische Vorgehensweise: Erstellen eines Symbols Rand | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fc813ed3c29c2fe0a4cac1c348ffed18ae8fd2d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Exemplarische Vorgehensweise: Erstellen eines Symbols Rand
Sie können die Darstellung der Editor Ränder anpassen, mithilfe von benutzerdefinierten Editor-Erweiterungen. In dieser exemplarischen Vorgehensweise wird ein benutzerdefiniertes Symbol Indikatorrand versehen, wenn das Wort "Todo" in einem Codekommentar angezeigt wird.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekts**.) Nennen Sie die Projektmappe `TodoGlyphTest`.  
  
2.  Fügen Sie ein Projektelement-Editor-Klassifizierung hinzu. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="defining-the-glyph"></a>Definieren das Symbol  
 Definieren ein Symbols durch das Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> Schnittstelle.  
  
#### <a name="to-define-the-glyph"></a>Das Symbol definieren  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TodoGlyphFactory`.  
  
2.  Fügen Sie die folgenden Deklarationen verwenden.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Fügen Sie eine Klasse mit dem Namen `TodoGlyphFactory` implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Fügen Sie ein privates Feld, das die Dimensionen des Symbols definiert.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementieren `GenerateGlyph` durch Definieren der Symbol-Benutzeroberflächenelement (UI). `TodoTag`wird weiter unten in dieser exemplarischen Vorgehensweise definiert.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Fügen Sie eine Klasse mit dem Namen `TodoGlyphFactoryProvider` implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exportieren dieser Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "TodoGlyph", ein <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von nach VsTextMarker eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code", und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Methode durch die Instanziierung der `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definieren eines TODO-Tag und Taggers  
 Definieren Sie die Beziehung zwischen dem Benutzeroberflächenelement, das Sie in den vorherigen Schritten definiert und der Indikatorrand, indem Sie eine Tagtyp sowie Tagger erstellen und exportieren es mithilfe eines Taggers-Anbieters.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Zum Definieren einer TODO-Tag und Taggers  
  
1.  Fügen Sie dem Projekt eine neue Klassendatei hinzu, und nennen Sie sie `TodoTagger`.  
  
2.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Fügen Sie eine Klasse mit dem Namen `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Ändern Sie die Klasse mit dem Namen `TodoTagger` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> vom Typ `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Um die `TodoTagger` -Klasse, fügen Sie private Felder für eine <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> und für der Text in der Klassifizierung gefunden umfasst.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Fügen Sie einen Konstruktor, der die Klassifizierung festlegt.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode mit einer Suche nach allen Klassifizierung umfasst, deren Name das Wort einschließen "Kommentar" und enthält, dessen Text den Suchtext ein. Bei jedem das Suchen von Text gefunden wird, ergeben wieder ein neues <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> vom Typ `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Deklarieren Sie eine `TagsChanged` Ereignis.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Fügen Sie eine Klasse mit dem Namen `TodoTaggerProvider` , implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, und exportieren Sie sie mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" und eine <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importieren der <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode durch die Instanziierung der `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die TodoGlyphTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>So erstellen und Testen der Lösung TodoGlyphTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Drücken Sie F5, um führen Sie das Projekt aus. Eine zweite Instanz von Visual Studio instanziiert wird.  
  
3.  Stellen Sie sicher, dass der Indikatorrand angezeigt wird. (Auf der **Tools** Menü klicken Sie auf **Optionen**. Auf der **Texteditor** Seite, stellen Sie sicher, dass **Indikatorrand** ausgewählt ist.)  
  
4.  Öffnen Sie eine Codedatei, die Kommentare verfügt. Fügen Sie das Wort "Todo" in den Abschnitten Kommentar hinzu.  
  
5.  Ein heller blauer Kreis, der einem dunklen blauen Rahmen hat, sollte im Indikatorrand auf der linken Seite des Codefensters angezeigt werden.