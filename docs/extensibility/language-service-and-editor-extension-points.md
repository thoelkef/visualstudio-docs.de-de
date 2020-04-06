---
title: Sprachdienst- und Editorerweiterungspunkte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28bb086eb99e4b8128c04f62f9b370eb2eab8fa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703058"
---
# <a name="language-service-and-editor-extension-points"></a>Sprachdienst- und Editorerweiterungspunkte
Der Editor stellt Erweiterungspunkte bereit, die Sie als MEF-Komponenten (Managed Extensibility Framework) erweitern können, einschließlich der meisten Sprachdienstfunktionen. Dies sind die wichtigsten Erweiterungspunktkategorien:

- Inhaltstypen

- Klassifizierungstypen und Klassifizierungsformate

- Ränder und Bildlaufleisten

- `Tags`

- Verzierungen

- Mausprozessoren

- Drop-Handler

- Optionen

- IntelliSense

## <a name="extend-content-types"></a>Erweitern von Inhaltstypen
 Inhaltstypen sind die Definitionen der Vom Editor behandelten Texttypen, z. B. "text", "code" oder "CSharp". Sie definieren einen neuen Inhaltstyp, indem <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Sie eine Variable des Typs deklarieren und dem neuen Inhaltstyp einen eindeutigen Namen zuweisen. Um den Inhaltstyp im Editor zu registrieren, exportieren Sie ihn zusammen mit den folgenden Attributen:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>ist der Name des Inhaltstyps.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>ist der Name des Inhaltstyps, von dem dieser Inhaltstyp abgeleitet wird. Ein Inhaltstyp kann von mehreren anderen Inhaltstypen erben.

  Da <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> die Klasse versiegelt ist, können Sie sie ohne Typparameter exportieren.

  Das folgende Beispiel zeigt Exportattribute für eine Inhaltstypdefinition.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Inhaltstypen können auf null oder mehr bereits vorhandenen Inhaltstypen basieren. Dies sind die integrierten Typen:

- Beeinen: der grundlegende Inhaltstyp. Übergeordnetes Element aller anderen Inhaltstypen.

- Text: der grundlegende Typ für Nichtprojektionsinhalte. Erbt von "any".

- Klartext: für Nicht-Code-Text. Erbt von "Text".

- Code: für Code aller Art. Erbt von "Text".

- Inert: schließt den Text von jeder Art der Handhabung aus. Für Text dieses Inhaltstyps wird nie eine Erweiterung angewendet.

- Projektion: für den Inhalt von Projektionspuffern. Erbt von "any".

- Intellisense: für den Inhalt von IntelliSense. Erbt von "Text".

- Sighelp: Unterschrift Hilfe. Erbt von "intellisense".

- Sighelp-doc: Signaturhilfedokumentation. Erbt von "intellisense".

  Dies sind einige der Inhaltstypen, die von Visual Studio definiert werden, und einige der Sprachen, die in Visual Studio gehostet werden:

- Standard

- C/C++

- ConsoleOutput

- CSharp

- CSS

- Enc

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Um die Liste der verfügbaren Inhaltstypen zu ermitteln, importieren Sie die <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, die die Auflistung der Inhaltstypen für den Editor verwaltet. Der folgende Code importiert diesen Dienst als Eigenschaft.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Um einen Inhaltstyp einer Dateinamenerweiterung <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>zuzuordnen, verwenden Sie .

> [!NOTE]
> In Visual Studio werden Dateinamenerweiterungen <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> mithilfe des für ein Sprachdienstpaket registriert. Der <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ordnet einen MEF-Inhaltstyp einer Dateinamenerweiterung zu, die auf diese Weise registriert wurde.

 Um die Dateinamenerweiterung in die Inhaltstypdefinition zu exportieren, müssen Sie die folgenden Attribute einschließen:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Gibt die Dateinamenerweiterung an.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Gibt den Inhaltstyp an.

  Da <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> die Klasse versiegelt ist, können Sie sie ohne Typparameter exportieren.

  Das folgende Beispiel zeigt Exportattribute für eine Dateinamenerweiterung in eine Inhaltstypdefinition.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 Der <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> verwaltet die Zuordnungen zwischen Dateinamenerweiterungen und Inhaltstypen.

