---
title: 'Exemplarische Vorgehensweise: Übereinstimmende Klammern anzeigen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bbea179eb2140706ee868a8a48215e7f490f57d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312523"
---
# <a name="walkthrough-display-matching-braces"></a>Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden geschweiften Klammern
Implementieren Sie die Sprache basierende Funktionen, z. B., Zuordnung von geschweiften Klammern durch definieren die geschweiften Klammern, die übereinstimmen sollten, und die übereinstimmenden geschweiften Klammern einer Textmarkierungstag hinzugefügt wird, wenn sich die Einfügemarke eines die geschweiften Klammern befindet. Sie können geschweifte Klammern im Kontext einer Sprache, eigene Dateinamenerweiterung und Inhaltstyp definieren, Tags definieren und Anwenden der zu, die geben oder Anwenden von Tags zu einem vorhandenen Inhaltstyp (z. B. "Text"). Die folgende exemplarische Vorgehensweise zeigt, wie Tags aus, um den Inhaltstyp "Text" Zugehörige Klammer angewendet wird.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen Sie ein Projekt Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein Editorklassifiziererprojekt. Nennen Sie die Projektmappe `BraceMatchingTest`.

2. Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-a-brace-matching-tagger"></a>Implementieren Sie eine Zuordnung von geschweiften Klammern Taggers
 Rufen Sie eine geschweifte Klammer hervorheben ab, der dem ähnelt, die in Visual Studio verwendet wird, können Sie einen Tagger des Typs implementieren <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Der folgende Code zeigt, wie Sie den Tagger für Klammerpaare auf jeder Schachtelungsebene definieren. In diesem Beispiel die Klammerpaare des [] und {} definiert sind, in den Tagger-Konstruktor, jedoch in einem vollständigen sprachimplementierung die entsprechenden Klammer Paare in der Language-Spezifikation definiert.

### <a name="to-implement-a-brace-matching-tagger"></a>Um eine Zuordnung von geschweiften Klammern Tagger zu implementieren.

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie Klammernentsprechung aus.

2. Importieren Sie die folgenden Namespaces ein.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Definieren Sie eine Klasse `BraceMatchingTagger` von erbt <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> des Typs <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Fügen Sie die Eigenschaften für die Textansicht, den Quellpuffer, der aktuellen Momentaufnahmepunkt und auch einen Satz von Klammerpaare hinzu.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. Legen Sie die Eigenschaften im Konstruktor Tagger und abonnieren Sie die Ansicht Änderungsereignisse <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In diesem Beispiel werden zur Veranschaulichung im Konstruktor auch übereinstimmende Paare definiert.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Als Teil der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Implementierung, deklarieren Sie ein TagsChanged-Ereignis.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Die Ereignishandler aktualisiert die aktuelle Einfügemarkenposition des der `CurrentChar` -Eigenschaft und lösen Sie das TagsChanged-Ereignis.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode entsprechend geschweiften Klammern, wenn das aktuelle Zeichen ist eine öffnende geschweifte Klammer oder das vorherige Zeichen ist eine schließende geschweifte Klammer, wie in Visual Studio. Wenn die Übereinstimmung gefunden wird, instanziiert diese Methode zwei Tags, eine für die öffnende geschweifte Klammer und eine für die schließende geschweifte Klammer.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Die folgenden privaten Methoden finden Sie auf jeder Schachtelungsebene Klammer. Die erste Methode sucht nach dem Schließen-Zeichen, das öffnende Zeichen entspricht:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Die folgende Hilfsmethode sucht nach dem Öffnen-Zeichen, das eine schließen-Zeichen entspricht:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementieren eines übereinstimmenden geschweiften Klammer-Tagger-Anbieters
 Zusätzlich zum Implementieren eines Taggers, müssen Sie auch implementieren und exportieren Sie einen Tagger-Anbieter. In diesem Fall wird der Inhaltstyp des Anbieters "Text". Also Klammer wird in allen Typen von Textdateien angezeigt, aber eine umfassendere Implementierung gilt nur für einen bestimmten Inhaltstyp zugehörige Klammer.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Einen Übereinstimmende Klammer-Tagger-Anbieter implementiert

1. Deklarieren Sie einen Tagger-Anbieter, die von erbt <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nennen Sie sie BraceMatchingTaggerProvider und exportieren Sie sie mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Methode, um eine BraceMatchingTagger zu instanziieren.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projektmappe BraceMatchingTest, und führen Sie es in der experimentellen Instanz.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Zum Erstellen und Testen BraceMatchingTest-Lösung

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text, der übereinstimmende geschweiften Klammern enthält.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Wenn Sie die position der Einfügemarke, bevor Sie eine öffnende geschweifte Klammer, sollten sowohl, geschweifte Klammer und der entsprechende schließende geschweifte Klammer hervorgehoben werden. Wenn Sie den Cursor direkt nach der schließenden geschweiften Klammer positionieren, sollten sowohl dieser geschweifte Klammer als auch die entsprechende öffnende geschweifte Klammer hervorgehoben werden.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Verknüpfen Sie einen Inhaltstyp mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)