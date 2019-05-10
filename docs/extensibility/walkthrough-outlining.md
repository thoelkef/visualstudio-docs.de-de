---
title: 'Exemplarische Vorgehensweise: Gliedern | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 908b2f2b7a0dc055065abd96df3eb4495ad30ce8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965053"
---
# <a name="walkthrough-outlining"></a>Exemplarische Vorgehensweise: Gliedern
Richten Sie die Sprache basierenden Funktionen wie z. B. das Gliedern von definiert die Arten der Textbereiche, die Sie erweitern oder reduzieren möchten. Sie können Regionen im Kontext von einem Sprachdienst zu definieren oder definieren eigene Erweiterung und Inhalt Dateinamentyp und gelten von der Region-Definition für nur diesen Typ, oder wenden die Definitionen für die Region auf einem vorhandenen Inhaltstyp (z. B. "Text"). Diese exemplarische Vorgehensweise veranschaulicht das Definieren und Anzeigen von Gliederungsbereiche.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015 können installieren nicht Sie das Visual Studio SDK aus dem Downloadcenter. Es wurde als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen Sie ein Projekt Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen eines VSIX-Projekts Nennen Sie die Projektmappe `OutlineRegionTest`.

2. Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-an-outlining-tagger"></a>Implementieren Sie eine Gliederung Taggers
 Gliederungsbereiche werden markiert, eine Art von Tags (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Dieses Tag stellt die Gliederung Verhalten. Die gegliederte Bereich kann erweitert oder reduziert werden. Die gegliederte Bereich ist gekennzeichnet durch ein Pluszeichen (**+**) falls er reduziert ist, oder ein Minuszeichen (-) (**-**), wenn er erweitert, und die erweiterte Region durch eine vertikale Linie abgegrenzt wird.

 Die folgenden Schritte zeigen, wie Sie einen Tagger definieren, die Gliederungsbereiche für alle Regionen, die durch die Klammern getrennt erstellt (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Implementieren Sie eine Gliederung Taggers

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `OutliningTagger`.

2. Importieren Sie die folgenden Namespaces ein.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Erstellen Sie eine Klasse, die mit dem Namen `OutliningTagger`, und lassen Sie sie implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Fügen Sie einige Felder zum Nachverfolgen der Textpuffer und die Momentaufnahme und für "accumulate" die Sätze von Zeilen, die gekennzeichnet werden sollen, als das Gliedern von Bereichen. Dieser Code enthält eine Liste von Region-Objekten (zu einem späteren Zeitpunkt definiert werden), die die Gliederungsbereiche darstellen.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Fügen Sie einen Tagger-Konstruktor, der die Felder initialisiert den Puffer analysiert und fügt einen Ereignishandler an das <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignis.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> -Methode, die das Tag instanziiert umfasst. In diesem Beispiel wird vorausgesetzt, dass die Spannen in der <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> an die Methode übergebenen zusammenhängenden, sind, auch wenn es nicht immer der Fall sein kann. Diese Methode instanziiert ein neues Tag Span aller Gliederungsbereiche.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Deklarieren Sie eine `TagsChanged` -Ereignishandler.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Hinzufügen einer `BufferChanged` -Ereignishandler, der auf reagiert <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> Ereignisse durch den Textpuffer zu analysieren.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Fügen Sie eine Methode, die den Puffer analysiert. Im hier angegebene Beispiel dient nur zur Veranschaulichung. Es analysiert synchron den Puffer in geschachtelten Gliederungsbereiche.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Die folgende Hilfsmethode Ruft eine Ganzzahl ab, das Maß der Gliederungen, 1, der am weitesten links stehende Geschwungene Klammern ist.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Die folgende Hilfsmethode übersetzt eine Region (weiter unten in diesem Artikel definiert) in einem SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Der folgende Code ist nur zur Veranschaulichung. Es definiert eine PartialRegion-Klasse, die die Zeilennummer und den Offset vom Anfang des einen Gliederungsbereich und einen Verweis auf den übergeordneten Bereich (sofern vorhanden) enthält. Dieser Code ermöglicht den Parser einrichten geschachtelt, Gliedern von Bereichen. Eine abgeleitete Klasse für die Region enthält einen Verweis auf die Zeilennummer des Endes des einen Gliederungsbereich.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementieren eines Taggers-Anbieters
 Exportieren Sie einen Tagger-Anbieter für Ihre Tagger. Den Tagger-Anbieter erstellt ein `OutliningTagger` für einen Puffer der Inhaltstyp "Text" oder andere gibt einen `OutliningTagger` , wenn der Puffer bereits vorhanden.

### <a name="to-implement-a-tagger-provider"></a>Zum Implementieren eines Taggers-Anbieters

1. Erstellen Sie eine Klasse, die mit dem Namen `OutliningTaggerProvider` implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, und exportieren Sie es mit den Attributen ContentType und TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implementieren der <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode durch das Hinzufügen einer `OutliningTagger` an den Eigenschaften des Puffers.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projektmappe OutlineRegionTest, und führen Sie es in der experimentellen Instanz.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Zum Erstellen und Testen der Lösung OutlineRegionTest

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen einer Textdatei Geben Sie Text, der die öffnenden Klammern und die schließenden Klammern enthält.

    ```
    [
       Hello
    ]
    ```

4. Es sollte ein Gliederungsbereich, der sowohl eckige Klammern enthält. Sie sollten das Minuszeichen links neben der öffnenden Klammer zum Reduzieren des Gliederungsbereichs klicken können. Wenn der Bereich reduziert werden, wird das Symbol mit den Auslassungszeichen (*...* ) sollte angezeigt werden, auf der linken Seite des reduzierten Bereich, und ein Popup mit dem Text **auf Text zeigen** sollte angezeigt werden, wenn Sie den Mauszeiger über die Schaltfläche bewegen.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Verknüpfen Sie einen Inhaltstyp mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)