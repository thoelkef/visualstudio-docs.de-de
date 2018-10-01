---
title: 'Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden geschweiften Klammern | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11021dc98acfd80f1e91443cc834eb4ae0126455
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509674"
---
# <a name="walkthrough-displaying-matching-braces"></a>Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden Klammern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden geschweiften Klammern](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-displaying-matching-braces).  
  
Sie können die Sprache basierenden Funktionen wie z. B. die Zuordnung von geschweiften Klammern durch definieren die geschweiften Klammern, die übereinstimmen sollten, und klicken Sie dann eine Textmarkierungstag auf die übereinstimmenden geschweiften Klammern hinzufügen, wenn sich die Einfügemarke, auf einem der Klammern befindet implementieren. Sie können geschweifte Klammern im Kontext einer Sprache, definieren Sie können eine eigene Erweiterung und Inhalt Dateinamentyp Tags definieren und Anwenden der, die nur diesen Typ oder Sie können die Tags anwenden, um einem vorhandenen Inhaltstyp (z. B. "Text"). Die folgende exemplarische Vorgehensweise zeigt, wie Tags aus, um den Inhaltstyp "Text" Zugehörige Klammer angewendet wird.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein Editorklassifiziererprojekt. Nennen Sie die Projektmappe `BraceMatchingTest`.  
  
2.  Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementieren eine Zuordnung von geschweiften Klammern Taggers  
 Rufen Sie eine geschweifte Klammer hervorheben ab, der dem ähnelt, die in Visual Studio verwendet wird, können Sie einen Tagger des Typs implementieren <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Der folgende Code zeigt, wie Sie den Tagger für Klammerpaare auf jeder Schachtelungsebene definieren. In diesem Beispiel-Paaren der geschweiften Klammern []. [], und {} definiert sind, in den Tagger-Konstruktor, jedoch in einem vollständigen sprachimplementierung die relevanten Klammerpaare würde in der Language-Spezifikation definiert werden.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Um eine Zuordnung von geschweiften Klammern Tagger zu implementieren.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie Klammernentsprechung aus.  
  
2.  Importieren Sie die folgenden Namespaces ein.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3.  Definieren Sie eine Klasse `BraceMatchingTagger` von erbt <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> des Typs <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4.  Fügen Sie Eigenschaften für die Textansicht, Quellpuffer, und der aktuellen Momentaufnahmepunkt und auch einen Satz von Klammerpaare.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5.  Legen Sie die Eigenschaften im Konstruktor Tagger und abonnieren Sie die Ansicht Änderungsereignisse <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In diesem Beispiel werden zur Veranschaulichung im Konstruktor auch übereinstimmende Paare definiert.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6.  Als Teil der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Implementierung, deklarieren Sie ein TagsChanged-Ereignis.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7.  Die Ereignishandler aktualisiert die aktuelle Einfügemarkenposition des der `CurrentChar` -Eigenschaft und lösen Sie das TagsChanged-Ereignis.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode entsprechend geschweiften Klammern, wenn das aktuelle Zeichen ist eine öffnende geschweifte Klammer oder das vorherige Zeichen ist eine schließende geschweifte Klammer, wie in Visual Studio. Wenn die Übereinstimmung gefunden wird, instanziiert diese Methode zwei Tags, eine für die öffnende geschweifte Klammer und eine für die schließende geschweifte Klammer.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Die folgenden privaten Methoden finden Sie auf jeder Schachtelungsebene Klammer. Die erste Methode sucht nach dem Schließen-Zeichen, das öffnende Zeichen entspricht:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Die folgende Hilfsmethode sucht nach dem Öffnen-Zeichen, das eine schließen-Zeichen entspricht:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementieren eine Zuordnung von geschweiften Klammern Tagger-Anbieter  
 Zusätzlich zum Implementieren eines Taggers, müssen Sie auch implementieren und exportieren Sie einen Tagger-Anbieter. In diesem Fall wird der Inhaltstyp des Anbieters "Text". Dies bedeutet, dass die Klammer in allen Typen von Textdateien angezeigt, jedoch eine umfassendere Implementierung würde Klammer, die nur für einen bestimmten Inhaltstyp angewendet werden.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Einen Übereinstimmende Klammer-Tagger-Anbieter implementiert  
  
1.  Deklarieren Sie einen Tagger-Anbieter, die von erbt <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nennen Sie sie BraceMatchingTaggerProvider und exportieren Sie sie mit einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und ein <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Methode, um eine BraceMatchingTagger zu instanziieren.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe BraceMatchingTest, und führen Sie es in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Zum Erstellen und Testen BraceMatchingTest-Lösung  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen Sie eine Textdatei, und geben Sie Text, der übereinstimmende geschweiften Klammern enthält.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Wenn Sie die position der Einfügemarke, bevor Sie eine öffnende geschweifte Klammer, sollten sowohl, geschweifte Klammer und der entsprechende schließende geschweifte Klammer hervorgehoben werden. Wenn Sie den Cursor direkt nach der schließenden geschweiften Klammer positionieren, sollten sowohl dieser geschweifte Klammer als auch die entsprechende öffnende geschweifte Klammer hervorgehoben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