## <a name="extend-classification-types-and-classification-formats"></a>Erweitern von Klassifizierungstypen und Klassifizierungsformaten
 Sie können Klassifizierungstypen verwenden, um die Texttypen zu definieren, für die Sie eine unterschiedliche Verarbeitung bereitstellen möchten (z. B. Das Farbn der "Schlüsselwort"-Textblau und der "Kommentar"-Text grün). Definieren Sie einen neuen Klassifizierungstyp, <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> indem Sie eine Variable des Typs deklarieren und ihr einen eindeutigen Namen zuweisen.

 Um den Klassifizierungstyp beim Editor zu registrieren, exportieren Sie ihn zusammen mit den folgenden Attributen:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Klassifizierungstyps.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: der Name des Klassifizierungstyps, von dem dieser Klassifizierungstyp erbt. Alle Klassifizierungstypen erben von "Text", und ein Klassifizierungstyp kann von mehreren anderen Klassifizierungstypen erben.

  Da <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> die Klasse versiegelt ist, können Sie sie ohne Typparameter exportieren.

  Das folgende Beispiel zeigt Exportattribute für eine Klassifizierungstypdefinition.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 Der <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> bietet Zugriff auf Standardklassifizierungen. Zu den integrierten Klassifizierungstypen gehören:

- "text"

- "natürliche Sprache" (ableitet von "Text")

- "formale Sprache" (ableitet von "Text")

- "string" (leitet von "literal")

- "character" (leitet von "literal")

- "numerisch" (leitet von "literal" ab)

  Eine Gruppe verschiedener Fehlertypen <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>erben von . Sie enthalten die folgenden Fehlertypen:

- "Syntaxfehler"

- "Compilerfehler"

- "anderer Fehler"

- "Warnung"

  Um die Liste der verfügbaren Klassifizierungstypen zu ermitteln, importieren Sie die <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, die die Auflistung der Klassifizierungstypen für den Editor verwaltet. Der folgende Code importiert diesen Dienst als Eigenschaft.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Sie können eine Klassifizierungsformatdefinition für Ihren neuen Klassifizierungstyp definieren. Leiten Sie eine <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> Klasse von dem <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>Typ ab, und exportieren Sie sie mit dem Typ :

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Formats.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: den Anzeigenamen des Formats.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Gibt an, ob das Format auf der Seite **Schriftarten und Farben** des Dialogfelds **Optionen** angezeigt wird.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Priorität des Formats. Gültige Werte <xref:Microsoft.VisualStudio.Text.Classification.Priority>stammen von .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: der Name des Klassifizierungstyps, dem dieses Format zugeordnet ist.

  Das folgende Beispiel zeigt Exportattribute für eine Klassifizierungsformatdefinition.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Um die Liste der verfügbaren <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>Formate zu ermitteln, importieren Sie die , die die Sammlung von Formaten für den Editor verwaltet. Der folgende Code importiert diesen Dienst als Eigenschaft.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Erweitern von Rändern und Bildlaufleisten
 Ränder und Bildlaufleisten sind neben der Textansicht selbst die Hauptansichtselemente des Editors. Zusätzlich zu den Standardrändern, die in der Textansicht angezeigt werden, können Sie eine beliebige Anzahl von Rändern angeben.

 Implementieren <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> Sie eine Schnittstelle, um einen Rand zu definieren. Sie müssen auch <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> die Schnittstelle implementieren, um den Rand zu erstellen.

 Um den Margin-Anbieter beim Editor zu registrieren, müssen Sie den Anbieter zusammen mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Rands.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der die Marge erscheint, relativ zu den anderen Rändern.

   Dies sind die integrierten Ränder:

  - "Wpf Horizontal Escrollbar"

  - "Wpf Vertikale Scrollbar"

  - "Wpf-Liniennummernrand"

    Horizontale Ränder mit einem `After="Wpf Horizontal Scrollbar"` Orderattribut von werden unterhalb des integrierten Rands `Before ="Wpf Horizontal Scrollbar"` und horizontale Ränder mit einem Orderattribut von über dem integrierten Rand angezeigt. Rechts vertikale Ränder mit einem `After="Wpf Vertical Scrollbar"` Order-Attribut von werden rechts neben der Bildlaufleiste angezeigt. Linke vertikale Ränder mit einem `After="Wpf Line Number Margin"` Order-Attribut von erscheinen links vom Zeilennummernrand (falls sichtbar).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: die Art des Rands (links, rechts, oben oder unten).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "Code"), für den Ihre Marge gültig ist.

  Das folgende Beispiel zeigt Exportattribute auf einem Margin-Anbieter für eine Marge, die rechts neben der Zeilennummernmarge angezeigt wird.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Erweitern von Tags
 Tags sind eine Möglichkeit, Daten verschiedenen Textarten zuzuordnen. In vielen Fällen werden die zugehörigen Daten als visueller Effekt angezeigt, aber nicht alle Tags verfügen über eine visuelle Darstellung. Sie können Ihre eigene Art <xref:Microsoft.VisualStudio.Text.Tagging.ITag>von Tag definieren, indem Sie . Sie müssen <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> auch implementieren, um die Tags für einen <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> bestimmten Satz von Textspannen und eine bereitzustellen, um den Tagger bereitzustellen. Sie müssen den Tagger-Anbieter zusammen mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "Code"), für den Ihr Tag gültig ist.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art des Tags.

  Das folgende Beispiel zeigt Exportattribute für einen Tagger-Anbieter.

