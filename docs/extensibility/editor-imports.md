---
title: Editor-Importe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99619efa5181fbcf299e99cde60b8879731c0c74
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715634"
---
# <a name="editor-imports"></a>Editor-Importe
Sie können eine Anzahl von Editor-Dienste, Factorys und Broker, mit die die Erweiterung verschiedene Arten des Zugriffs auf die Kern-Editor zu ermöglichen, importieren. Sie können z. B. Importieren der <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> bereit mit einem <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> für einen bestimmten Inhaltstyp. (Dieses Navigators ermöglicht, dass Sie verschiedene Arten von Suchvorgängen für einen Textpuffer ausführen.)

 Um einen Import Editor verwenden, importieren Sie sie als ein Feld oder eine Eigenschaft einer Klasse, die von einer Managed Extensibility Framework-Komponente exportiert.

> [!NOTE]
>  Weitere Informationen über das Managed Extensibility Framework, finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Importsyntax
 Das folgende Beispiel zeigt den Editor importieren Optionen Factory-Dienst.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Wenn Sie den Dienst als ein Feld und keine Eigenschaft importieren möchten, legen Sie es auf `null` in der Deklaration, um die Compiler-Warnungen zu nicht zuweisen zu einer Variablen zu vermeiden:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Weitere Beispiele für die Verwendung von Importen finden Sie in den folgenden exemplarischen Vorgehensweisen:

- [Exemplarische Vorgehensweise: Erstellen einer randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Exemplarische Vorgehensweise: Anpassen der Textansicht](../extensibility/walkthrough-customizing-the-text-view.md)

- [Exemplarische Vorgehensweise: Hervorheben von text](../extensibility/walkthrough-highlighting-text.md)

- [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Exemplarische Vorgehensweise: Signaturhilfe anzeigen](../extensibility/walkthrough-displaying-signature-help.md)

- [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)

- [Exemplarische Vorgehensweise: Anzeigen einer Glühbirne gekennzeichneten Vorschlägen](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importieren Sie den Service-Anbieter
 Sie können auch Importieren einer <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (gefunden in der Assembly Microsoft.VisualStudio.Shell.Immutable.10.0) auf die gleiche Weise für den Zugriff auf Visual Studio-Diensten:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Zugriff auf das DTE-Objekt aus einer Editor-Erweiterung](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) für Weitere Informationen.

## <a name="services"></a>Dienste
 Editor-Dienste sind, in der Regel einzelnen Entitäten, die einen Service bieten, und werden über mehrere Komponenten gemeinsam genutzt wird.

|Importieren|Enthält|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Die Beziehung zwischen Dateierweiterungen und <xref:Microsoft.VisualStudio.Utilities.IContentType> Objekte.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Die Auflistung von <xref:Microsoft.VisualStudio.Utilities.IContentType>-Objekten.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>-Objekte|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Viele Objekte für die Editor-Adapter:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> -Objekt für eine angegebene Textansicht.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Eine <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Eine <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Ein <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> Unterschiede.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Ein <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> Unterschiede.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> oder <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> für einen Satz von <xref:Microsoft.VisualStudio.Text.ITextBuffer> Objekte.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> für eine <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Verwaltet die Auflistung der <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Objekte.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> für einen Textpuffer.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> für eine Textansicht.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Die <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> für den angegebenen Bereich.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> für eine Textansicht.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ein <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ruft den automatischen Einzug, über die <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> Objekte.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Verwaltet die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> für eine <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Eine <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generiert RTF-formatierten Text aus einer Reihe von Momentaufnahmespannen.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Ein <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> zum Formatieren von Textzeilen in einer Ansicht.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> Objekt für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Sucht eine Textmomentaufnahme.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Ein <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> für eine <xref:Microsoft.VisualStudio.Text.ITextBuffer> von <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Ein <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> für eine Textansicht.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Ein Standardsatz von Symbolen.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Ein <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Verfolgt Tastatur behandeln.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standard <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Objekte.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Verwaltet die Beziehung zwischen Textpuffern und <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> Objekte.|

## <a name="other-imports"></a>Andere Importvorgänge
 Wertanbieterfactorys und Makler sind im Allgemeinen Entitäten, die mehrere Instanzen in mehreren Komponenten verwenden können.

|Importieren|Enthält|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Eine <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> des Typs <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) für den angegebenen Puffer.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Einen Textmarkierungstagger (einen <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> des Typs <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Ein <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> für einen bestimmten <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Eine <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Eine <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Eine <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Siehe auch
- [Language-Dienst und -Editor-Erweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
