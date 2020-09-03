---
title: Editor Importe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1fc32d0126d912acab104ecefe3cb62d80b8513f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690317"
---
# <a name="editor-imports"></a>Editor-Importe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Reihe von Editor Diensten, Factorys und Brokern importieren, die ihre Erweiterung mit unterschiedlichen Arten von Zugriff auf den Kern-Editor bereitstellen. Beispielsweise können Sie den importieren, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> für einen bestimmten Inhaltstyp ein bereitzustellen. (Mit diesem Navigator können Sie verschiedene Arten von Such Vorgängen in einem Text Puffer ausführen.)  
  
 Um einen Editor-Import zu verwenden, importieren Sie ihn als Feld oder Eigenschaft einer Klasse, die einen Managed Extensibility Framework Komponenten Teils exportiert.  
  
> [!NOTE]
> Weitere Informationen zum Managed Extensibility Framework finden Sie unter [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Import Syntax  
 Im folgenden Beispiel wird gezeigt, wie der Editor Optionen-Factory-Dienst importiert wird.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Wenn Sie den Dienst als ein Feld und keine Eigenschaft importieren möchten, sollten Sie es `null` in der Deklaration auf festlegen, um die Compilerwarnungen zu vermeiden, die einer Variablen nicht zugewiesen werden:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Weitere Beispiele für die Verwendung von Importen finden Sie in den folgenden exemplarischen Vorgehensweisen:  
  
 [Exemplarische Vorgehensweise: Erstellen einer Randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Exemplarische Vorgehensweise: Anpassen der Textansicht](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen der Signaturhilfe](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Smarttags](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Importieren des Dienstanbieters  
 Sie können auch eine <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (die in der Assembly Microsoft. VisualStudio. Shell. immutable. 10.0 enthalten ist) auf dieselbe Weise importieren, um Zugriff auf Visual Studio-Dienste zu erhalten:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Zugreifen auf das DTE-Objekt aus einer Editor-Erweiterung](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) .  
  
## <a name="services"></a>Dienste  
 Editor Dienste sind im allgemeinen einzelne Entitäten, die einen Dienst bereitstellen und für mehrere Komponenten freigegeben sind.  
  
|Importieren|Stellt|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Die Beziehung zwischen Dateierweiterungen und <xref:Microsoft.VisualStudio.Utilities.IContentType> Objekten.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Die Auflistung von <xref:Microsoft.VisualStudio.Utilities.IContentType>-Objekten.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>-Objekte|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Viele Editor-Adapter Objekte:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Ein- <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> Objekt für eine angegebene Textansicht.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|<xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Eine <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> von unterschieden.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Eine <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> von unterschieden.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> oder ein <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> für einen Satz von- <xref:Microsoft.VisualStudio.Text.ITextBuffer> Objekten.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> für ein <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> für ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> für ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> für ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Verwaltet die Auflistung von- <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Objekten.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> für einen Text Puffer.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> für eine Textansicht.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Die <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> für den angegebenen Bereich.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> für eine Textansicht.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ein <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> für ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ruft den automatischen Einzug durch die- <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> Objekte ab.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Verwaltet die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> für einen <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generiert RTF-formatierten Text aus einer Reihe von Momentaufnahme spannen.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> für ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Ein <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> zum Formatieren von Textzeilen in einer Ansicht.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Ein- <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> Objekt für ein-Objekt <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Durchsucht eine Text Momentaufnahme.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Ein <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> für einen <xref:Microsoft.VisualStudio.Text.ITextBuffer> durch <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Ein <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> für eine Textansicht.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Ein Standardsatz von Symbolen.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Ein <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> für ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Verfolgt die Tastatur Behandlung.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standard <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Objekte.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Behält die Beziehung zwischen Text Puffern und  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> Objekten bei.|  
  
## <a name="other-imports"></a>Andere Importe  
 Anbieterfactorys und-Broker sind im allgemeinen Entitäten, die mehrere Instanzen in mehreren Komponenten aufweisen können.  
  
|Importieren|Stellt|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> vom Typ <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) für den angegebenen Puffer.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Ein textmarkertagger ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> vom Typ <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Ein <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> für einen angegebenen <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)