\<CodeContentPlaceHolder></CodeContentPlaceHolder> 8 Die folgenden Arten von Tags sind integriert:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: zugeordnet <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>mit einer .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: mit Fehlertypen verknüpft.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: mit einer Verzierung verknüpft.

  > [!NOTE]
  > Ein Beispiel für <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>ein finden Sie in der HighlightWordTag-Definition in [der exemplarischen Vorgehensweise: Hervorheben von Text](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: zugeordnet mit Regionen, die in der Gliederung erweitert oder zusammengeklappt werden können.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: Definiert den Raum, den eine Verzierung in einer Textansicht einnimmt. Weitere Informationen zu Raumverzierungen finden Sie im folgenden Abschnitt.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: bietet automatische Abstände und Größengrößen für die Verzierung.

  Um Tags für Puffer und Ansichten zu <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> suchen <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>und zu <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> verwenden, importieren Sie die oder die , die Ihnen einen vom angeforderten Typ geben. Der folgende Code importiert diesen Dienst als Eigenschaft.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tags und MarkerFormatDefinitionen
 Sie können <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> die Klasse erweitern, um die Darstellung eines Tags zu definieren. Sie müssen Ihre Klasse <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>(als )mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name, der verwendet wird, um auf dieses Format zu verweisen

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Dies bewirkt, dass das Format in der Benutzeroberfläche angezeigt wird

  Im Konstruktor definieren Sie den Anzeigenamen und die Darstellung des Tags. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>definiert die Füllfarbe <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> und definiert die Rahmenfarbe. Der <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> ist der lokalisierbare Name der Formatdefinition.

  Im Folgenden finden Sie ein Beispiel für eine Formatdefinition:

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

 Um diese Formatdefinition auf ein Tag anzuwenden, verweisen Sie auf den Namen, den Sie im Namensattribut der Klasse festgelegt haben (nicht den Anzeigenamen).

> [!NOTE]
> Ein Beispiel für <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>ein finden Sie in der HighlightWordFormatDefinition-Klasse in [der exemplarischen Vorgehensweise: Hervorheben von Text](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Erweitern von Verzierungen
 Verzierungen definieren visuelle Effekte, die entweder dem Text, der in einer Textansicht angezeigt wird, oder der Textansicht selbst hinzugefügt werden können. Sie können Ihre eigene Verzierung <xref:System.Windows.UIElement>als jede Art von definieren.

 In Ihrer Verzierungsklasse <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>müssen Sie eine deklarieren. Um Den Verzierungs-Layer zu registrieren, exportieren Sie ihn zusammen mit den folgenden Attributen:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name der Verzierung.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge der Verzierung in Bezug auf andere Verzierungsschichten. Die <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> Klasse definiert vier Standard-Layer: Auswahl, Gliederung, Caret und Text.

  Das folgende Beispiel zeigt Exportattribute für eine Adornment-Layer-Definition.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Sie müssen eine zweite Klasse <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> erstellen, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> die ihr Ereignis implementiert und verarbeitet, indem Sie die Verzierung instanziieren. Sie müssen diese Klasse zusammen mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "Code"), für den die Verzierung gültig ist.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht, für die diese Verzierung gültig ist. Die <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> Klasse verfügt über den Satz vordefinierter Textansichtsrollen. Beispielsweise <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> wird in erster Linie für Textansichten von Dateien verwendet. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>wird für Textansichten verwendet, die ein Benutzer mit einer Maus und einer Tastatur bearbeiten oder navigieren kann. Beispiele <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> für Ansichten sind die Editor-Textansicht und das **Ausgabefenster.**

  Das folgende Beispiel zeigt Exportattribute auf dem Verzierungsanbieter.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Eine Raum-Verhandeln-Verzierung ist eine, die Platz auf der gleichen Ebene wie der Text einnimmt. Um diese Art von Verzierung zu erstellen, müssen <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>Sie eine Tag-Klasse definieren, die von erbt, die den Raum definiert, den die Verzierung einnimmt.

 Wie bei allen Verzierungen müssen Sie die Definition des Verzierungs-Layers exportieren.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Um die Raumverzierung zu instanziieren, müssen Sie <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>eine Klasse erstellen, die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> zusätzlich zu der Klasse implementiert, die implementiert (wie bei anderen Arten von Verzierungen).

 Um den Tagger-Anbieter zu registrieren, müssen Sie ihn zusammen mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "Code"), für den Ihre Verzierung gültig ist.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht, für die dieses Tag oder diese Verzierung gültig ist. Die <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> Klasse verfügt über den Satz vordefinierter Textansichtsrollen. Beispielsweise <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> wird in erster Linie für Textansichten von Dateien verwendet. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>wird für Textansichten verwendet, die ein Benutzer mit einer Maus und einer Tastatur bearbeiten oder navigieren kann. Beispiele <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> für Ansichten sind die Editor-Textansicht und das **Ausgabefenster.**

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art des Tags oder der Verzierung, die Sie definiert haben. Sie müssen eine <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>Sekunde für hinzufügen.

  Das folgende Beispiel zeigt Exportattribute auf dem Tagger-Anbieter für ein Space-Negotiating-Adornment-Tag.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Erweitern von Mausprozessoren
 Sie können eine spezielle Handhabung für die Mauseingabe hinzufügen. Erstellen Sie eine Klasse, <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> die die Mausereignisse für die Eingabe, die Sie verarbeiten möchten, erbt und überschreibt diese. Sie müssen <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> auch in einer zweiten Klasse <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> implementieren und sie zusammen mit dem exportieren, der die Art des Inhalts (z. B. "Text" oder "Code") angibt, für den der Maushandler gültig ist.

 Das folgende Beispiel zeigt Exportattribute auf einem Mausprozessoranbieter.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Erweitern von Drop-Handlern
 Sie können das Verhalten von Drophandlern für bestimmte Texttypen <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> anpassen, indem Sie <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> eine Klasse erstellen, die implementiert, und eine zweite Klasse, die zum Erstellen des Drophandlers implementiert wird. Sie müssen den Drophandler zusammen mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: das Textformat, für das dieser Ablagehandler gültig ist. Die folgenden Formate werden in der Prioritätsreihenfolge von der höchsten bis zur niedrigsten Formate behandelt:

  1. Jedes benutzerdefinierte Format

  2. Filedrop

  3. EnhancedMetafile

  4. Waveaudio

  5. Riff

  6. Dif

  7. Gebietsschema

  8. Palette

  9. PenData

  10. Serialisierbar

  11. SymbolicLink

  12. Xaml

  13. XamlPackage

  14. TIFF

  15. Bitmap

  16. Dib

  17. MetafilePicture

  18. CSV

  19. System.String

  20. HTML-Format

  21. Unicodetext

  22. OEMText

  23. Text

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Drop-Handlers.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge des Drop-Handlers vor oder nach dem Standard-Drop-Handler. Der Standard-Drophandler für Visual Studio heißt "DefaultFileDropHandler".

  Das folgende Beispiel zeigt Exportattribute auf einem Drophandleranbieter.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Erweitern der Editoroptionen
 Sie können Optionen definieren, die nur in einem bestimmten Bereich gültig sind, z. B. in einer Textansicht. Der Editor stellt diesen Satz vordefinierter Optionen bereit: Editoroptionen, Ansichtsoptionen und Windows Presentation Foundation (WPF)-Ansichtsoptionen. Diese Optionen finden <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>Sie <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>unter <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>, und .

 Um eine neue Option hinzuzufügen, leiten Sie eine Klasse aus einer der folgenden Optionsdefinitionsklassen ab:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Das folgende Beispiel zeigt, wie eine Optionsdefinition mit einem booleschen Wert exportiert wird.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Erweitern von IntelliSense
 IntelliSense ist ein allgemeiner Begriff für eine Gruppe von Features, die Informationen über strukturierten Text und die Abschlusserklärung von Ausweisen für diesen Text bereitstellen. Zu diesen Funktionen gehören die Anweisungsvervollständigung, Signaturhilfe, Quick Info und Glühbirnen. Mit der Anweisungsvervollständigung können Benutzer ein Sprachschlüsselwort oder einen Membernamen richtig eingeben. Die Signaturhilfe zeigt die Signatur oder Signaturen für die Methode an, die der Benutzer gerade eingegeben hat. Quick Info zeigt eine vollständige Signatur für einen Typ oder Elementnamen an, wenn die Maus darauf ruht. Glühbirne bietet zusätzliche Aktionen für bestimmte Bezeichner in bestimmten Kontexten, z. B. das Umbenennen aller Vorkommen einer Variablen, nachdem ein Vorkommen umbenannt wurde.

 Das Design einer IntelliSense-Funktion ist in allen Fällen identisch:

