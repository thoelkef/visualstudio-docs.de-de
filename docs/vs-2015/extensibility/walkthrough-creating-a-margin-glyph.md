---
title: 'Exemplarische Vorgehensweise: Erstellen einer Randglyphe | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112467"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Exemplarische Vorgehensweise: Erstellen einer Randglyphe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Darstellung der Editor Ränder anpassen, mithilfe von benutzerdefinierten Editor-Erweiterungen. In dieser exemplarischen Vorgehensweise legt ein benutzerdefiniertes Symbol auf der Indikatorrand, wenn das Wort "Todo" in einem Codekommentar angezeigt wird.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
1. Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `TodoGlyphTest`.  
  
2. Fügen Sie einem Projektelement-Editor-Klassifizierung hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="defining-the-glyph"></a>Definieren das Symbol  
 Definieren Sie ein Symbol, durch das Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> Schnittstelle.  
  
#### <a name="to-define-the-glyph"></a>Das Symbol definiert.  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TodoGlyphFactory`.  
  
2. Fügen Sie die folgenden using-Deklarationen.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Fügen Sie eine Klasse, die mit dem Namen `TodoGlyphFactory` implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Fügen Sie ein privates Feld, das die Abmessungen des Symbols definiert.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. Implementieren `GenerateGlyph` durch die Definition der Symbol-Benutzeroberflächenelement (UI). `TodoTag` weiter unten in dieser exemplarischen Vorgehensweise wird definiert werden.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Fügen Sie eine Klasse, die mit dem Namen `TodoGlyphFactoryProvider` implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exportieren dieser Klasse mit einer <xref:Microsoft.VisualStudio.Utilities.NameAttribute> von "TodoGlyph", ein <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von nach VsTextMarker eine <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Code", und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Methode durch die Instanziierung der `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definieren einen Todo-Tag und einen Tagger  
 Definieren Sie die Beziehung zwischen der UI-Element, das Sie in den vorherigen Schritten definiert und der Indikatorrand, indem Sie erstellen einen Tagtyp und den Tagger und exportieren es mithilfe eines Taggers Datenanbieters.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Um ein Todo-Tag und einen Tagger zu definieren.  
  
1. Fügen Sie dem Projekt eine neue Klassendatei hinzu, und nennen Sie sie `TodoTagger`.  
  
2. Fügen Sie die folgenden Importe hinzu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Fügen Sie eine Klasse, die mit dem Namen `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Ändern Sie die Klasse, die mit dem Namen `TodoTagger` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> des Typs `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. Um die `TodoTagger` -Klasse, fügen Sie private Felder für eine <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> und für der Text finden Sie in der Klassifizierung umfasst.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Fügen Sie einen Konstruktor, der die Klassifizierung festlegt.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode, indem Sie die Suche nach allen die Klassifizierung umfasst, deren Namen das Wort enthalten "comment" und, dessen Text den Suchtext enthält. Yield zurück, wenn der Suchtext gefunden wird, ein neues <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> des Typs `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Deklarieren Sie eine `TagsChanged` Ereignis.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Fügen Sie eine Klasse, die mit dem Namen `TodoTaggerProvider` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Code" und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Importieren der <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode durch die Instanziierung der `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe TodoGlyphTest, und führen Sie es in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Zum Erstellen und Testen der Lösung TodoGlyphTest  
  
1. Erstellen Sie die Projektmappe.  
  
2. Führen Sie das Projekt durch Drücken von F5. Es wird eine zweite Instanz von Visual Studio instanziiert.  
  
3. Stellen Sie sicher, dass der Indikatorrand angezeigt wird. (Auf der **Tools** Menü klicken Sie auf **Optionen**. Auf der **Text-Editor** Seite, stellen Sie sicher, dass **Indikatorrand** ausgewählt ist.)  
  
4. Öffnen Sie eine Codedatei, die Kommentare. Fügen Sie das Wort "Todo", auf einen der Kommentarabschnitte.  
  
5. Ein heller blauer Kreis, die einen dunklen blauen über sollte im Indikatorrand auf der linken Seite des Codefensters angezeigt werden.
