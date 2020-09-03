---
title: 'Exemplarische Vorgehensweise: Erstellen eines Rand Symbols | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148859"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Exemplarische Vorgehensweise: Erstellen einer Randglyphe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Darstellung der Editor Ränder anpassen, indem Sie benutzerdefinierte Editor-Erweiterungen verwenden. In dieser exemplarischen Vorgehensweise wird ein benutzerdefiniertes Symbol auf den Indikator Rand eingefügt, wenn das Wort "ToDo" in einem Code Kommentar angezeigt wird.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit**und dann **VSIX-Projekt**aus.) Benennen Sie die Projekt Mappe `TodoGlyphTest` .  
  
2. Fügen Sie ein Editor-Klassifizierungs Projekt Element hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="defining-the-glyph"></a>Definieren des Symbols  
 Definieren Sie ein Symbol, indem Sie die- <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> Schnittstelle implementieren.  
  
#### <a name="to-define-the-glyph"></a>So definieren Sie das Symbol  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TodoGlyphFactory`.  
  
2. Fügen Sie die folgenden using-Deklarationen hinzu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Fügen Sie eine Klasse mit dem Namen hinzu `TodoGlyphFactory` , die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Fügen Sie ein privates Feld hinzu, das die Dimensionen des Symbols definiert.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. Implementieren Sie, `GenerateGlyph` indem Sie das Glyphe-Benutzeroberflächen Element definieren. `TodoTag` wird später in dieser exemplarischen Vorgehensweise definiert.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Fügen Sie eine Klasse mit dem Namen hinzu `TodoGlyphFactoryProvider` , die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exportieren Sie diese Klasse mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> der Zeichenfolge "", "", "" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> nach "vstextmarker", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" und "" <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von "dedotag".  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Methode, indem Sie die instanziieren `TodoGlyphFactory` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definieren eines ToDo-Tags und Taggers  
 Definieren Sie die Beziehung zwischen dem Benutzeroberflächen Element, das Sie in den vorherigen Schritten definiert haben, und dem Indikator Rand, indem Sie einen Tagtyp und einen Tagger erstellen und ihn mithilfe eines Tagger-Anbieters exportieren.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>So definieren Sie ein TODO-Tag und einen Tagger  
  
1. Fügen Sie dem Projekt eine neue Klassendatei hinzu, und benennen Sie Sie `TodoTagger` .  
  
2. Fügen Sie die folgenden Importe hinzu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Fügen Sie eine Klasse namens `TodoTag`hinzu.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Ändern Sie die Klasse `TodoTagger` mit dem Namen, die <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> vom Typ implementiert `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. `TodoTagger`Fügen Sie der-Klasse private Felder für ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> und für den Text hinzu, der in den Klassifizierungs spannen gesucht werden soll.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Fügen Sie einen Konstruktor hinzu, der den Klassifizierer festlegt.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode, indem Sie alle Klassifizierungs spannen ermitteln, deren Namen das Wort "comment" enthalten und dessen Text den Suchtext enthält. Wenn der Suchtext gefunden wird, wird ein neuer <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> des Typs zurückgeben `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Deklarieren Sie ein- `TagsChanged` Ereignis.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Fügen Sie eine Klasse mit dem Namen hinzu `TodoTaggerProvider` , die implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" und einem <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von "dedotag".  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Importieren Sie <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode, indem Sie die instanziieren `TodoTagger` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projekt Mappe "Projekt Mappe", und führen Sie Sie in der experimentellen Instanz aus.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>So erstellen und testen Sie die Projekt Mappe "tdoglyphtest"  
  
1. Erstellen Sie die Projektmappe.  
  
2. Führen Sie das Projekt aus, indem Sie F5 drücken. Eine zweite Instanz von Visual Studio wird instanziiert.  
  
3. Stellen Sie sicher, dass der Indikator Rand angezeigt wird. (Klicken Sie **im Menü Extras** auf **Optionen**. Vergewissern Sie sich, dass auf der Seite **Text-Editor** die Option **Indikator Rand** ausgewählt ist.)  
  
4. Öffnen Sie eine Codedatei, die Kommentare enthält. Fügen Sie einem der Kommentar Abschnitte das Wort "ToDo" hinzu.  
  
5. Ein heller blauer Kreis mit einem dunkelblauen Umriss sollte im Indikator Rand links neben dem Code Fenster angezeigt werden.
