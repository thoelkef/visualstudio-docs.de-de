---
title: "Language Service und Erweiterungspunkte-Editor | Microsoft Docs"
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
  - "Editoren [Visual Studio SDK] neue - Erweiterungspunkte"
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
---
# Language Service und Erweiterungspunkte-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Editor stellt Erweiterungspunkte, mit denen Sie als Managed Extensibility Framework \(MEF\)\-Komponenten, z. B. die meisten Language Service\-Funktionen erweitern können. Dies sind die wichtigsten Erweiterung Punkt Kategorien:  
  
-   Inhaltstypen  
  
-   Klassifizierungstypen und Klassifizierung Formate  
  
-   Ränder und Bildlaufleisten  
  
-   Tags  
  
-   Details  
  
-   Maus\-Prozessoren  
  
-   Drop\-Handler  
  
-   Optionen  
  
-   IntelliSense  
  
## Erweitern von Inhaltstypen  
 Inhaltstypen sind die Definitionen der Arten von behandelten vom Editor, z. B. Text, "Text", "Code" oder "CSharp". Sie definieren einen neuen Inhaltstyp durch Deklarieren einer Variablen des Typs <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> und dem neuen Inhaltstyp einen eindeutigen Namen. Um den Inhaltstyp mit dem Editor zu registrieren, exportieren Sie sie zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> ist der Name des Inhaltstyps.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> ist der Name des Inhaltstyps von dem dieser Inhaltstyp abgeleitet ist. Ein Inhaltstyp kann mehrere andere Inhaltstypen erben.  
  
 Da die <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Klasse versiegelt ist, können Sie ihn mit keine Typparameter exportieren.  
  
 Das folgende Beispiel zeigt ExportAttribute auf einen Content\-Type\-Definition.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Inhaltstypen können auf 0 \(null\) oder mehreren bereits vorhandenen Inhaltstypen basieren. Dies sind die integrierten Typen:  
  
-   Eine: der grundlegenden Inhaltstyp. Übergeordnete Element aller anderen Inhaltstypen.  
  
-   Text: der Basistyp für nicht\-Projektion Inhalt. Erbt von "any".  
  
-   Nur\-Text: für nicht codierte Text. Erbt von "Text".  
  
-   Code: für alle Arten von Code. Erbt von "Text".  
  
-   Inertem: Schließt den Text aus jeder Art von Verarbeitung. Text dieses Inhaltstyps müssen nie eine beliebige Erweiterung angewendet wird.  
  
-   Projektion: für den Inhalt der Projektionspuffer. Erbt von "any".  
  
-   IntelliSense: für den Inhalt von IntelliSense. Erbt von "Text".  
  
-   Sighelp: Signaturhilfe. Erbt von "Intellisense".  
  
-   Sighelp\-Doc: Signatur in der Hilfe zu. Erbt von "Intellisense".  
  
 Dies sind einige der Inhaltstypen, die von Visual Studio definiert werden und andere Sprachen, die in Visual Studio gehostet werden:  
  
-   Standard  
  
-   C\/C\+\+  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F\#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Importieren Sie die Liste der verfügbaren Inhaltstypen zu ermitteln, die <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, die verwaltet der Auflistung von Inhaltstypen für den Editor. Im folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Um die Erweiterung einen Inhaltstyp zuordnen möchten, verwenden Sie <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  In Visual Studio Dateinamenerweiterungen registriert sind, mithilfe der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> auf ein Sprachpaket für den Dienst. Der <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ordnet einen MEF\-Inhaltstyp Erweiterung, die auf diese Weise registriert wurde.  
  
 Um die Erweiterung der Content\-Type\-Definition exportieren möchten, müssen Sie die folgenden Attribute enthalten:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Gibt die Erweiterung an.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Gibt den Inhaltstyp an.  
  
 Da die <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Klasse versiegelt ist, können Sie ihn mit keine Typparameter exportieren.  
  
 Das folgende Beispiel zeigt ExportAttribute auf Erweiterung ein Content\-Type\-Definition.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 Die <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> verwaltet die Zuordnungen zwischen Dateinamenerweiterungen und Inhaltstypen.  
  
