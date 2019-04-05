---
title: Sprachdienst und Erweiterungspunkte-Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 80aed463b2d8ef9d083940a8966574e778623ddd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958952"
---
# <a name="language-service-and-editor-extension-points"></a>Erweiterungspunkte für den Sprachdienst und den Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Editor stellt Erweiterungspunkte, die Sie als Managed Extensibility Framework (MEF) Komponenten, einschließlich der meisten Language Service-Features erweitern können. Dies sind die haupterweiterung zeigen Kategorien:  
  
-   Inhaltstypen  
  
-   Klassifizierungstypen und Klassifizierung-Formate  
  
-   Rändern und Bildlaufleisten  
  
-   Tags  
  
-   Zusatzelemente  
  
-   Maus-Prozessoren  
  
-   Drop-Handler  
  
-   Optionen  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Erweitern von Inhaltstypen  
 Inhaltstypen sind die Definitionen für die Arten von behandelten vom Editor, z. B. Text, "Text", "Code" oder "CSharp". Sie definieren einen neuen Inhaltstyp durch Deklarieren einer Variablen des Typs <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> und dem neuen Inhaltstyp einen eindeutigen Namen. Um den Inhaltstyp für den Editor zu registrieren, exportieren Sie es zusammen mit den folgenden Attributen:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> ist der Name des Inhaltstyps.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> ist der Name des Inhaltstyps von dem dieser Inhaltstyp abgeleitet ist. Ein Inhaltstyp möglicherweise von mehreren anderen Inhaltstypen erben.  
  
  Da die <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Klasse versiegelt ist, können Sie es mit keinen Typparameter exportieren.  
  
  Das folgende Beispiel zeigt die ExportAttribute auf eine Content-Type-Definition.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Content-Arten können auf NULL oder mehr vorhandene Inhaltstypen basieren. Dies sind die integrierten Typen:  
  
- Alle: der grundlegenden Inhaltstyp. Übergeordnete Element aller anderen Inhaltstypen.  
  
- Text: der Basistyp für den Inhalt von nicht-Projektion. Erbt von "any".  
  
- Nur-Text: für Text, ohne Code. Erbt von "Text".  
  
- Code: Code aller Art. Erbt von "Text".  
  
- Inertem: Schließt den Text aus jeder Art von Verarbeitung aus. Text dieses Inhaltstyps müssen nie eine beliebige Erweiterung angewendet wird.  
  
- Projektion: für die Inhalte der Projektionspuffer. Erbt von "any".  
  
- IntelliSense: für den Inhalt von IntelliSense. Erbt von "Text".  
  
- Sighelp: Signaturhilfe zu. Erbt von "Intellisense".  
  
- Sighelp-Doc: Signatur-Hilfedokumentation. Erbt von "Intellisense".  
  
  Dies sind einige der Inhaltstypen, die von Visual Studio definiert sind und andere Sprachen, die in Visual Studio gehostet werden:  
  
- Standard  
  
- C/C++  
  
- ConsoleOutput  
  
- CSharp  
  
- CSS  
  
- ENC  
  
- FindResults  
  
- F#  
  
- HTML  
  
- JScript  
  
- XAML  
  
- XML  
  
  Um die Liste der verfügbaren Inhaltstypen zu ermitteln, importieren die <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, der die Auflistung von Inhaltstypen für den Editor verwaltet. Der folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Verwenden Sie zum Zuordnen eines Inhaltstyps mit einer Dateinamenerweiterung <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  In Visual Studio Dateinamenerweiterungen Weitere Erweiterungen registriert sind, mithilfe der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> auf ein Sprachpaket für den Dienst. Die <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ordnet einen MEF-Inhaltstyp eine Dateinamenerweiterung, die auf diese Weise registriert wurde.  
  
 Um die Dateinamenerweiterung der Content-Type-Definition exportieren, müssen Sie die folgenden Attribute einschließen:  
  
- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Gibt die Dateierweiterung an.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Gibt den Inhaltstyp an.  
  
  Da die <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Klasse versiegelt ist, können Sie es mit keinen Typparameter exportieren.  
  
  Das folgende Beispiel zeigt die ExportAttribute auf eine Dateinamenerweiterung eine Content-Type-Definition.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 Die <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> verwaltet die Zuordnungen zwischen Dateierweiterungen und Inhaltstypen.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Erweitern von Klassifizierungstypen und Klassifizierung formatiert  
 Sie können die Klassifizierungstypen verwenden, um die Arten von Text zu definieren, für die Sie anderen Verarbeitung (z. B. die Farben der Text "Schlüsselwort" Blau und den Text "Kommentar" Grün) bereitstellen möchten. Definieren Sie einen neuen Klassifizierungstyp durch Deklarieren einer Variablen vom Typ <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> und ihm einen eindeutigen Namen.  
  
 Um den Klassifizierungstyp in einem Editor zu registrieren, exportieren Sie es zusammen mit den folgenden Attributen:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Klassifizierungstyps.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: der Name des Klassifizierungstyps, von dem dieser Klassifizierungstyp erbt. Alle Klassifizierungstypen erben von "Text" ggf., und ein Klassifizierungstyp in mehrere andere Klassifizierungstypen.  
  
  Da die <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> Klasse versiegelt ist, können Sie es mit keinen Typparameter exportieren.  
  
  Das folgende Beispiel zeigt ExportAttribute auf eine Typdefinition für die Klassifizierung an.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 Die <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> ermöglicht den Zugriff auf die standard-Klassifizierungen. Integrierte Typen gehören:  
  
- „Text“  
  
- "Natural Language" (abgeleitet von "Text")  
  
- "formalen Sprache" (abgeleitet von "Text")  
  
- "String" (abgeleitet von "Literal")  
  
- 'Character' (abgeleitet von "Literal")  
  
- "numerische" (abgeleitet von "Literal")  
  
  Eine Anzahl verschiedener Fehlerarten erben <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Dazu gehören die folgenden Fehlertypen:  
  
- "Syntaxfehler"  
  
- "Compiler Error"  
  
- "andere Fehler"  
  
- "Warnung"  
  
  Um die Liste der verfügbaren Klassifizierungstypen zu ermitteln, importieren die <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, der die Auflistung der Klassifizierungstypen für den Editor verwaltet. Der folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Sie können eine Klassifizierung Formatdefinition für Ihre neue Klassifizierungstyp definieren. Leiten Sie eine Klasse von <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> und exportieren Sie es mit dem Typ <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>zusammen mit den folgenden Attributen:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Formats.  
  
- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: der Anzeigename des Formats.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Gibt an, ob das Format wird angezeigt, auf die **Schriftarten und Farben** auf der Seite die **Optionen** Dialogfeld.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Priorität des Formats. Gültige Werte reichen von <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: Geben Sie der Namen der Klassifizierung, dem dieses Format zugeordnet wird.  
  
  Das folgende Beispiel zeigt ExportAttribute, auf die Definition einer Klassifizierung-Format.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Um die Liste der verfügbaren Formate zu ermitteln, importieren die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, der die Auflistung der Formate für den Editor verwaltet. Der folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Erweitern von Rändern und Bildlaufleisten  
 Sind die Hauptansicht-Elemente des Editors neben der Textansicht an sich selbst, Rändern und Bildlaufleisten. Sie können eine beliebige Anzahl von Rändern zusätzlich zu den standardmäßigen Ränder angeben, die rund um die Textansicht angezeigt werden.  
  
 Implementieren einer <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> Schnittstelle, um einen Rand zu definieren. Sie müssen auch implementieren, die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Schnittstelle, um den Rand zu erstellen.  
  
 Um den Margin-Anbieter in einem Editor zu registrieren, müssen Sie den Anbieter zusammen mit den folgenden Attributen exportieren:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Rands.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in dem der Rand angezeigt, relativ zu den anderen Rändern wird.  
  
   Dies sind die integrierten Ränder:  
  
  - "Wpf Horizontal Scrollbar"  
  
  - "Wpf vertikale Bildlaufleiste"  
  
  - "WPF-Rand mit Zeilennummern"  
  
    Horizontale Ränder, die ein Order-Attribut des `After="Wpf Horizontal Scrollbar"` werden angezeigt, unter dem integrierten Rand und horizontal Ränder, die ein Order-Attribut des `Before ="Wpf Horizontal Scrollbar"` , die über den integrierten Rand angezeigt werden. Vertikale Ränder, die ein Order-Attribut des rechten `After="Wpf Vertical Scrollbar"` werden rechts neben die Bildlaufleiste angezeigt. Vertikale Ränder, die ein Order-Attribut des Links `After="Wpf Line Number Margin"` links neben der Rand mit Zeilennummern angezeigt werden, (wenn es sichtbar ist).  
  
- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: die Art des Rands (links, rechts, oben oder unten).  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die Ihre Rand gültig ist.  
  
  Das folgende Beispiel zeigt die ExportAttribute eine Margin-Anbieter für einen Rand, der rechts neben der Rand mit Zeilennummern angezeigt wird.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Erweitern von Tags  
 Tags sind eine Möglichkeit, Zuordnen von Daten mit verschiedenen Arten von Text. In vielen Fällen die zugehörigen Daten werden als eines visuellen Effekts angezeigt, aber nicht alle Tags sind eine visuelle Darstellung. Sie können Ihre eigene Art von Tags definieren, durch die Implementierung <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Sie müssen auch implementieren, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> , die Tags für eine bestimmte Anzahl von Textspannen, bereitzustellen und eine <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> den Tagger bereitstellen. Sie müssen den Tagger Anbieter zusammen mit den folgenden Attributen exportieren:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die Ihr Tag gültig ist.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art des Tags.  
  
  Das folgende Beispiel zeigt die ExportAttribute für einen Tagger-Anbieter.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TagType(typeof(TestTag))]  
internal class TestTaggerProvider : ITaggerProvider  
```  
  
 Die folgenden Arten von Tags sind integriert:  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: zugeordnete ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: Error-Typen zugeordnet.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: ein Zusatzelement zugeordnet.  
  
  > [!NOTE]
  >  Ein Beispiel für eine <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, finden Sie unter der Definition HighlightWordTag in [Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md).  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: zugeordneten Regionen, die erweitert oder reduziert werden, in der Gliederung werden können.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definiert den Speicherplatz ein Zusatzelement befindet sich in einer Textansicht. Weitere Informationen zu Zusatzelemente mit Platzausgleich finden Sie im folgenden Abschnitt.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: bietet automatischen Abstand und größenanpassung für das Zusatzelement.  
  
  Zum Suchen und Verwenden von Tags für Puffer und Ansichten, importieren die <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> oder <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, die erhalten Sie eine <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> des angeforderten Typs. Der folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Tags und MarkerFormatDefinitions  
 Sie können die erweitern die <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Klasse, um die Darstellung eines Tags zu definieren. Sie müssen die Klasse exportieren (als eine <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) mit den folgenden Attributen:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name verwendet, um dieses Format zu verweisen.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Dies führt dazu, dass das Format, das in der Benutzeroberfläche angezeigt werden.  
  
  Im Konstruktor definieren Sie den Anzeigenamen und die Darstellung des Tags. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> definiert die Füllfarbe und <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definiert die Farbe des Rahmens. Die <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> der lokalisierbare Namen des in der Formatdefinition ist.  
  
  Im folgenden finden ein Beispiel für eine Formatdefinition:  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Verweisen auf den Namen, die, den Sie in das Name-Attribut der Klasse (nicht den Anzeigenamen) festlegen, zum Anwenden dieser Formatdefinition, die ein Tag.  
  
> [!NOTE]
>  Ein Beispiel für eine <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, finden Sie unter der HighlightWordFormatDefinition-Klasse in [Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Erweitern von Randsteuerelementen  
 Zusatzelemente definieren die visuelle Effekte, die hinzugefügt werden können entweder auf den Text, der in einer Textansicht angezeigt wird, oder zeigen Sie auf den Text selbst. Sie können Ihre eigenen Zusatzelement definieren, als jede Art von <xref:System.Windows.UIElement>.  
  
 Sie müssen in Ihrer Klasse Zusatzelement deklarieren eine <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Informationen zum Registrieren Ihrer Zusatzelementebene exportieren Sie es zusammen mit den folgenden Attributen:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Zusatzelements ab.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge des Zusatzelements in Bezug auf andere Ebenen des Zusatzelements ab. Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> vier Standardfolien definiert: Auswahl, Gliederung, Einfügemarke und Text.  
  
  Das folgende Beispiel zeigt die ExportAttribute auf eine Definition einer Ebene Zusatzelements ab.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Müssen Sie eine zweite Klasse, die implementiert erstellen <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> und behandelt die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Ereignis durch Instanziieren des Zusatzelements ab. Sie müssen diese Klasse zusammen mit den folgenden Attributen exportieren:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die das Zusatzelement gültig ist.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht, für den diesem Zusatzelement gültig ist. Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> hat den Satz von vordefinierten Textansichtsrollen. Z. B. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> wird hauptsächlich für Textansichten von Dateien. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> wird für Textansichten verwendet, dass ein Benutzer bearbeiten kann, oder navigieren Sie mithilfe einer Tastatur und Maus. Beispiele für <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Ansichten sind die Text-Editor-Ansicht und die **Ausgabe** Fenster.  
  
  Das folgende Beispiel zeigt die ExportAttribute für den Anbieter des Zusatzelements ab.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Ein Zusatzelement mit Platzausgleich ist ein, der belegt Speicherplatz auf der gleichen Ebene wie der Text. Um diese Art von Zusatzelement erstellen zu können, müssen Sie eine Tag-Klasse, die von erbt definieren <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, definiert die Menge des Speicherplatzes, der das Zusatzelement belegt.  
  
 Wie bei der alle Zusatzelemente, müssen Sie die Zusatzelement Layer-Definition exportieren.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Um das Zusatzelement mit Platzausgleich zu instanziieren, müssen Sie eine Klasse, die implementiert erstellen <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, zusätzlich zu der Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (wie bei anderen Arten von Zusatzelemente).  
  
 Um den Tagger-Anbieter zu registrieren, müssen Sie es zusammen mit den folgenden Attributen exportieren:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die Ihre Zusatzelement gültig ist.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht, für die dieses Tag oder Zusatzelement ist gültig. Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> hat den Satz von vordefinierten Textansichtsrollen. Z. B. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> wird hauptsächlich für Textansichten von Dateien. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> wird für Textansichten verwendet, dass ein Benutzer bearbeiten kann, oder navigieren Sie mithilfe einer Tastatur und Maus. Beispiele für <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Ansichten sind die Text-Editor-Ansicht und die **Ausgabe** Fenster.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art der Tag oder Zusatzelement, die Sie definiert haben. Sie müssen ein zweites hinzufügen <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> für <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
  Das folgende Beispiel zeigt die ExportAttribute für den Anbieter Tagger für Tags Zusatzelement mit Platzausgleich.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Erweitern Sie die Maus-Prozessoren  
 Sie können spezielle Behandlung für die Mauseingabe hinzufügen. Erstellen Sie eine Klasse, die von erbt <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> und überschreiben Sie die Mausereignisse für die Eingabe, die Sie behandeln möchten. Sie müssen auch implementieren <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> in eine zweite Klasse und exportieren Sie es zusammen mit den <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , die angibt, dass der Art des Inhalts (z. B. "Text" oder "code"), die für den Maushandler für Ihre gültig ist.  
  
 Das folgende Beispiel zeigt die ExportAttribute für einen Anbieter der Maus-Prozessor.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Erweitern Sie die Drop-Handler  
 Sie können das Verhalten des Drop-Handler für bestimmte Arten von Text anpassen, indem Sie eine Klasse erstellen, implementiert <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> und eine zweite Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> der Drop-Handlers erstellen. Sie müssen die Drop-Handlers zusammen mit den folgenden Attributen exportieren:  
  
- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: der Text-Format für den dieser Ablagehandler gültig ist. Die folgenden Formate werden in der Reihenfolge ihrer Priorität von der höchsten zur niedrigsten behandelt:  
  
  1.  Alle benutzerdefinierten format  
  
  2.  FileDrop  
  
  3.  EnhancedMetafile  
  
  4.  WaveAudio  
  
  5.  RIFF  
  
  6.  Dif  
  
  7.  Gebietsschema  
  
  8.  Palette  
  
  9. PenData  
  
  10. Serialisierbare  
  
  11. SymbolicLink  
  
  12. Xaml  
  
  13. XamlPackage  
  
  14. TIFF  
  
  15. Bitmap  
  
  16. DIB  
  
  17. MetafilePicture  
  
  18. CSV  
  
  19. System.String  
  
  20. HTML-Format  
  
  21. UnicodeText  
  
  22. OEMText  
  
  23. Text  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Drop-Handlers.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge der Drop-Handlers vor oder nach dem Standardhandler für die Drop. Der Drop-Standardhandler für Visual Studio heißt "DefaultFileDropHandler".  
  
  Das folgende Beispiel zeigt die ExportAttribute für einen Anbieter der Drop-Handler.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Erweitern Sie die Editor-Optionen  
 Sie können Optionen gültig ist nur in einen bestimmten Bereich, z. B. in einer Textansicht definieren. Der Editor stellt dieser Satz von vordefinierten Optionen:-Editor-Optionen, Optionen und Optionen für Windows Presentation Foundation (WPF). Diese Optionen finden Sie im <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, und <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Um eine neue Option hinzuzufügen, leiten Sie eine Klasse von einer der folgenden Option Definition Klassen:  
  
- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
  Das folgende Beispiel zeigt, wie Sie eine Optionsdefinition exportieren, die einen booleschen Wert aufweist.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Erweitern von IntelliSense  
 IntelliSense ist ein allgemeiner Begriff für eine Gruppe von Funktionen, die Informationen zu strukturiertem Text bereitstellen, und die Anweisungsvervollständigung für sie. Zu diesen Funktionen gehören die Anweisungsvervollständigung, Signaturhilfe, QuickInfos und Glühbirnen. Anweisungsvervollständigung hilft Benutzern, die ein Sprachenname-Schlüsselwort oder Member korrekt eingeben. Signaturhilfe zeigt die Signatur oder die Signaturen für die Methode, die der Benutzer nur eingegeben hat. QuickInfo zeigt eine vollständige Signatur für den Namen eines Typs oder Members an, wenn die Maus darauf zeigt. Glühbirne bieten zusätzliche Aktionen für bestimmte Bezeichner in bestimmten Kontexten, z. B. alle Vorkommen einer Variable umbenennen, nachdem ein Vorkommen umbenannt wurde.  
  
 Der Entwurf einer IntelliSense-Funktion ist ähnlich in allen Fällen:  
  
- Eine von IntelliSense *Broker* ist verantwortlich für den gesamten Prozess.  
  
- Eine von IntelliSense *Sitzung* die Abfolge der Ereignisse, die zwischen der auslösenden der Presenter und Commits oder Abbruch der Auswahl darstellt. Die Sitzung wird in der Regel durch eine Benutzeraktion ausgelöst.  
  
- Eine von IntelliSense *Controller* ist verantwortlich für die Entscheidung, wenn die Sitzung beginnen und enden soll. Es legt außerdem fest, wenn die Informationen ein Commit ausgeführt werden soll, und wenn die Sitzung abgebrochen werden soll.  
  
- Eine von IntelliSense *Quelle* enthält die Inhalte und entscheidet, die beste Übereinstimmung.  
  
- Eine von IntelliSense *Presenter* dient zum Anzeigen des Inhalts.  
  
  In den meisten Fällen wird empfohlen, dass Sie mindestens eine Quelle und eines Controllers angeben. Sie können auch einen Presenter angeben, wenn Sie die Anzeige anpassen möchten.  
  
### <a name="implementing-an-intellisense-source"></a>Implementieren eine IntelliSense-Quelle  
 Wenn eine Quelle anpassen möchten, müssen Sie (mindestens) der folgenden Quellschnittstellen implementieren:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> ist veraltet zugunsten des <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Darüber hinaus müssen Sie einen Anbieter der gleichen Art implementieren:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> ist veraltet zugunsten des <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Sie müssen den Anbieter zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name der Quelle.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die auf die die Quelle angewendet wird.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der die Quelle angezeigt (in Bezug auf andere Quellen werden soll).  
  
-   Das folgende Beispiel zeigt ExportAttribute auf einen Vervollständigungsanbieter für die Datenquelle an.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Weitere Informationen zum Implementieren von IntelliSense-Datenquellen finden Sie in den folgenden exemplarischen Vorgehensweisen:  
  
 [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen der Signaturhilfe](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Implementieren einen IntelliSense-Controller  
 Wenn einen Controller anpassen möchten, müssen Sie implementieren die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> Schnittstelle. Darüber hinaus müssen Sie einen Controller-Anbieter zusammen mit den folgenden Attributen implementieren:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Controllers.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die der Controller gilt.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der der Controller (in Bezug auf andere Controller) angezeigt werden soll.  
  
  Das folgende Beispiel zeigt die ExportAttribute auf einen Vervollständigungsanbieter für den Controller.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Weitere Informationen zur Verwendung von IntelliSense-Controller finden Sie in den folgenden exemplarischen Vorgehensweisen:  
  
 [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
