---
title: 'Exemplarische Vorgehensweise: Gliedern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054703"
---
# <a name="walkthrough-outlining"></a>Exemplarische Vorgehensweise: Gliedern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Sprache basierenden Funktionen wie z. B. durch Definieren der Arten von Textbereiche, die Sie erweitern oder reduzieren möchten Gliederung implementieren. Können Sie Regionen in den Kontext für den Sprachdienst definieren können definieren Sie eigene Datei Name-Erweiterung und der Inhalt Typ und die Definition für die Region, nur diesen Typ gelten oder Sie können die Definitionen für die Region auf einem vorhandenen Inhaltstyp (z. B. "Text") anwenden. Diese exemplarische Vorgehensweise veranschaulicht das Definieren und Anzeigen von Gliederungsbereiche.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1. Erstellen Sie ein VSIX-Projekt. Nennen Sie die Projektmappe `OutlineRegionTest`.  
  
2. Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementieren eine Gliederung Taggers  
 Gliederungsbereiche werden markiert, eine Art von Tags (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Dieses Tag stellt die Gliederung Verhalten. Die gegliederte Bereich kann erweitert oder reduziert werden. Die gegliederte Bereich wird durch ein Pluszeichen, falls er reduziert ist oder ein Minuszeichen (-) markiert, wenn er erweitert, und die erweiterte Region durch eine vertikale Linie abgegrenzt wird.  
  
 Die folgenden Schritte zeigen, wie Sie einen Tagger definieren, die Gliederungsbereiche für alle Regionen erstellt werden, die durch getrennt sind "[" und "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Implementieren Sie eine Gliederung Taggers  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `OutliningTagger`.  
  
2. Importieren Sie die folgenden Namespaces ein.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Erstellen Sie eine Klasse, die mit dem Namen `OutliningTagger`, und lassen Sie sie implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Fügen Sie einige Felder zum Nachverfolgen der Textpuffer und die Momentaufnahme und für "accumulate" die Sätze von Zeilen, die gekennzeichnet werden sollen, als das Gliedern von Bereichen. Dieser Code enthält eine Liste von Region-Objekten (zu einem späteren Zeitpunkt definiert werden), die die Gliederungsbereiche darstellen.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Fügen Sie einen Tagger-Konstruktor, der die Felder initialisiert den Puffer analysiert und fügt einen Ereignishandler an das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> -Methode, die das Tag instanziiert umfasst. In diesem Beispiel wird vorausgesetzt, dass die Spannen in der <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> an die Methode übergebenen zusammenhängenden, sind, auch wenn dies nicht immer der Fall sein kann. Diese Methode instanziiert ein neues Tag Span aller Gliederungsbereiche.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Deklarieren Sie eine `TagsChanged` -Ereignishandler.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Hinzufügen einer `BufferChanged` -Ereignishandler, der auf reagiert <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignisse durch den Textpuffer zu analysieren.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Fügen Sie eine Methode, die den Puffer analysiert. Im hier angegebene Beispiel dient nur zur Veranschaulichung. Es analysiert synchron den Puffer in geschachtelten Gliederungsbereiche.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Die folgende Hilfsmethode Ruft eine Ganzzahl ab, das Maß der Gliederungen, 1, der am weitesten links stehende Geschwungene Klammern ist.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Die folgende Hilfsmethode übersetzt eine Region (weiter unten in diesem Thema definiert) in einem SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Der folgende Code ist nur zur Veranschaulichung. Es definiert eine PartialRegion-Klasse, die die Zeilennummer und den Offset vom Anfang des einen Gliederungsbereich sowie einen Verweis auf den übergeordneten Bereich (sofern vorhanden) enthält. Dies ermöglicht den Parser einrichten geschachtelt, Gliedern von Bereichen. Eine abgeleitete Klasse für die Region enthält einen Verweis auf die Zeilennummer des Endes des einen Gliederungsbereich.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementieren eines Taggers-Anbieters  
 Sie müssen einen Tagger-Anbieter für Ihre Tagger exportieren. Den Tagger-Anbieter erstellt ein `OutliningTagger` für einen Puffer der Inhaltstyp "Text" oder andere gibt einen `OutliningTagger` , wenn der Puffer bereits vorhanden.  
  
#### <a name="to-implement-a-tagger-provider"></a>Zum Implementieren eines Taggers-Anbieters  
  
1. Erstellen Sie eine Klasse, die mit dem Namen `OutliningTaggerProvider` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, und exportieren Sie es mit den Attributen ContentType und TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode durch das Hinzufügen einer `OutliningTagger` an den Eigenschaften des Puffers.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe OutlineRegionTest, und führen Sie es in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Zum Erstellen und Testen der Lösung OutlineRegionTest  
  
1. Erstellen Sie die Projektmappe.  
  
2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3. Erstellen einer Textdatei Geben Sie Text, der der öffnenden geschweiften Klammer und der schließenden geschweiften Klammer enthält.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Es sollte ein Gliederungsbereich, der beiden geschweiften Klammern enthält. Sie sollten das Minuszeichen links neben die öffnende geschweifte Klammer zum Reduzieren des Gliederungsbereichs klicken können. Wenn der Bereich reduziert werden, wird das Symbol mit den Auslassungszeichen (...) sollte angezeigt werden, auf der linken Seite des reduzierten Bereich, und ein Popup mit dem Text **auf Text zeigen** sollte angezeigt werden, wenn Sie den Mauszeiger über die Schaltfläche bewegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