- Ein *IntelliSense-Broker* ist für den gesamten Prozess verantwortlich.

- Eine IntelliSense-Sitzung stellt die Abfolge von Ereignissen zwischen dem Auslösen des Referenten und dem Committal oder Abbruch der Auswahl dar. *session* Die Sitzung wird in der Regel durch eine Benutzergeste ausgelöst.

- Ein IntelliSense-Controller ist für die Entscheidung verantwortlich, wann die Sitzung beginnen und enden soll. *controller* Er entscheidet auch, wann die Informationen gebunden werden sollen und wann die Sitzung abgebrochen werden soll.

- Eine IntelliSense-Quelle stellt den Inhalt bereit und entscheidet über die beste Übereinstimmung. *source*

- Ein *IntelliSense-Moderator* ist für die Anzeige des Inhalts verantwortlich.

  In den meisten Fällen wird empfohlen, mindestens eine Quelle und einen Controller bereitzustellen. Sie können auch einen Referenten bereitstellen, wenn Sie die Anzeige anpassen möchten.

### <a name="implement-an-intellisense-source"></a>Implementieren einer IntelliSense-Quelle
 Um eine Quelle anzupassen, müssen Sie eine (oder mehrere) der folgenden Quellschnittstellen implementieren:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>wurde zugunsten von <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>abgestellt.

 Darüber hinaus müssen Sie einen Anbieter der gleichen Art implementieren:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>wurde zugunsten von <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>abgestellt.

 Sie müssen den Anbieter zusammen mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name der Quelle.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "Code"), auf den die Quelle angewendet wird.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der die Quelle erscheinen soll (in Bezug auf andere Quellen).

- Das folgende Beispiel zeigt Exportattribute auf einem Abschlussquellenanbieter.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Weitere Informationen zum Implementieren von IntelliSense-Quellen finden Sie in den folgenden exemplarischen Vorgehensweisen:

- [Exemplarische Vorgehensweise: QuickInfo-Tooltips anzeigen](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Exemplarische Vorgehensweise: Signaturhilfe anzeigen](../extensibility/walkthrough-displaying-signature-help.md)

- [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementieren eines IntelliSense-Controllers
 Um einen Controller anzupassen, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> müssen Sie die Schnittstelle implementieren. Darüber hinaus müssen Sie einen Controlleranbieter zusammen mit den folgenden Attributen implementieren:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Controllers.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "Code"), auf den der für die Verarbeitung Verantwortliche angewendet wird.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der der Controller erscheinen soll (in Bezug auf andere Controller).

  Das folgende Beispiel zeigt Exportattribute auf einem Abschlusscontrolleranbieter.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Weitere Informationen zur Verwendung von IntelliSense-Controllern finden Sie in den folgenden exemplarischen Vorgehensweisen:

- [Exemplarische Vorgehensweise: QuickInfo-Tooltips anzeigen](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
