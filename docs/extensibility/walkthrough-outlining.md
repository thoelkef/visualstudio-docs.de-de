---
title: 'Exemplarische Vorgehensweise: Gliedern | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8360daf5ff1e7d94d995bdbefee6228a47e47db8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-outlining"></a>Exemplarische Vorgehensweise: Gliedern
Sie können die Sprache basierende Funktionen wie das Gliedern von definieren die Arten von Textbereiche, die Sie erweitern oder reduzieren möchten implementieren. Sie können Bereiche im Kontext eines Diensts Sprache definieren können Sie definieren Sie eine eigene Erweiterung und Inhalt Dateityp von Name und die Region-Definition auf nur diesen Typ gelten oder Sie können die Definitionen für die Region anwenden, um einen vorhandenen Inhaltstyp (z. B. "Text"). Diese exemplarische Vorgehensweise zeigt, wie definieren und Gliederungsbereiche anzeigen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)  
  
#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt  
  
1.  Erstellen Sie ein VSIX-Projekt. Nennen Sie die Projektmappe `OutlineRegionTest`.  
  
2.  Dem Projekt eine Elementvorlage Editor Klassifizierer hinzugefügt. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementieren einer Gliederung Taggers  
 Gliederungsbereiche werden durch eine Art von Tag gekennzeichnet (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Dieses Tag enthält die Standard-Verhalten gliedern. Die gegliederte Bereich kann erweitert oder reduziert werden. Gegliederte Bereich ist durch ein Pluszeichen, falls er reduziert ist oder ein Minuszeichen (-) gekennzeichnet, wenn es erweitert wird und die erweiterte Region wird durch eine vertikale Linie abgegrenzt.  
  
 Die folgenden Schritte zeigen, wie Sie einen Tagger definieren, die Gliederungsbereiche für alle Regionen erstellt, die von begrenzt sind "[" und "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>So implementieren Sie eine Gliederung tagger  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `OutliningTagger`.  
  
2.  Importieren Sie die folgenden Namespaces hinzu.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Erstellen Sie eine Klasse mit dem Namen `OutliningTagger`, und implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Fügen Sie einige Felder zum Nachverfolgen der Textpuffer und die Momentaufnahme und gesammelt, die Sätze von Zeilen, die als Gliederungsbereiche gekennzeichnet werden sollen. Dieser Code enthält eine Liste der Bereichsobjekte (zu einem späteren Zeitpunkt definiert werden), die die Gliederungsbereiche darstellen.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Fügen Sie einen Tagger-Konstruktor, der die Felder initialisiert den Puffer analysiert und fügt einen Ereignishandler an das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> -Methode, die das Tag instanziiert umfasst. In diesem Beispiel wird vorausgesetzt, dass die Spannen in der <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> an die Methode übergebene sind zusammenhängend, obwohl dies möglicherweise nicht immer die Groß-/Kleinschreibung. Diese Methode wird einen neuer Transponder Span aller Gliederungsbereiche instanziiert.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Deklarieren Sie eine `TagsChanged` -Ereignishandler.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Hinzufügen einer `BufferChanged` Ereignishandler, auf die reagiert <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignisse durch Analysieren der Textpuffers.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Fügen Sie eine Methode, die den Puffer analysiert. Die hier angegebene Beispiel dient nur zur Veranschaulichung. Es analysiert synchron Puffer in geschachtelten Gliederungsbereiche.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Die folgende Hilfsmethode Ruft eine ganze Zahl, die das Maß an die Gliederung darstellt, 1, der am weitesten links stehende Geschwungene Klammern ist.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Die folgende Hilfsmethode übersetzt eine Region (weiter unten in diesem Thema definiert) in einem SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Der folgende Code ist nur zur Veranschaulichung. Es definiert eine PartialRegion-Klasse, die Zeilennummer und den Offset vom Anfang des einen Gliederungsbereich sowie einen Verweis auf den übergeordneten Bereich (sofern vorhanden) enthält. Dies ermöglicht den Parser einrichten Gliederungsbereiche geschachtelt. Eine abgeleitete Klasse der Region enthält einen Verweis auf die Zeilennummer des Endes des einen Gliederungsbereich.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementieren eines Taggers-Anbieters  
 Sie müssen einen Tagger-Anbieter für Ihre Tagger exportieren. Der Tagger-Anbieter erstellt ein `OutliningTagger` für einen Puffer der Inhaltstyp "Text" oder andere gibt einen `OutliningTagger` Falls der Puffer bereits vorhanden.  
  
#### <a name="to-implement-a-tagger-provider"></a>Zum Implementieren eines Taggers-Anbieters  
  
1.  Erstellen Sie eine Klasse mit dem Namen `OutliningTaggerProvider` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, und mit den Attributen ContentType und TagType zu exportieren.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode durch Hinzufügen einer `OutliningTagger` an den Eigenschaften des Puffers.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die OutlineRegionTest-Projektmappe, und führen Sie sie in der experimentellen Instanz.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>So erstellen und Testen der Lösung OutlineRegionTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen einer Textdatei Geben Sie etwas Text ein, die der öffnenden geschweiften Klammer und die schließende geschweifte Klammer enthält.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Es darf ein Gliederungsbereich, der beiden geschweiften Klammern enthält. Sie sollten das Minuszeichen links neben die öffnende geschweifte Klammer zum Reduzieren des Gliederungsbereichs klicken können. Wenn der Bereich reduziert wird, wird das Symbol mit den Auslassungspunkten (...) sollte angezeigt werden, auf der linken Seite des reduzierten Bereich, und ein Popup mit dem Text **Text zeigen** sollte angezeigt werden, wenn Sie den Mauszeiger über den drei Punkten bewegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)