---
title: "Exemplarische Vorgehensweise: Erstellen einer Randglyphe | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] margin neu - Symbol"
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen einer Randglyphe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Darstellung des Editors Ränder anpassen, mit benutzerdefinierten Editor\-Erweiterungen. In dieser exemplarischen Vorgehensweise wird ein benutzerdefiniertes Symbol Indikatorrand immer das Wort "Todo" innerhalb eines Codekommentars angezeigt wird.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt. \(In der **Neues Projekt** Dialogfeld **Visual c\# \/ Erweiterbarkeit**, dann **VSIX\-Projekt**.\) Nennen Sie die Projektmappe `TodoGlyphTest`.  
  
2.  Fügen Sie eine Classifier\-Editor\-Projektelement hinzu. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## Definieren das Symbol  
 Definieren ein Symbols durch das Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> Schnittstelle.  
  
#### Um das Symbol zu definieren.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie es `TodoGlyphFactory`.  
  
2.  Fügen Sie die folgenden Deklarationen verwenden.  
  
     [!code-cs[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Fügen Sie eine Klasse mit dem Namen `TodoGlyphFactory` implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-cs[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Fügen Sie ein privates Feld, das die Dimensionen des Symbols definiert.  
  
     [!code-cs[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementieren `GenerateGlyph` durch das Symbol Benutzeroberflächenelement \(UI\) definieren.`TodoTag` wird später in dieser exemplarischen Vorgehensweise definiert.  
  
     [!code-cs[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Fügen Sie eine Klasse mit dem Namen `TodoGlyphFactoryProvider` implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exportieren dieser Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "TodoGlyph", eine <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von nach VsTextMarker eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Code", und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von TodoTag.  
  
     [!code-cs[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Methode durch die Instanziierung der `TodoGlyphFactory`.  
  
     [!code-cs[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## Definieren eines TODO\-Tag und Tagger  
 Definieren Sie die Beziehung zwischen dem Element der Benutzeroberfläche, das Sie in den vorherigen Schritten definiert und Indikatorrand, indem Sie einen Tag\-Typ und Tagger erstellen und exportieren es mithilfe eines Anbieters Tagger.  
  
#### Um eine TODO\-Tag und Tagger definieren  
  
1.  Das Projekt eine neue Klassendatei hinzu, und nennen Sie es `TodoTagger`.  
  
2.  Fügen Sie die folgenden Importe hinzu.  
  
     [!code-cs[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Fügen Sie eine Klasse mit dem Namen `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Ändern Sie die Klasse mit dem Namen `TodoTagger` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> vom Typ `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Um die `TodoTagger` \-Klasse, fügen Sie private Felder für eine <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> und für der Text in der Klassifizierung finden umfasst.  
  
     [!code-cs[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Fügen Sie einen Konstruktor, der die Klassifizierung festlegt.  
  
     [!code-cs[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode mit einer Suche nach allen Klassifizierung umfasst, deren Namen den Begriff "comment" und dessen Text den gesuchten Text enthält. Wenn der zu durchsuchende Text gefunden wird, ergibt wieder eine neue <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> vom Typ `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Deklarieren Sie eine `TagsChanged` Ereignis.  
  
     [!code-cs[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Fügen Sie eine Klasse mit dem Namen `TodoTaggerProvider` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Code" und eine <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> der TodoTag.  
  
     [!code-cs[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importieren der <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-cs[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode durch die Instanziierung der `TodoTagger`.  
  
     [!code-cs[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe TodoGlyphTest, und führen Sie es in der experimentellen Instanz.  
  
#### So erstellen und Testen der Lösung TodoGlyphTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Führen Sie das Projekt, indem Sie F5 drücken. Eine zweite Instanz von Visual Studio wird instanziiert.  
  
3.  Stellen Sie sicher, dass im Indikatorrand angezeigt wird. \(Auf der **Tools** Menü klicken Sie auf **Optionen**. Auf der **Texteditor** Seite, stellen Sie sicher, dass **Indikatorrand** ausgewählt ist.\)  
  
4.  Öffnen Sie eine Codedatei, die Kommentare enthält. Fügen Sie das Wort "Todo" in den Abschnitten Kommentar.  
  
5.  Ein Licht blauer Kreis, der einem dunklen blauen Rahmen hat sollte im Indikatorrand auf der linken Seite des Codefensters angezeigt werden.