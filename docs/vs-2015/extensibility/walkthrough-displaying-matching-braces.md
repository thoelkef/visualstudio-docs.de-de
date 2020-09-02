---
title: 'Exemplarische Vorgehensweise: Anzeigen von passenden geschweiften Klammern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caaafd0143d3b09a51518ee5f54a02b06dbf10aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165778"
---
# <a name="walkthrough-displaying-matching-braces"></a>Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden Klammern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können sprachbasierte Funktionen wie die Übereinstimmung mit Klammern implementieren, indem Sie die geschweiften Klammern definieren und dann einen textmarkertag zu den übereinstimmenden geschweiften Klammern hinzufügen, wenn sich die Einfügemarke in einer der geschweiften Klammern befindet. Sie können geschweifte Klammern im Kontext einer Sprache definieren, oder Sie können eine eigene Dateinamenerweiterung und einen Inhaltstyp definieren und die Tags nur auf diesen Typ anwenden, oder Sie können die Tags auf einen vorhandenen Inhaltstyp (z. b. "Text") anwenden. In der folgenden exemplarischen Vorgehensweise wird veranschaulicht, wie Sie mit dem Inhaltstyp "Text" übereinstimmende geschweifter Klammern anwenden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1. Erstellen Sie ein Editorklassifiziererprojekt. Nennen Sie die Projektmappe `BraceMatchingTest`.  
  
2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementieren einer mit Tagger passenden geschweifter Klammer  
 Wenn Sie einen Effekt hervorheben möchten, der der geschweifter Klammer ähnelt, der in Visual Studio verwendet wird, können Sie einen Tagger vom Typ implementieren <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Der folgende Code zeigt, wie das Tagger für geschweifter Klammern auf einer beliebigen Schachtelungs Ebene definiert wird. In diesem Beispiel werden die Klammer Paare [] angezeigt. [], und {} werden im Tagger-Konstruktor definiert, aber in einer vollständigen sprach Implementierung werden die relevanten Klammer Paare in der Sprachspezifikation definiert.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>So implementieren Sie eine mit Tagger übereinstimmende Klammer  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie Sie "bracematching".  
  
2. Importieren Sie die folgenden Namespaces.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Definieren Sie eine Klasse `BraceMatchingTagger` , die von vom Typ erbt <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Fügen Sie Eigenschaften für die Textansicht, den Quell Puffer und den aktuellen Momentaufnahme Punkt sowie einen Satz von geschweifter Klammern hinzu.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. Legen Sie im Tagger-Konstruktor die Eigenschaften fest, und abonnieren Sie die Sicht Änderungs Ereignisse <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . In diesem Beispiel werden die übereinstimmenden Paare zu Veranschaulichung auch im Konstruktor definiert.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. Deklarieren Sie als Teil der- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Implementierung ein tagscheignis-Ereignis.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. Die Ereignishandler aktualisieren die aktuelle Position der Einfügemarke der `CurrentChar` Eigenschaft und rufen das tagscheignis-Ereignis auf.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode, um geschweifte Klammern zu finden, wenn das aktuelle Zeichen eine öffnende geschweifte Klammer ist, oder wenn das vorherige Zeichen eine schließende geschweifte Klammer ist, wie in Visual Studio. Wenn die Entsprechung gefunden wird, instanziiert diese Methode zwei Tags, eine für die öffnende geschweifter Klammer und eine für die schließende Klammer.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Die folgenden privaten Methoden suchen nach der passenden geschweifter Klammer auf jeder Ebene der Schachtelung. Die erste Methode findet das schließende Zeichen, das mit dem geöffneten Zeichen übereinstimmt:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Die folgende Hilfsmethode findet das geöffnete Zeichen, das mit einem Schließ Zeichen übereinstimmt:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementieren einer geschweifter Klammer zum Tagger-Anbieter  
 Zusätzlich zum Implementieren eines Taggers müssen Sie auch einen Tagger-Anbieter implementieren und exportieren. In diesem Fall ist der Inhaltstyp des Anbieters "Text". Dies bedeutet, dass die Übereinstimmung mit Klammern in allen Textdateien angezeigt wird, aber eine umfassendere Implementierung würde die geschweifter Klammer nur auf einen bestimmten Inhaltstyp anwenden.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>So implementieren Sie eine Klammer, die dem Tagger-Anbieter entspricht  
  
1. Deklarieren Sie einen Tagger-Anbieter, der von erbt <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , nennen Sie ihn bracematchingtaggerprovider, und exportieren Sie ihn mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und einem <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Methode, um ein bracematchingtagger zu instanziieren.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die bracematchingtest-Projekt Mappe, und führen Sie Sie in der experimentellen Instanz aus.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>So erstellen und testen Sie die bracematchingtest-Projekt Mappe  
  
1. Erstellen Sie die Projektmappe.  
  
2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der passende geschweifte Klammern enthält.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. Wenn Sie die Einfügemarke vor einer öffnenden geschweifter Klammer positionieren, sollten diese geschweifter Klammer und die entsprechende schließende geschweifter Klammer hervorgehoben werden. Wenn Sie den Cursor direkt nach der schließenden geschweifter Klammer positionieren, sollten diese geschweifter Klammer und die entsprechende öffnende geschweifter Klammer hervorgehoben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
