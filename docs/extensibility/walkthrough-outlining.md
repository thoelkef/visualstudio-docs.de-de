---
title: 'Exemplarische Vorgehensweise: Gliederung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697213"
---
# <a name="walkthrough-outlining"></a>Exemplarische Vorgehensweise: Gliedern
Richten Sie sprachbasierte Features ein, z. B. umreißen, indem Sie die Arten von Textbereichen definieren, die Sie erweitern oder reduzieren möchten. Sie können Regionen im Kontext eines Sprachdienstes definieren oder eine eigene Dateinamenerweiterung und einen eigenen Inhaltstyp definieren und die Regionsdefinition nur auf diesen Typ anwenden oder die Regionsdefinitionen auf einen vorhandenen Inhaltstyp anwenden (z. B. "Text"). In dieser exemplarischen Vorgehensweise wird gezeigt, wie Gliederungsbereiche definiert und angezeigt werden.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen eines MEF-Projekts (Managed Extensibility Framework)

### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen eines VSIX-Projekts Nennen Sie die Projektmappe `OutlineRegionTest`.

2. Fügen Sie dem Projekt eine Editor-Klassifierelementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-an-outlining-tagger"></a>Implementieren eines Gliederungs-Taggers
 Umrissbereiche sind durch eine Art<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>Tag ( ) gekennzeichnet. Dieses Tag stellt das Standard-Umrissverhalten bereit. Der umrissene Bereich kann erweitert oder reduziert werden. Der umrissene Bereich wird durch**+** ein Pluszeichen ( ) gekennzeichnet,**-** wenn er reduziert wird, oder durch ein Minuszeichen ( ), wenn er erweitert wird, und der erweiterte Bereich durch eine vertikale Linie abgegrenzt wird.

 Die folgenden Schritte zeigen, wie Sie einen Tagger definieren, der Gliederungsbereiche für alle regionen erstellt, die durch die Klammern (**[**,**]**) begrenzt sind.

### <a name="to-implement-an-outlining-tagger"></a>So implementieren Sie einen Gliederungs-Tagger

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `OutliningTagger`.

2. Importieren Sie die folgenden Namespaces.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Erstellen Sie `OutliningTagger`eine Klasse mit <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>dem Namen , und lassen Sie sie implementieren:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Fügen Sie einige Felder hinzu, um den Textpuffer und den Snapshot nachzuverfolgen und um die Zeilensätze zu akkumulieren, die als Gliederungsbereiche gekennzeichnet werden sollen. Dieser Code enthält eine Liste der Region-Objekte (die später definiert werden sollen), die die Gliederungsbereiche darstellen.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Fügen Sie einen Tagger-Konstruktor hinzu, der die Felder initialisiert, <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> den Puffer analysiert und dem Ereignis einen Ereignishandler hinzufügt.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Sie die Methode, die die Tag-Spannen instanziiert. In diesem Beispiel wird davon <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> ausgegangen, dass die Spannen in der übergebenen Methode zusammenhängend sind, auch wenn dies möglicherweise nicht immer der Fall ist. Diese Methode instanziiert eine neue Tag-Spanne für jede der Gliederungsbereiche.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Deklarieren Sie einen `TagsChanged` Ereignishandler.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Fügen `BufferChanged` Sie einen Ereignishandler <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> hinzu, der auf Ereignisse reagiert, indem Sie den Textpuffer analysieren.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Fügen Sie eine Methode hinzu, die den Puffer analysiert. Das hier gegebene Beispiel dient nur zur Veranschaulichung. Es analysiert den Puffer synchron in verschachtelte Gliederungsbereiche.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Die folgende Hilfsmethode ruft eine ganze Zahl ab, die die Ebene der Gliederung darstellt, sodass 1 das linke Klammerpaar ist.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Die folgende Hilfsmethode übersetzt eine Region (definiert weiter unten in diesem Artikel) in einen SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Der folgende Code dient nur zur Veranschaulichung. Es definiert eine PartialRegion-Klasse, die die Zeilennummer und den Offset des Anfangs einer Gliederungsregion sowie einen Verweis auf den übergeordneten Bereich (falls vorhanden) enthält. Dieser Code ermöglicht es dem Parser, verschachtelte Gliederungsbereiche einzurichten. Eine abgeleitete Region-Klasse enthält einen Verweis auf die Zeilennummer des Endes einer Gliederungsregion.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementieren eines Tagger-Anbieters
 Exportieren Sie einen Tagger-Anbieter für Ihren Tagger. Der Tagger-Anbieter `OutliningTagger` erstellt einen für einen Puffer des Inhaltstyps "text", oder gibt einen zurück, wenn der Puffer bereits über einen `OutliningTagger` puffer verfügt.

### <a name="to-implement-a-tagger-provider"></a>So implementieren Sie einen Tagger-Anbieter

1. Erstellen Sie `OutliningTaggerProvider` eine Klasse <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>mit dem Namen , die implementiert, und exportieren Sie sie mit den Attributen ContentType und TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Sie die `OutliningTagger` Methode, indem Sie den Eigenschaften des Puffers eine hinzufügen.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die OutlineRegionTest-Lösung, und führen Sie sie in der experimentellen Instanz aus.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>So erstellen und testen Sie die OutlineRegionTest-Lösung

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen einer Textdatei Geben Sie Text ein, der sowohl die öffnenden als auch die schließenden Klammern enthält.

    ```
    [
       Hello
    ]
    ```

4. Es sollte einen Umrissbereich geben, der beide Klammern enthält. Sie sollten in der Lage sein, auf das Minuszeichen links neben der geöffneten Klammer zu klicken, um den Gliederungsbereich zu reduzieren. Wenn der Bereich reduziert wird, sollte das Auslassungssymbol (*...*) links neben dem reduzierten Bereich angezeigt werden, und ein Popup mit dem **Texthover-Text** sollte angezeigt werden, wenn Sie den Zeiger über die Auslassungspunkte bewegen.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