## Erweitern von Klassifizierungstypen und Klassifizierung Formate  
 Klassifizierungstypen können Sie um die Arten von Text zu definieren, für die Sie andere Behandlung \(z. B. lässt den Text "Schlüsselwort" Blau und den Text "Kommentar" Grün\) bereitstellen möchten. Definieren Sie einen neuen Klassifizierungstyp durch Deklarieren einer Variablen vom Typ <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> und ihm einen eindeutigen Namen.  
  
 Um den Klassifizierungstyp in einem Editor zu registrieren, exportieren Sie sie zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Klassifizierungstyps.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: der Name der den Klassifizierungstyp, von dem dieser Klassifizierungstyp erbt. Alle Klassifizierungstypen aus "Text", und ein Klassifizierungstyp erben von mehreren anderen Klassifizierung.  
  
 Da die <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> Klasse versiegelt ist, können Sie ihn mit keine Typparameter exportieren.  
  
 Das folgende Beispiel zeigt ExportAttribute auf eine Typdefinition Klassifizierung.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 Die <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> ermöglicht den Zugriff auf die standard\-Klassifikationen. Integrierte Klassifizierungstypen gehören:  
  
-   „Text“  
  
-   "natürlicher Sprache" \(abgeleitet von "Text"\)  
  
-   "formalen Language" \(abgeleitet von "Text"\)  
  
-   "String" \(abgeleitet von "Literal"\)  
  
-   'Character' \(abgeleitet von "Literal"\)  
  
-   "Numerisch" \(abgeleitet von "Literal"\)  
  
 Eine Reihe von verschiedenen Fehlerarten erben von <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Dazu gehören die folgenden Fehlertypen:  
  
-   "Syntaxfehler"  
  
-   "Compilerfehler"  
  
-   "andere Fehler"  
  
