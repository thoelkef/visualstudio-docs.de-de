---
title: Editor Importe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712010"
---
# <a name="editor-imports"></a>Editor-Importe
Sie können eine Reihe von Editordiensten, Fabriken und Brokern importieren, die Ihrer Erweiterung verschiedene Arten von Zugriff auf den Kerneditor bieten. Sie können z. <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> importieren, um Ihnen eine für einen bestimmten Inhaltstyp bereitzustellen. (Mit diesem Navigator können Sie verschiedene Arten von Suchvorgängen für einen Textpuffer durchführen.)

 Um einen Editorimport zu verwenden, importieren Sie ihn als Feld oder Eigenschaft einer Klasse, die ein Managed Extensibility Framework-Komponententeil exportiert.

> [!NOTE]
> Weitere Informationen zum Managed Extensibility Framework finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Importsyntax
 Das folgende Beispiel zeigt, wie sie den Factorydienst für Editoroptionen importieren.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Wenn Sie den Dienst als Feld und nicht als Eigenschaft `null` importieren möchten, sollten Sie ihn in der Deklaration aufsetzen, um zu vermeiden, dass die Compilerwarnungen über das Zuweisen zu einer Variablen vermieden werden:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Weitere Beispiele für die Verwendung von Importen finden Sie in den folgenden exemplarischen Vorgehensweisen:

- [Exemplarische Vorgehensweise: Erstellen einer Rand-Glyphe](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Exemplarische Vorgehensweise: Anpassen der Textansicht](../extensibility/walkthrough-customizing-the-text-view.md)

- [Exemplarische Vorgehensweise: Text hervorheben](../extensibility/walkthrough-highlighting-text.md)

- [Exemplarische Vorgehensweise: QuickInfo-Tooltips anzeigen](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Exemplarische Vorgehensweise: Signaturhilfe anzeigen](../extensibility/walkthrough-displaying-signature-help.md)

- [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)

- [Walkthrough: Anzeigen von Glühbirnenvorschlägen](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importieren des Dienstanbieters
 Sie können auch <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> eine (in der Assembly Microsoft.VisualStudio.Shell.Immutable.10.0) auf die gleiche Weise importieren, um Zugriff auf Visual Studio-Dienste zu erhalten:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Weitere Informationen finden Sie [unter Exemplarvorgehensweise: Greifen Sie über eine Editorerweiterung auf das DTE-Objekt](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) zu.

## <a name="services"></a>Dienste
 Editordienste sind im Allgemeinen einzelne Entitäten, die einen Dienst bereitstellen und über mehrere Komponenten hinweg gemeinsam genutzt werden.

|Importieren|Bietet|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Die Beziehung zwischen <xref:Microsoft.VisualStudio.Utilities.IContentType> Dateierweiterungen und Objekten.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Die Auflistung der <xref:Microsoft.VisualStudio.Utilities.IContentType>-Objekte.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Objekte.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Viele Editor-Adapterobjekte:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> Objekt für eine bestimmte Textansicht.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.ITextBuffer>-Element.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.ITextDocument>-Element.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Eine <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> der Unterschiede.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Eine <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> der Unterschiede.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Eine <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> oder <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>eine .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> für eine <xref:Microsoft.VisualStudio.Text.ITextBuffer> Gruppe von Objekten.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> für <xref:Microsoft.VisualStudio.Text.ITextBuffer>eine .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> für <xref:Microsoft.VisualStudio.Text.Editor.ITextView>eine .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> für <xref:Microsoft.VisualStudio.Text.Editor.ITextView>eine .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> für <xref:Microsoft.VisualStudio.Text.Editor.ITextView>eine .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Behält die <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Auflistung von Objekten bei.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|An <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> für einen Textpuffer.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> für eine Textansicht.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Die <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> für den angegebenen Bereich.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> für eine Textansicht.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ein <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> für <xref:Microsoft.VisualStudio.Text.Editor.ITextView>eine .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ruft den automatischen Einzug <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> durch die Objekte ab.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Verwaltet <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>for a .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>-Element.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generiert RTF-formatierten Text aus einer Reihe von Snapshot-Spannen.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> für <xref:Microsoft.VisualStudio.Text.Editor.ITextView>eine .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> zum Formatieren von Textzeilen in einer Ansicht.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> Objekt <xref:Microsoft.VisualStudio.Text.Editor.ITextView>für eine .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Durchsucht einen Text-Snapshot.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|An <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> for <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>an by .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Ein <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> für eine Textansicht.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Ein Standardsatz von Glyphen.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Ein <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> für <xref:Microsoft.VisualStudio.Text.Editor.ITextView>eine .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Verfolgt die Tastaturbehandlung.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standardobjekte. <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Behält die Beziehung zwischen <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> Textpuffern und Objekten bei.|

## <a name="other-imports"></a>Sonstige Einfuhren
 Anbieterfabriken und Broker sind im Allgemeinen Entitäten, die mehrere Instanzen in mehreren Komponenten haben können.

|Importieren|Bietet|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> vom <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>Typ ) für den angegebenen Puffer.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Ein Textmarker-Tagger <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> (ein Typ <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Ein <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> für <xref:Microsoft.VisualStudio.Text.Editor.ITextView>eine bestimmte .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Ein <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>-Element.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Ein <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>-Element.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Ein <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>-Element.|

## <a name="see-also"></a>Weitere Informationen
- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
