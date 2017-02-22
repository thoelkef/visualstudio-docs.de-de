---
title: "Exemplarische Vorgehensweise: Gliedern | Microsoft Docs"
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
  - "Editoren [Visual Studio SDK] neue - Gliederung"
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Gliedern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können\-basierter Funktionen wie z. B. Gliederung durch Definieren der Arten von Textbereiche, die Sie erweitern oder reduzieren möchten, implementieren. Sie können Bereiche definieren, im Kontext eines Sprachdiensts können eigene Erweiterung und Inhalt Dateinamentyp und definiert den Bereich Definition nur diesem Typ oder können Sie die Definitionen der Region auf einem vorhandenen Inhaltstyp \(z. B. "Text"\) anwenden. In dieser exemplarischen Vorgehensweise veranschaulicht das Definieren und Gliederungsbereiche anzeigen.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts \(Managed Extensibility Framework\)  
  
#### So erstellen Sie ein MEF\-Projekt  
  
1.  Erstellen Sie ein VSIX\-Projekt. Nennen Sie die Projektmappe `OutlineRegionTest`.  
  
2.  Fügen Sie dem Projekt eine Classifier\-Editor\-Elementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## Implementieren eine Gliederung Tagger  
 Gliederungsbereiche markiert wurde, eine Art von Tag \(<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>\). Dieses Tag enthält die Standard\-Verhalten gliedern. Die gegliederte Bereich kann erweitert oder reduziert werden. Gegliederte Bereich wird durch ein Pluszeichen \(\+\), wenn es ausgeblendet ist oder ein Minuszeichen markiert, wenn er erweitert und erweiterte Bereich durch eine vertikale Linie abgegrenzt wird.  
  
 Die folgenden Schritte zeigen, wie eine Tagger definiert, die Gliederungsbereiche für alle Regionen erstellt werden, die durch getrennt sind "\[" und "\]".  
  
#### Um eine Gliederung Tagger zu implementieren.  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie es `OutliningTagger`.  
  
2.  Importieren Sie die folgenden Namespaces.  
  
     [!code-cs[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Erstellen Sie eine Klasse mit dem Namen `OutliningTagger`, und implementieren Sie <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-cs[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Fügen Sie einige Felder, die Textpuffer und die Momentaufnahme nachverfolgt und die Sätze von Zeilen zu sammeln, die als Gliederungsbereiche markiert werden sollen. Dieser Code enthält eine Liste der Regionsobjekte \(später definiert\), die Gliederungsbereiche darstellen.  
  
     [!code-cs[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Fügen Sie einen Tagger\-Konstruktor, der die Felder initialisiert den Puffer analysiert und fügt einen Ereignishandler für das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.  
  
     [!code-cs[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> \-Methode, die das Tag instanziiert umfasst. In diesem Beispiel wird vorausgesetzt, dass die Spannen in der <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> an die Methode übergebenen sind zusammenhängend, obwohl dies möglicherweise nicht immer der Fall. Diese Methode erstellt eine neues Tagspanne aller Gliederungsbereiche.  
  
     [!code-cs[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Deklarieren Sie eine `TagsChanged` \-Ereignishandler.  
  
     [!code-cs[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Hinzufügen einer `BufferChanged` \-Ereignishandler, auf die reagiert <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignisse durch das Analysieren des Textpuffers.  
  
     [!code-cs[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Fügen Sie eine Methode, die den Puffer analysiert. Das hier gezeigte Beispiel dient nur zur Veranschaulichung. Synchron Puffer in geschachtelten Gliederungsbereiche eingelesen.  
  
     [!code-cs[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. Die folgende Hilfsmethode Ruft eine Ganzzahl, die Zugriffsebene der Gliederung darstellt, 1, der am weitesten links stehende Geschwungene Klammern ist.  
  
     [!code-cs[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. Die folgende Hilfsmethode übersetzt eine Region \(weiter unten in diesem Thema definiert\) in eine SnapshotSpan ab.  
  
     [!code-cs[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. Der folgende Code dient nur zur Veranschaulichung. Es definiert eine PartialRegion\-Klasse, die Zeilennummer und den Offset vom Anfang des einen Gliederungsbereich sowie einen Verweis auf den übergeordneten Bereich \(sofern vorhanden\) enthält. Dies ermöglicht den Parser einrichten Gliederungsbereiche geschachtelt. Eine abgeleitete Klasse für die Region enthält einen Verweis auf die Nummer der am Ende einen Gliederungsbereich.  
  
     [!code-cs[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## Implementieren eines Anbieters Tagger  
 Sie müssen einen Anbieter Tagger für Ihre Tagger exportieren. Erstellt der Anbieter Tagger ein `OutliningTagger` für einen Puffer der Inhaltstyp "Text" oder andere gibt einen `OutliningTagger` wenn der Puffer vorhanden ist.  
  
#### Implementierung eines Anbieters tagger  
  
1.  Erstellen Sie eine Klasse mit dem Namen `OutliningTaggerProvider` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, und es mit den Attributen ContentType und TagType exportieren.  
  
     [!code-cs[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode durch Hinzufügen einer `OutliningTagger` auf die Eigenschaften des Puffers.  
  
     [!code-cs[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## Erstellen und Testen des Codes  
 Um diesen Code zu testen, erstellen Sie die Projektmappe OutlineRegionTest, und führen Sie es in der experimentellen Instanz.  
  
#### So erstellen und Testen der Lösung OutlineRegionTest  
  
1.  Erstellen Sie die Projektmappe.  
  
2.  Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
3.  Erstellen einer Textdatei Geben Sie Text, der der öffnenden geschweiften Klammer und der schließenden Klammer enthält.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Es sollte ein Gliederungsbereich, der beiden geschweiften Klammern enthält. Sie sollten das Minuszeichen links neben die öffnende geschweifte Klammer zum Reduzieren des Gliederungsbereichs klicken können. Wenn der Bereich reduziert wird, wird das Symbol mit den Auslassungspunkten \(...\) erscheint links neben den reduzierten Bereich, und ein Popup\-Fenster mit dem Text **auf Text zeigen** sollte angezeigt werden, wenn Sie den Mauszeiger über die Schaltfläche bewegen.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit Erweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)