---
title: 'Exemplarische Vorgehensweise: Anzeigen von zueinander passende Klammern | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3dde61c10d0a8c9fc5578b02cc713f648409cbf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-matching-braces"></a>Exemplarische Vorgehensweise: Anzeigen von Klammern
Sie können die Sprache basierende Funktionen wie z. B. die Zuordnung von geschweiften Klammern durch definieren die geschweiften Klammern, die übereinstimmen soll, und klicken Sie dann hinzugefügt Marker Texttag die übereinstimmenden geschweiften Klammern wird das Caretzeichen auf einem der Klammern implementieren. Sie können geschweifte Klammern im Kontext einer Sprache definieren können Sie definieren Sie eine eigene Erweiterung und Inhalt Dateityp von Name und die Tags auf nur diesen Typ gelten oder Sie können die Tags anwenden, um einen vorhandenen Inhaltstyp (z. B. "Text"). Die folgende exemplarische Vorgehensweise veranschaulicht die Zuordnung von geschweiften Klammern Tags aus, um den Inhaltstyp "Text" angewendet.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein Editorklassifiziererprojekt. Nennen Sie die Projektmappe `BraceMatchingTest`.  
  
2.  Dem Projekt eine Elementvorlage Editor Klassifizierer hinzugefügt. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementieren eine Zuordnung von geschweiften Klammern Taggers  
 Um erhalten eine geschweifte Klammer hervorheben wirksam, das diesem ähnelt, die in Visual Studio verwendet wird, können Sie einen Tagger des Typs implementieren <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Der folgende Code zeigt, wie die Tagger für geschweifte Klammer Paare auf jeder Ebene der Schachtelung definiert wird. In diesem Beispiel Paaren die geschweiften Klammern []. [], und "{}" in der Tagger Konstruktor definiert sind, jedoch in einer Implementierung eines vollständigen Sprachzugriff würde die entsprechende geschweifte Klammer-Paare in der Language-Spezifikation definiert werden.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Um eine Zuordnung von geschweiften Klammern Tagger zu implementieren.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie BraceMatching.  
  
2.  Importieren Sie die folgenden Namespaces hinzu.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Definieren Sie eine Klasse `BraceMatchingTagger` von erbt <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> vom Typ <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Fügen Sie die Eigenschaften der Textansicht, der Quellpuffer und den aktuellen Zeitpunkt der Momentaufnahme und auch eine Reihe von Paaren von geschweiften Klammern hinzu.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  Im Konstruktor Tagger legen Sie die Eigenschaften und abonnieren Sie die Ansicht Änderungsereignisse <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In diesem Beispiel werden zur Veranschaulichung in den Konstruktor auch übereinstimmende Paare definiert.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Als Teil der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Implementierung, deklarieren Sie ein TagsChanged-Ereignis.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Die Ereignishandler Aktualisieren von der aktuellen Position der Einfügemarke die `CurrentChar` Eigenschaft und lösen Sie das TagsChanged-Ereignis.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode entsprechend geschweifte Klammern, wenn das aktuelle Zeichen ist eine öffnende geschweifte Klammer oder wenn das vorherige Zeichen eine schließende geschweifte Klammer, wie in Visual Studio ist. Bei der Übereinstimmung gefunden wird, wird diese Methode zwei Tags, eine für die öffnende geschweifte Klammer und eine für die schließende geschweifte Klammer instanziiert.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Die folgenden privaten Methoden finden auf jeder Ebene der Schachtelung geschweiften Klammer. Die erste Methode sucht nach dem Schließen Zeichen, das dem geöffnete Zeichen entspricht:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Die folgende Hilfsmethode sucht nach dem Öffnen Zeichen, das ein Schließen Zeichen entspricht:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementieren eine Zuordnung von geschweiften Klammern Tagger-Anbieter  
 Zusätzlich zum Implementieren eines Taggers, müssen Sie auch implementieren und exportieren einen Tagger-Anbieter. Der Inhaltstyp des Anbieters ist in diesem Fall "Text". Dies bedeutet, dass die Klammer in allen Typen von Textdateien erscheint, aber eine umfassendere Implementierung würde die Zuordnung von geschweiften Klammern, die nur für einen bestimmten Inhaltstyp gelten.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Einen Übereinstimmende Klammer-Tagger-Anbieter implementiert  
  
1.  Deklarieren Sie einen Tagger-Anbieter, die von erben <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nennen Sie sie BraceMatchingTaggerProvider und exportieren Sie sie mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und eine <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Methode, um eine BraceMatchingTagger zu instanziieren.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die BraceMatchingTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>So erstellen und Testen der Lösung BraceMatchingTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie etwas Text ein, die übereinstimmende geschweiften Klammern enthält.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Wenn Sie die position der Einfügemarke, bevor Sie eine öffnende geschweifte Klammer, sollte diese geschweiften Klammer und der übereinstimmende schließende geschweifte Klammer markiert sein. Wenn Sie den Cursor hinter die schließende geschweifte Klammer positionieren, sollte diese geschweiften Klammer und das entsprechende öffnende geschweifte Klammer markiert sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)