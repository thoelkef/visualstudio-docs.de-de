---
title: 'Exemplarische Vorgehensweise: Anzeigen übereinstimmender Klammern | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697450"
---
# <a name="walkthrough-display-matching-braces"></a>Exemplarische Vorgehensweise: Passende geschweifte Klammern anzeigen
Implementieren Sie sprachbasierte Features, z. B. die Übereinstimmung der geschweiften Klammern, indem Sie die geschweiften Klammern definieren, die Sie übereinstimmen möchten, und fügen Sie den übereinstimmenden geschweiften Klammern ein Textmarker-Tag hinzu, wenn sich die Einsaucheinheit auf einer der geschweiften Klammern befindet. Sie können geschweifte Klammern im Kontext einer Sprache definieren, ihre eigene Dateinamenerweiterung und ihren eigenen Inhaltstyp definieren und die Tags auf genau diesen Typ anwenden oder die Tags auf einen vorhandenen Inhaltstyp anwenden (z. B. "Text"). In der folgenden exemplarischen Vorgehensweise wird gezeigt, wie Brace-Matching-Tags auf den Inhaltstyp "Text" angewendet werden.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)

#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein Editorklassifiziererprojekt. Nennen Sie die Projektmappe `BraceMatchingTest`.

2. Fügen Sie dem Projekt eine Editor-Klassifierelementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-a-brace-matching-tagger"></a>Implementieren eines übereinstimmenden Taggers für geschweifte Klammern
 Um einen Brace-Hervorhebungseffekt zu erhalten, der dem in Visual Studio verwendeten <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>ähnelt, können Sie einen Tagger vom Typ implementieren. Der folgende Code zeigt, wie sie den Tagger für geschweifte Paare auf jeder Schachtelungsebene definieren. In diesem Beispiel werden die geschweiften Paare von [] und {} im Tagger-Konstruktor definiert, aber in einer vollständigen Sprachimplementierung würden die relevanten geschweiften Paare in der Sprachspezifikation definiert.

### <a name="to-implement-a-brace-matching-tagger"></a>So implementieren Sie einen korsetten übereinstimmenden Tagger

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie BraceMatching.

2. Importieren Sie die folgenden Namespaces.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Definieren Sie `BraceMatchingTagger` eine Klasse, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> die <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>vom Typ erbt.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Fügen Sie Eigenschaften für die Textansicht, den Quellpuffer, den aktuellen Snapshotpunkt und auch eine Reihe von geschweiften Paaren hinzu.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. Legen Sie im Tagger-Konstruktor die Eigenschaften fest, und abonnieren Sie die Ansichtsänderungsereignisse <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In diesem Beispiel werden zur Veranschaulichung auch die übereinstimmenden Paare im Konstruktor definiert.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Deklarieren <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Sie als Teil der Implementierung ein TagsChanged-Ereignis.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Die Ereignishandler aktualisieren die aktuelle Einsierungsposition der `CurrentChar` Eigenschaft und erhöhen das TagsChanged-Ereignis.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Sie die Methode, um geschweifte Klammern entweder abzugleichen, wenn das aktuelle Zeichen eine offene geschweifte Klammer ist, oder wenn das vorherige Zeichen eine geschlossene geschweifte Klammer ist, wie in Visual Studio. Wenn die Übereinstimmung gefunden wird, instanziiert diese Methode zwei Tags, eines für die offene geschweifte Klammer und eines für die enge geschweifte Klammer.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Die folgenden privaten Methoden finden die übereinstimmende geschweifte Klammer auf jeder Schachtelungsebene. Die erste Methode findet das nahe Zeichen, das mit dem geöffneten Zeichen übereinstimmt:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Die folgende Hilfsmethode findet das offene Zeichen, das mit einem schließenden Zeichen übereinstimmt:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementieren eines brace matching tagger-Anbieters
 Neben der Implementierung eines Taggers müssen Sie auch einen Tagger-Anbieter implementieren und exportieren. In diesem Fall ist der Inhaltstyp des Anbieters "Text". Daher wird der Abgleich von Geschweifklammern in allen Arten von Textdateien angezeigt, aber eine vollständigere Implementierung wendet den Korsettab nur auf einen bestimmten Inhaltstyp an.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>So implementieren Sie einen brace matching tagger-Anbieter

1. Deklarieren Sie einen Tagger-Anbieter, der <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>von erbt, nennen <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Sie ihn BraceMatchingTaggerProvider, und exportieren Sie ihn mit einem von "text" und einem <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> . <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implementieren <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Sie die Methode zum Instanziieren eines BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die BraceMatchingTest-Lösung, und führen Sie sie in der experimentellen Instanz aus.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>So erstellen und testen Sie die BraceMatchingTest-Lösung

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der übereinstimmende geschweifte Klammern enthält.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Wenn Sie die Einsergruppe vor einer geöffneten geschweiften Klammer positionieren, sollten sowohl diese geschweifte Klammer als auch die entsprechende geschlossene Klammer hervorgehoben werden. Wenn Sie den Cursor direkt nach dem schließenden geschweiften Klammern positionieren, sollten sowohl diese geschweifte Klammer als auch die entsprechende offene geschweifte Klammer hervorgehoben werden.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