-   "Warnung"  
  
 Importieren Sie die Liste der verfügbaren Klassifizierung zu ermitteln, die <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, die die Auflistung der Klassifizierungstypen für den Editor verwaltet. Im folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Sie können eine Klassifizierung Formatdefinition für die neue Klassifizierungstyp definieren. Leiten Sie eine Klasse von <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> und exportieren Sie es mit dem Typ <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Formats.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: der Anzeigename des Formats.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Gibt an, ob das Format wird angezeigt, auf die **Schriftarten und Farben** auf der Seite der **Optionen** \(Dialogfeld\).  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Priorität des Formats. Gültige Werte reichen von <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: Geben Sie der Namen der Klassifizierung, dem dieses Format zugeordnet wird.  
  
 Das folgende Beispiel zeigt ExportAttribute auf die Definition einer Klassifizierung Format.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Importieren Sie die Liste der verfügbaren Formate zu ermitteln, die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, die die Auflistung der Formate für den Editor verwaltet. Im folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## Erweitern von Rändern und Bildlaufleisten  
 Ränder und Bildlaufleisten sind die Haupt\-View\-Elemente des Editors neben der Textansicht selbst. Sie können eine beliebige Anzahl von Rändern, zusätzlich zu den standardmäßigen Ränder bereitstellen, die um die Textansicht angezeigt werden.  
  
 Implementieren einer <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> Schnittstelle, um einen Rand zu definieren. Sie müssen auch implementieren, die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Schnittstelle, um den Rand zu erstellen.  
  
 Um die Margin\-Anbieter in einem Editor zu registrieren, müssen Sie den Anbieter zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Rands.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der der Rand angezeigt, relativ zu den anderen Rändern wird.  
  
     Dies sind die integrierten Ränder:  
  
    -   "Wpf horizontale Bildlaufleiste"  
  
    -   "Wpf vertikale Bildlaufleiste"  
  
    -   "Wpf Rand mit Zeilennummern"  
  
     Horizontale Ränder, die über ein Order\-Attribut des `After="Wpf Horizontal Scrollbar"` werden angezeigt, unter dem integrierten Rand und dem horizontalen Ränder, die über ein Order\-Attribut des `Before ="Wpf Horizontal Scrollbar"` über den integrierten Rand angezeigt werden. Mit der rechten Maustaste vertikale Ränder, die über ein Order\-Attribut des `After="Wpf Vertical Scrollbar"` werden rechts neben die Bildlaufleiste angezeigt. Vertikale Ränder, die über ein Order\-Attribut des Links `After="Wpf Line Number Margin"` links neben der Rand mit Zeilennummern angezeigt werden, \(wenn es sichtbar ist\).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: die Art des Rands \(links, rechts, oben oder unten\).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art der Inhalte \(z. B. "Text" oder "code"\), für die eine gültig ist.  
  
 Das folgende Beispiel zeigt ExportAttribute eine Margin\-Anbieter für einen Rand, der rechts neben der Rand mit Zeilennummern angezeigt wird.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## Erweitern von Tags  
 Tags sind eine Möglichkeit zum Zuordnen von Daten zu verschiedenen Arten von Text. In vielen Fällen die zugeordneten Daten als einen visuellen Effekt angezeigt, aber nicht alle Tags haben eine visuelle Darstellung. Sie können eigene Art des Tags definieren, durch die Implementierung <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Zudem muss implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Tags für eine bestimmte Gruppe von Textabschnitte, bereitstellen und ein <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> der Tagger bereitstellen. Sie müssen den Anbieter Tagger zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts \(z. B. "Text" oder "code"\), die für den das Tag gültig ist.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art des Tags.  
  
 Das folgende Beispiel zeigt ExportAttribute auf einem Tagger\-Anbieter.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Die folgenden Arten von Tag sind integriert:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: zugeordnete ein <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: Error\-Typen zugeordnet.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: ein Zusatzelement zugeordnet.  
  
    > [!NOTE]
    >  Ein Beispiel für eine <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, finden Sie unter der HighlightWordTag\-Definition in der [Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: Regionen, in denen können erweitert oder reduziert im gegliederten zugeordnet.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definiert den Bereich, der ein Zusatzelement belegt eine Textansicht. Weitere Informationen zum Speicherplatz\-Aushandlung Zusatzelemente finden Sie unter den folgenden Abschnitt.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: bietet automatische Abstand und Größe für das Zusatzelement.  
  
 Importieren Sie zum Suchen und Verwenden von Tags für Puffer und Ansichten, die <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> oder <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, die erhalten Sie ein <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> des angeforderten Typs. Im folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### Tags und MarkerFormatDefinitions  
 Sie können erweitern die <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Klasse, um die Darstellung eines Tags zu definieren. Sie müssen die Klasse exportieren \(wie ein <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>\) mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name, mit diesem Format verweisen  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Dies bewirkt, dass das Format, das in der Benutzeroberfläche angezeigt werden.  
  
 Im Konstruktor definieren Sie den Anzeigenamen und die Darstellung des Tags.<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> definiert die Füllfarbe und <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definiert die Farbe des Rahmens. Die <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> der lokalisierbare Namen der Formatdefinition ist.  
  
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
  
 Verweisen auf den Namen, den Sie in das Name\-Attribut der Klasse \(nicht den Anzeigenamen\) festlegen, zum Anwenden dieser Formatdefinition auf ein Tag.  
  
> [!NOTE]
>  Ein Beispiel für eine <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, finden Sie unter der HighlightWordFormatDefinition\-Klasse [Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md).  
  
## Erweitern von Details  
 Zusatzelemente visuelle Effekte, die können hinzugefügt werden, entweder auf den Text, der in einer Textansicht angezeigt wird, oder zeigen Sie auf den Text selbst zu definieren. Sie können Ihre eigenen Adornment definieren, wie jeder <xref:System.Windows.UIElement>.  
  
 Sie müssen in Ihrer Klasse Adornment Deklarieren einer <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Um Ihre Randsteuerelement\-Ebene zu registrieren, exportieren Sie sie zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des dem Zusatzelement.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge der Adornment in Bezug auf andere Adornment Ebenen. Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definiert vier Standardfolien: Auswahl, gliedern, Caretzeichen und Text.  
  
 Das folgende Beispiel zeigt ExportAttribute auf die Definition eines Randsteuerelement\-Ebene.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Müssen Sie eine zweite Klasse, die implementiert erstellen <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> und behandelt die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Ereignis durch das Zusatzelement instanziieren. Sie müssen diese Klasse zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art der Inhalte \(z. B. "Text" oder "code"\), für die das Zusatzelement gültig ist.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht, die für den diesem Zusatzelement gültig ist. Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> sind die Rollen von vordefinierten Text anzeigen. Z. B. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> dient in erster Linie für Textansichten von Dateien.<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Text\-Ansichten dient, dass ein Benutzer bearbeiten oder mithilfe von Maus und Tastatur navigieren kann. Beispiele für <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Ansichten sind die Ansicht für den Editor und die **Ausgabe** Fenster.  
  
 Das folgende Beispiel zeigt ExportAttribute vom Randsteuerelement\-Anbieter.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Ein Zusatzelement ist eine, die auf der gleichen Ebene wie der Text Speicherplatz belegen. Um diese Art von Adornment zu erstellen, müssen Sie definieren eine Tag\-Klasse, die von erbt <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, definiert das Zusatzelement belegt Speicherplatz.  
  
 Wie bei allen Zusatzelemente müssen Sie die Adornment Layer\-Definition exportieren.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Um die Zusatzelement zu instanziieren, erstellen Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, zusätzlich zu der Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> \(wie bei anderen Arten von Zusatzelemente\).  
  
 Um den Tagger\-Anbieter zu registrieren, müssen Sie es zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts \(z. B. "Text" oder "code"\), die für die Ihre Adornment gültig ist.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht für diesen Tag oder Adornment gültig ist. Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> sind die Rollen von vordefinierten Text anzeigen. Z. B. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> dient in erster Linie für Textansichten von Dateien.<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Text\-Ansichten dient, dass ein Benutzer bearbeiten oder mithilfe von Maus und Tastatur navigieren kann. Beispiele für <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Ansichten sind die Ansicht für den Editor und die **Ausgabe** Fenster.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art der Tag oder Adornment, die Sie definiert haben. Sie müssen ein zweites hinzufügen <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> für <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 Das folgende Beispiel zeigt ExportAttribute für den Anbieter Tagger Tag Adornment Speicherplatz aushandeln.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## Erweitern Sie die Maus\-Prozessoren  
 Sie können spezielle Behandlung von Mauseingaben hinzufügen. Erstellen Sie eine Klasse, die von erbt <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> und überschreiben die Mausereignisse für die Eingabe, die Sie behandeln möchten. Sie müssen auch implementieren <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> in einer zweiten Klasse und exportieren es zusammen mit der <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> angibt, dass die Art der Inhalte \(z. B. "Text" oder "code"\), für die die Maushandler gültig ist.  
  
 Das folgende Beispiel zeigt ExportAttribute auf einem Maus\-Prozessor\-Anbieter.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## Erweitern Sie die Drop\-Handler  
 Sie können das Verhalten des Drop\-Handler für bestimmte Arten von Text anpassen, indem Sie eine Klasse erstellen, implementiert <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> und eine zweite Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> der Drop\-Handler zu erstellen. Exportieren Sie die Drop\-Handler zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: das Text\-Format für die dieses Drop\-Handler gültig ist. Die folgenden Formate werden in der Reihenfolge ihrer Priorität vom höchsten zum niedrigsten Wert behandelt:  
  
    1.  Jedes benutzerdefinierte format  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  DIF  
  
    7.  Gebietsschema  
  
    8.  Palette  
  
    9. PenData  
  
    10. Serialisierbare  
  
    11. SymbolicLink  
  
    12. XAML  
  
    13. XamlPackage  
  
    14. TIFF  
  
    15. Bitmap  
  
    16. DIB  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. HTML\-Format  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Text  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Drop\-Handler.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge der Drop\-Handler vor oder nach der Standard\-Drop\-Handler. Der Standard\-Drop\-Handler für Visual Studio heißt "DefaultFileDropHandler".  
  
 Das folgende Beispiel zeigt ExportAttribute auf einem Drop\-Handler\-Anbieter.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## Erweitern Sie die Editor\-Optionen  
 Sie können Optionen gültig ist nur in einem bestimmten Bereich, z. B. in einer Textansicht definieren. Der Editor stellt dieser Satz von vordefinierten Optionen:\-Editor\-Optionen, Optionen und Optionen für Windows Presentation Foundation \(WPF\). Diese Optionen befinden sich im <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, und <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Um eine neue Option hinzufügen, leiten Sie eine Klasse von einer der Klassen diese Definition:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 Im folgenden Beispiel wird veranschaulicht, wie eine Optionsdefinition zu exportieren, die einen booleschen Wert verfügt.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## Erweitern von IntelliSense  
 IntelliSense ist ein allgemeiner Begriff für eine Gruppe von Funktionen, mit denen Informationen zu strukturierten Text und Anweisungsabschluss dafür. Zu diesen Funktionen gehören Anweisungsabschluss, Signaturhilfe, QuickInfo und Glühbirnen. Anweisungsabschluss hilft Benutzern, die ein Schlüsselwort oder einen Member Sprachenname richtig eingegeben. Signaturhilfe zeigt die Signatur oder die Signaturen für die Methode, die der Benutzer gerade eingegeben hat. QuickInfo zeigt eine vollständige Signatur für einen Typ oder Member, wenn die Maus darüber bewegt wird. Glühbirne bieten zusätzliche Aktionen für bestimmte Bezeichner in bestimmten Kontexten, z. B. alle Vorkommen einer Variablen umbenennen, nachdem ein Element umbenannt wurde.  
  
 Der Entwurf der IntelliSense\-Funktion ist ähnlich in allen Fällen:  
  
-   Eine IntelliSense *Broker* für den gesamten Prozess verantwortlich ist.  
  
-   Eine IntelliSense *Sitzung* die Abfolge der Ereignisse zwischen der auslösenden der Presenter und Aktionsstatus oder Abbruch der Auswahl darstellt. Die Sitzung wird in der Regel durch eine Benutzeraktion ausgelöst.  
  
-   Eine IntelliSense *Controller* ist verantwortlich für die Entscheidung, wann die Sitzung beginnen und enden soll. Sie entscheidet auch, wenn die Informationen übernommen werden soll, und wenn die Sitzung abgebrochen werden soll.  
  
-   Eine IntelliSense *Quelle* enthält den Inhalt und die beste Übereinstimmung entscheidet.  
  
-   Eine IntelliSense *Presenter* dient zum Anzeigen des Inhalts.  
  
 In den meisten Fällen wird empfohlen, dass Sie mindestens eine Quelle und einem Domänencontroller bereitstellen. Sie können auch einen Presenter angeben, wenn Sie die Anzeige anpassen möchten.  
  
### Implementieren eine IntelliSense\-Quelle  
 Um eine Quelle anzupassen, müssen Sie \(mindestens\) von der folgenden Schnittstellen implementieren:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> ist veraltet zugunsten des <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Darüber hinaus müssen Sie einen Anbieter dieser Art implementieren:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> ist veraltet zugunsten des <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Sie müssen den Anbieter zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name der Quelle.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts \(z. B. "Text" oder "code"\), die auf die Quelle angewendet wird.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der die Quelle \(in Bezug auf andere Quellen\) angezeigt werden soll.  
  
-   Das folgende Beispiel zeigt ExportAttribute auf einen Abschluss Quellenanbieter.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Weitere Informationen über das Implementieren von IntelliSense\-Datenquellen finden Sie unter den folgenden exemplarischen Vorgehensweisen:  
  
 [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Anweisungsabschluss](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### Implementieren eine IntelliSense\-Controller  
 Um einen Controller anzupassen, müssen Sie implementieren die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> Schnittstelle. Darüber hinaus müssen Sie einen Controller\-Anbieter zusammen mit den folgenden Attributen implementieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Controllers.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art der Inhalte \(z. B. "Text" oder "code"\) auf den Controller angewendet wird.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der der Controller \(in Bezug auf andere Domänencontroller\) angezeigt werden soll.  
  
 Das folgende Beispiel zeigt ExportAttribute auf einen Abschluss Controller\-Anbieter.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Weitere Informationen zum Verwenden von IntelliSense\-Controller finden Sie in den folgenden exemplarischen Vorgehensweisen:  
  
 [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)