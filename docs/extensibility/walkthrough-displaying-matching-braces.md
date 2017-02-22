---
title: "Exemplarische Vorgehensweise: Anzeigen von &#252;bereinstimmenden geschweiften Klammern | Microsoft Docs"
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
  - "Editoren [Visual Studio SDK] neue - Klammer"
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Anzeigen von &#252;bereinstimmenden geschweiften Klammern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Sprache basierende Funktionen wie Klammer definieren die geschweiften Klammern, die übereinstimmen soll, und dann Texttag Marker, die übereinstimmenden geschweiften Klammern hinzufügen, wird die Einfügemarke auf eine der Klammern implementieren. Können geschweifte Klammern im Kontext einer Sprache können eigene Erweiterung und Inhalt Dateinamentyp und definiert die Tags, nur diesen Typ oder Sie können die Tags anwenden, um einen vorhandenen Inhaltstyp \(z. B. "Text"\). Die folgende exemplarische Vorgehensweise zeigt, wie Klammer Tags im Inhaltstyp "Text" angewendet wird.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts \(Managed Extensibility Framework\)  
  
#### So erstellen Sie ein MEF\-Projekt  
  
1.  Erstellen Sie ein Editorklassifiziererprojekt. Nennen Sie die Projektmappe `BraceMatchingTest`.  
  
2.  Fügen Sie dem Projekt eine Classifier\-Editor\-Elementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## Implementieren eine Klammer Tagger  
 So erhalten eine geschweifte Klammer hervorheben wirksam, das diesem ähnelt, das in Visual Studio verwendet wird, können Sie eine Tagger des Typs implementieren <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Der folgende Code zeigt, wie die Tagger geschweifte Klammer\-Paaren auf jeder Ebene der Schachtelung definiert wird. In diesem Beispiel\-Paare für die geschweifte Klammer \[\]. \[\], und {} im Konstruktor Tagger definiert sind, aber in eine vollständige Programmiersprache Implementierung würde die entsprechende geschweifte Klammer\-Paare in der Language\-Spezifikation definiert werden.  
  
#### Implementieren Sie eine Klammer tagger  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie Klammernentsprechung.  
  
2.  Importieren Sie die folgenden Namespaces.  
  
     [!code-cs[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Definieren Sie eine Klasse `BraceMatchingTagger` die von erbt <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> vom Typ <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Eigenschaften für die Textansicht der Quellpuffer und den aktuellen Snapshot Punkt und auch geschweifte Klammer Paare hinzufügen.  
  
     [!code-cs[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  Legen Sie die Eigenschaften im Konstruktor Tagger und Abonnieren von View Change\-Ereignissen <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In diesem Beispiel werden zur Veranschaulichung im Konstruktor auch übereinstimmende Paare definiert.  
  
     [!code-cs[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Als Teil der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Implementierung TagsChanged\-Ereignis zu deklarieren.  
  
     [!code-cs[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Die Ereignishandler Aktualisieren von der aktuellen Position der Einfügemarke die `CurrentChar` Eigenschaft und lösen Sie das TagsChanged\-Ereignis.  
  
     [!code-cs[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode entsprechend geschweifte Klammern, wenn das aktuelle Zeichen ist eine öffnende geschweifte Klammer oder das vorherige Zeichen ist eine schließende geschweifte Klammer, wie in Visual Studio. Wenn die Übereinstimmung gefunden wird, instanziiert diese Methode zwei Tags, eine für die öffnende geschweifte Klammer und eine für die schließende geschweifte Klammer.  
  
     [!code-cs[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Die folgenden privaten Methoden finden Sie die entsprechende geschweifte Klammer auf jeder Ebene der Schachtelung. Die erste Methode sucht nach dem Schließen Zeichen, das dem geöffnete Zeichen entspricht:  
  
     [!code-cs[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Die folgende Hilfsmethode sucht nach dem Öffnen Zeichen, das ein Schließen Zeichen entspricht:  
  
     [!code-cs[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## Implementieren eine Klammer Tagger\-Anbieter  
 Zusätzlich zur Implementierung einer Tagger, müssen Sie auch implementieren und exportieren einen Anbieter Tagger. Der Inhaltstyp des Anbieters ist in diesem Fall "Text". Dies bedeutet, dass die Klammer in allen Typen von Textdateien angezeigt wird, sondern eine umfassendere Implementierung gilt nur für einen bestimmten Inhaltstyp übereinstimmende Klammern.  
  
#### Einen Übereinstimmende Klammer\-Tagger\-Anbieter implementiert  
  
1.  Deklarieren Sie einen Tagger\-Anbieter, die von erbt <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nennen Sie es BraceMatchingTaggerProvider, und exportieren Sie es mit einer <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Methode, um eine BraceMatchingTagger zu instanziieren.  
  
     [!code-cs[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe BraceMatchingTest, und führen Sie es in der experimentellen Instanz.  
  
#### So erstellen und Testen der Lösung BraceMatchingTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text ein, der übereinstimmende geschweiften Klammern enthält.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Wenn Sie die position der Einfügemarke, bevor Sie eine öffnende geschweifte Klammer, sollte diese Klammer und der entsprechenden schließenden geschweiften Klammer markiert sein. Wird direkt nach der schließenden geschweiften Klammer den Cursor positioniert ist, sollte diese Klammer und der geöffneten geschweiften Klammer markiert sein.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit Erweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)