---
title: Editor-Importe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 2c7daddb7cd40dd0e5d24f01df141ce30ba713f9
ms.lasthandoff: 02/22/2017

---
# <a name="editor-imports"></a>Imports-Editor
Sie können eine Anzahl von Editor Dienste, Factorys und Brokern, die Ihre Erweiterung verschiedene Arten des Zugriffs auf die Core-Editor bieten importieren. Importieren Sie z. B. die <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>ermöglichen Ihnen eine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>für einen bestimmten Inhaltstyp.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (Dieser Navigator können Sie verschiedene Arten von Suchen in einem Textpuffer ausführen.)  
  
 Um einen Import Editor zu verwenden, importieren Sie es als ein Feld oder eine Eigenschaft einer Klasse, die von einer Komponente Managed Extensibility Framework exportiert.  
  
> [!NOTE]
>  Weitere Informationen über das Managed Extensibility Framework finden Sie unter [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Import-Syntax  
 Im folgenden Beispiel wird veranschaulicht, wie den Editor importieren Optionen Factory-Dienst.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Wenn Sie den Dienst als ein Feld und keine Eigenschaft importieren möchten, legen Sie es auf `null` in der Deklaration, um den Compiler-Warnungen zu keiner Variablen zuweisen zu vermeiden:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Weitere Beispiele zur Verwendung von Importen finden Sie in den folgenden exemplarischen Vorgehensweisen:  
  
 [Exemplarische Vorgehensweise: Erstellen einer Randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Exemplarische Vorgehensweise: Anpassen der Textansicht](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Smarttags](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Importieren des Dienstanbieters  
 Sie können auch Importieren einer <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>(zu finden in der Assembly Microsoft.VisualStudio.Shell.Immutable.10.0) auf die gleiche Weise für den Zugriff auf Visual Studio-Dienste:</xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Finden Sie unter [Exemplarische Vorgehensweise: Zugreifen auf das DTE-Objekt über eine Editor-Erweiterung](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) Weitere Informationen.  
  
## <a name="services"></a>Dienste  
 Editor-Dienste sind in der Regel die einzigen Entitäten, die eine und mehrere Komponenten gemeinsam sind.  
  
|Importieren|Enthält|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService></xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Die Beziehung zwischen Dateierweiterungen und <xref:Microsoft.VisualStudio.Utilities.IContentType>Objekte.</xref:Microsoft.VisualStudio.Utilities.IContentType>|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService></xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Die Auflistung der <xref:Microsoft.VisualStudio.Utilities.IContentType>Objekte.</xref:Microsoft.VisualStudio.Utilities.IContentType>|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService></xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Objekte</xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService></xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Viele Objekte in einer Editor-Adapter:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService></xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>-Objekt für eine angegebene Textansicht.</xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService></xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextBuffer>.</xref:Microsoft.VisualStudio.Text.ITextBuffer>|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService></xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextDocument>.</xref:Microsoft.VisualStudio.Text.ITextDocument>|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService></xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Ein <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>Unterschiede.</xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601>|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService></xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Ein <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>Unterschiede.</xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection>|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService></xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>oder eine <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.</xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> </xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService></xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>für einen Satz von <xref:Microsoft.VisualStudio.Text.ITextBuffer>Objekte.</xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService></xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>für eine <xref:Microsoft.VisualStudio.Text.ITextBuffer>.</xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Classification.IClassifier>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService></xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IClassifier>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService></xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService></xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Ein <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap>|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService></xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Verwaltet die Auflistung der <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Objekte.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService></xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>für einen Textpuffer.</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService></xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>für eine Textansicht.</xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601>|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService></xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Die <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>für den angegebenen Bereich.</xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions>|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService></xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>für eine Textansicht.</xref:Microsoft.VisualStudio.Text.Editor.IScrollMap>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService></xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ein <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService></xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ruft den automatischen Einzugs und der <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>Objekte.</xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider>|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService></xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Verwaltet die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>für eine <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|An <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.</xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService></xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Wird Text im RTF-Format aus einem Satz von Spannen Snapshot generiert.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer>|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService></xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Ein <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>zur Formatierung von Textzeilen in einer Ansicht.</xref:System.Windows.Media.TextFormatting.TextParagraphProperties>|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService></xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Ein <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>Objekt für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService></xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Sucht eine Textmomentaufnahme.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService></xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Ein <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>für eine <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>.</xref:Microsoft.VisualStudio.Utilities.IContentType> </xref:Microsoft.VisualStudio.Text.ITextBuffer> </xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService></xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Ein <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>für eine Textansicht.</xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService></xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Ein Standardsatz von Symbolen.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService></xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Ein <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>für eine <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService></xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Verfolgt Tastenkombination behandeln.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService></xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standard <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Objekte.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry></xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Verwaltet die Beziehung zwischen Textpuffer und <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>Objekte.</xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory>|  
  
## <a name="other-imports"></a>Weitere Importe  
 Anbieterfactorys und Makler sind im Allgemeinen Entitäten, die mehrere Instanzen in mehreren Komponenten verwenden können.  
  
|Importieren|Enthält|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Ein <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>vom Typ <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) für den angegebenen Puffer.</xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> </xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Einen Textmarkierungstagger (einen <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>vom Typ <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601>|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory></xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Ein <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>für einen bestimmten <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.</xref:Microsoft.VisualStudio.Text.Editor.ITextView> </xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker></xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker></xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker></xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>|  
  
## <a name="see-also"></a>Siehe auch  
 [Language Service und Erweiterungspunkte-Editor](../extensibility/language-service-and-editor-extension-points.md)
