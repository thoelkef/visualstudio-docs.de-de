---
title: Sprachdienst und Erweiterungspunkten-Editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7e62f1f3cac8f279dedbc79f283b908119d66ff2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="language-service-and-editor-extension-points"></a>Sprachdienst und Erweiterungspunkten-Editor
Der Editor stellt Erweiterungspunkte, die Sie als Managed Extensibility Framework (MEF) Komponenten, z. B. die meisten Language Service-Funktionen erweitern können. Dies sind die haupterweiterung Punkt Kategorien:  
  
-   Inhaltstypen  
  
-   Klassifizierungstypen und Klassifizierung Formate  
  
-   Ränder und Bildlaufleisten  
  
-   Tags  
  
-   Zusatzelemente  
  
-   Maus-Prozessoren  
  
-   Drop-Handler  
  
-   Optionen  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>Erweitern von Inhaltstypen  
 Inhaltstypen sind die Definitionen der Arten von behandelten vom Editor, z. B. Text, "Text", "Code" oder "CSharp". Sie definieren einen neuen Inhaltstyp durch Deklarieren einer Variablen des Typs <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> und dem neuen Inhaltstyp einen eindeutigen Namen. Um den Inhaltstyp mithilfe des Editors zu registrieren, exportieren Sie es zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>ist der Name des Inhaltstyps.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>ist der Name mit dem Inhaltstyp, der von dem dieser Inhaltstyp abgeleitet ist. Ein Inhaltstyp möglicherweise von mehreren anderen Inhaltstypen erben.  
  
 Da die <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Klasse ist versiegelt, können Sie ihn exportieren, wobei keine Type-Parameter.  
  
 Das folgende Beispiel zeigt ExportAttribute auf einen Content-Type-Definition.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 Inhaltstypen können auf 0 (null) oder mehrere bereits vorhandene Inhaltstypen basieren. Dies sind die integrierten Typen:  
  
-   Eine: der grundlegenden Inhaltstyp. Übergeordnete Element aller anderen Inhaltstypen.  
  
-   Text: der Basistyp für nicht-Projektion Inhalt. Erbt von "Jeder".  
  
-   Nur-Text: für Text, ohne Code. Erbt von "Text".  
  
-   Code: für alle Arten von Code. Erbt von "Text".  
  
-   Inertem: Schließt den Text aus jeder Art von Verarbeitung. Dieser Inhaltstyp Text haben also nie eine beliebige Erweiterung angewendet wird.  
  
-   Projektion: für den Inhalt der Projektionspuffer. Erbt von "Jeder".  
  
-   IntelliSense: für den Inhalt von IntelliSense. Erbt von "Text".  
  
-   Sighelp: Signaturhilfe. Erbt von "Intellisense".  
  
-   Sighelp-Doc: Signatur Hilfe-Dokumentation. Erbt von "Intellisense".  
  
 Dies sind einige der Inhaltstypen, die von Visual Studio definiert sind und einige Sprachen, die in Visual Studio gehostet werden:  
  
-   Standard  
  
-   C/C++  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 Importieren Sie die Liste der verfügbaren Inhaltstypen zu ermitteln, die <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, die die Auflistung von Inhaltstypen für den Editor verwaltet. Im folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Um eine Dateinamenerweiterung einen Inhaltstyp zuzuordnen, verwenden Sie <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  In Visual Studio Dateinamenerweiterungen registriert sind, mithilfe der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> auf ein Sprachpaket für den Dienst. Die <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ordnet einen MEF-Inhaltstyp eine Dateinamenerweiterung, die auf diese Weise registriert wurde.  
  
 Um die Dateinamenerweiterung der Content-Type-Definition exportieren, müssen Sie die folgenden Attribute enthalten:  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: Gibt die Dateierweiterung an.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Gibt den Inhaltstyp an.  
  
 Da die <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Klasse ist versiegelt, können Sie ihn exportieren, wobei keine Type-Parameter.  
  
 Das folgende Beispiel zeigt ExportAttribute auf eine Dateinamenerweiterung für die Definition einer Inhaltstyp an.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 Die <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> verwaltet die Zuordnungen zwischen Dateinamenerweiterungen und Inhaltstypen.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Erweitern von Klassifizierungstypen und Klassifizierung formatiert  
 Sie können die Klassifizierungstypen verwenden, um die Arten von Text zu definieren, für die Sie andere Behandlung (z. B. Farbgebung blauen Text "Schlüsselwort" und der Text "Kommentar" Grün) bereitstellen möchten. Definieren Sie einen neue Klassifizierungstyp durch Deklarieren einer Variablen vom Typ <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> und ihm einen eindeutigen Namen.  
  
 Um den Klassifizierungstyp in einem Editor zu registrieren, exportieren Sie es zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Klassifizierungstyps.  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: der Name des den Klassifizierungstyp, dieses Klassifizierungstyp erbt. Alle Klassifizierungstypen Vererben "Text" und ein Klassifizierungstyp kann von mehreren anderen Klassifizierungstypen erben.  
  
 Da die <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> Klasse ist versiegelt, können Sie ihn exportieren, wobei keine Type-Parameter.  
  
 Das folgende Beispiel zeigt ExportAttribute auf eine Typdefinition Klassifizierung an.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 Die <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> ermöglicht den Zugriff auf die standard-Klassifikationen. Integrierte Klassifizierungstypen umfassen diese:  
  
-   „Text“  
  
-   "natürlicher Sprache" (ableitet, "Text")  
  
-   "formale Language" (ableitet, "Text")  
  
-   "String" (abgeleitet von "Literal")  
  
-   "Character" (abgeleitet von "Literal")  
  
-   "numerische" (abgeleitet von "Literal")  
  
 Eine Reihe von verschiedenen Fehlertypen Vererben <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Dazu zählen die folgenden Fehlertypen:  
  
-   "Syntaxfehler"  
  
-   "Compilerfehler."  
  
-   "andere Fehler"  
  
-   "Warnung"  
  
 Importieren Sie die Liste der verfügbaren Klassifizierungstypen zu ermitteln, die <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, die die Auflistung der Klassifizierungstypen für den Editor verwaltet. Im folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Sie können die Definition einer Klassifizierung Format für Ihre neue Klassifizierungstyp definieren. Leiten Sie eine Klasse von <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> und exportieren Sie es mit dem Typ <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Formats.  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: der Anzeigename des Formats.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Gibt an, ob das Format wird angezeigt, auf die **Schriftarten und Farben** auf der Seite der **Optionen** (Dialogfeld).  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Priorität des Formats. Gültige Werte reichen von <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: Geben Sie der Namen der Klassifizierung, dem folgenden Format zugeordnet wird.  
  
 Das folgende Beispiel zeigt ExportAttribute auf die Definition einer Klassifizierung-Format.  
  
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
  
## <a name="extending-margins-and-scrollbars"></a>Erweitern von Aktivierungs- und Bildlaufleisten  
 Ränder und Bildlaufleisten sind die Elemente Hauptansicht des Editors neben der Textansicht selbst. Sie können eine beliebige Anzahl von Ränder zusätzlich zu den standardmäßigen Ränder bereitstellen, die um Textansicht angezeigt werden.  
  
 Implementieren einer <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> Schnittstelle, um einen Rand definieren. Sie müssen auch implementieren die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Schnittstelle, um den Rand zu erstellen.  
  
 Um den Margin-Anbieter in einem Editor zu registrieren, müssen Sie den Anbieter zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Rands.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in dem der Rand, relativ zu den anderen Rändern angezeigt.  
  
     Dies sind die integrierten Ränder:  
  
    -   "Wpf-horizontale Bildlaufleiste"  
  
    -   "Wpf-vertikale Bildlaufleiste"  
  
    -   "WPF-Rand mit Zeilennummern"  
  
     Horizontale Ränder, die eine Order-des Attribut `After="Wpf Horizontal Scrollbar"` werden angezeigt, unter dem integrierten Rand und dem horizontalen Ränder, die eine Order-Attribut des `Before ="Wpf Horizontal Scrollbar"` , die über den integrierten Rand angezeigt werden. Mit der rechten Maustaste vertikale Ränder, die eine Order-des Attribut `After="Wpf Vertical Scrollbar"` werden rechts neben der Bildlaufleiste angezeigt. Vertikale Ränder, die eine Order-des Attribut Links `After="Wpf Line Number Margin"` links neben der Rand mit Zeilennummern angezeigt werden, (wenn es sichtbar ist).  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: die Art der Rand (links, rechts, oben oder unten).  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die der Rand gültig ist.  
  
 Das folgende Beispiel zeigt ExportAttribute ein Rand-Anbieter für einen Rand, der rechts neben der Rand mit Zeilennummern angezeigt wird.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Erweitern von Tags  
 Tags sind eine Möglichkeit zum Zuordnen von Daten mit verschiedenen Arten von Text. In vielen Fällen ist die zugehörigen Daten eines visuellen Effekts angezeigt, jedoch nicht alle Tags haben eine visuelle Darstellung. Sie können eigene Art des Tags definieren, durch die Implementierung <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Müssen Sie auch implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Tags für eine bestimmte Gruppe von unzusammenhängende, bereitstellen und ein <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> Taggers bereitstellen. Sie müssen den Anbieter des Taggers zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die Ihr Tag gültig ist.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art des Tags.  
  
 Das folgende Beispiel zeigt ExportAttribute für einen Tagger-Anbieter.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Die folgenden Arten von Tags sind integriert:  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: verknüpft sind mit einem <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: Fehler Objekttypen zugeordnet.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: ein Randsteuerelement zugeordnet.  
  
    > [!NOTE]
    >  Ein Beispiel für eine <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, finden Sie unter der Definition HighlightWordTag [Exemplarische Vorgehensweise: Hervorheben von Text](../extensibility/walkthrough-highlighting-text.md).  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: zugeordnete Bereiche, die erweitert oder im gegliederten reduziert werden können.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: den Speicherplatz eine Zusatzelement (adornment belegt) in einer Textansicht definiert. Weitere Informationen zum Aushandeln von Speicherplatz Zusatzelemente finden Sie im folgenden Abschnitt.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: stellt die automatische Anpassung der Abstände und größenanpassung für die Zusatzelement (adornment) bereit.  
  
 Importieren Sie zum Suchen und Verwenden von Tags für Buffers "und" Sichten, die <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> oder <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, die Ihnen dabei helfen eine <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> des angeforderten Typs. Im folgende Code wird dieser Dienst als Eigenschaft importiert.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>RFID-Transponder und MarkerFormatDefinitions  
 Sie können erweitern die <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Klasse, um die Darstellung eines Tags zu definieren. Sie müssen Ihre Klasse exportieren (als eine <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name verwendet, um dieses Format verweisen  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Dies führt dazu, dass das Format in der Benutzeroberfläche angezeigt werden.  
  
 Im Konstruktor definieren Sie den Anzeigenamen und die Darstellung des Tags. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A>definiert die Füllfarbe und <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definiert die Farbe des Rahmens. Die <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> die Formatdefinition lokalisierbare heißt.  
  
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
  
 Um ein Tag diese Formatdefinition zuzuweisen, verweisen Sie den Namen, den Sie in das Namensattribut der Klasse (nicht den Anzeigenamen) festlegen.  
  
> [!NOTE]
>  Ein Beispiel für eine <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, finden Sie unter der Klasse HighlightWordFormatDefinition in [Exemplarische Vorgehensweise: Hervorheben von Text](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Erweitern von Randsteuerelementen  
 Zusatzelemente visuelle Effekte, die können hinzugefügt werden, entweder auf den Text, der in einer Textansicht angezeigt wird, oder zeigen auf den Text selbst zu definieren. Sie können eigene Zusatzelement (adornment) definieren, als jede Art von <xref:System.Windows.UIElement>.  
  
 Sie müssen in Ihrer Klasse Randsteuerelement Deklarieren einer <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Zum Registrieren Ihrer Randsteuerelement Layer exportieren Sie es zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des der Zusatzelement (adornment).  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge der Randsteuerelement in Bezug auf andere Ebenen Zusatzelement (adornment). Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definiert vier Ebenen der Standardeinstellung: Auswahl, gliedern, Caretzeichen und Text.  
  
 Das folgende Beispiel zeigt ExportAttribute auf die Definition einer Zusatzelement (adornment) Ebene an.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Müssen Sie eine zweite-Klasse, die implementiert erstellen <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> und behandelt die <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Ereignis durch Instanziierung der Zusatzelement (adornment). Sie müssen diese Klasse zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die die Zusatzelement (adornment) gültig ist.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht, die für die diese Zusatzelement (adornment) gültig ist. Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> enthält den Satz von Rollen für vordefiniertem Text anzeigen. Beispielsweise <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> dient in erster Linie für Textansichten von Dateien. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>Text-Ansichten dient, dass ein Benutzer bearbeiten kann, oder navigieren Sie mithilfe von Maus und Tastatur. Beispiele für <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Ansichten sind die Editoransicht für Text und die **Ausgabe** Fenster.  
  
 Das folgende Beispiel zeigt ExportAttribute vom Randsteuerelement-Anbieter.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Ein Zusatzelement ist ein, die auf derselben Ebene wie der Text Speicherplatz belegt. Um diese Art von Zusatzelement (adornment) zu erstellen, müssen Sie definieren eine Tag-Klasse, die von erben <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, definiert den Umfang des Speicherplatzes der Randsteuerelement belegt.  
  
 Wie bei allen Zusatzelemente müssen Sie die Randsteuerelement Layer-Definition exportieren.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Um die Zusatzelement zu instanziieren, erstellen Sie eine Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, zusätzlich zu implementierenden Klasse <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (wie bei anderen Arten von Zusatzelemente).  
  
 Um den Tagger-Anbieter zu registrieren, müssen Sie es zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die Ihre Zusatzelement (adornment) gültig ist.  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht für das dieses Tag oder Zusatzelement (adornment) ist ungültig. Die Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> enthält den Satz von Rollen für vordefiniertem Text anzeigen. Beispielsweise <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> dient in erster Linie für Textansichten von Dateien. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive>Text-Ansichten dient, dass ein Benutzer bearbeiten kann, oder navigieren Sie mithilfe von Maus und Tastatur. Beispiele für <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Ansichten sind die Editoransicht für Text und die **Ausgabe** Fenster.  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art der Tag oder Zusatzelement (adornment), die Sie definiert haben. Sie müssen ein zweites hinzufügen <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> für <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
 Das folgende Beispiel zeigt ExportAttribute auf dem Tagger-Anbieter für ein Leerzeichen aushandeln Randsteuerelement-Tag.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Erweitern Sie die Maus Prozessoren  
 Sie können spezielle Behandlung für Mauseingaben hinzufügen. Erstellen Sie eine Klasse, die von erben <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> und überschreiben die Mausereignisse für die Eingabe, die Sie behandeln möchten. Müssen Sie auch implementieren <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> in einer zweiten Klasse und exportieren Sie sie zusammen mit der <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , die gibt der Art des Inhalts (z. B. "Text" oder "code"), die für die der Maushandler gültig ist.  
  
 Das folgende Beispiel zeigt ExportAttribute für einen Anbieter der Maus-Prozessor.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Erweitern Sie die Drop-Handler  
 Sie können das Verhalten des Drop-Handler für bestimmte Arten von Text anpassen, indem Sie eine Klasse erstellen, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> und eine zweite-Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> den Drophandler zu erstellen. Exportieren Sie die Drop-Handler zusammen mit den folgenden Attributen:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: der Text-Format für die diese Drop-Handler gültig ist. Die folgenden Formate werden in Reihenfolge ihrer Priorität von der höchsten zur niedrigsten behandelt:  
  
    1.  Jedes benutzerdefinierte format  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  RIFF  
  
    6.  DIF  
  
    7.  Gebietsschema  
  
    8.  Palette  
  
    9. PenData  
  
    10. Serializable  
  
    11. SymbolicLink  
  
    12. XAML  
  
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
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Drop-Handler.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge der Drop-Handler, vor oder nach der Drop-Standardhandler. Der Standardhandler für die Dropdownliste für Visual Studio heißt "DefaultFileDropHandler".  
  
 Das folgende Beispiel zeigt ExportAttribute für einen Anbieter der Drop-Handler.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Erweitern von Editoroptionen  
 Definieren Sie Optionen aus, um nur in einem bestimmten Bereich, z. B. in einer Textansicht gültig sein. Der Editor stellt dieser Satz von vordefinierten Optionen: Editoroptionen, Optionen und Optionen für Windows Presentation Foundation (WPF). Diese Optionen finden Sie in <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, und <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Um eine neue Option hinzuzufügen, leiten Sie eine Klasse aus einer dieser Option Definition Klassen:  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 Das folgende Beispiel zeigt, wie eine Optionsdefinition exportieren, die einen booleschen Wert aufweist.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>Erweitern von IntelliSense  
 IntelliSense ist ein allgemeiner Begriff für eine Gruppe von Funktionen, die Informationen zu strukturierter Textdateien bereitstellen, und Anweisungsvervollständigung dafür. Zu diesen Funktionen gehören Anweisungsvervollständigung, Signaturhilfe, QuickInfo und Glühbirnen. Anweisungsvervollständigung hilft Benutzern, die ordnungsgemäß Geben Sie ein Schlüsselwort oder Member Sprachenname. Signaturhilfe zeigt die Signatur oder die Signaturen für die Methode, die der Benutzer gerade eingegeben hat. QuickInfo zeigt eine vollständige Signatur für den Namen eines Typs oder Members, wenn der Mauszeiger darauf verbleibt. Glühbirne bieten zusätzliche Aktionen für bestimmte Bezeichner in bestimmten Kontexten, z. B. alle Vorkommen einer Variablen umbenennen, nachdem ein Vorkommen umbenannt wurde.  
  
 Der Entwurf einer IntelliSense-Funktion ist in allen Fällen:  
  
-   Eine von IntelliSense *Broker* für den gesamten Prozess verantwortlich ist.  
  
-   Eine von IntelliSense *Sitzung* die Abfolge der Ereignisse zwischen der auslösenden Referenten und den Aktionsstatus oder Abbruch der Auswahl darstellt. Die Sitzung wird in der Regel durch eine Benutzeraktion ausgelöst.  
  
-   Eine von IntelliSense *Controller* ist verantwortlich für die Entscheidung, wenn die Sitzung starten und enden soll. Es legt außerdem fest, wenn die Informationen ein Commit ausgeführt werden soll, und wenn die Sitzung abgebrochen werden soll.  
  
-   Eine von IntelliSense *Quelle* enthält die Inhalte und entscheidet, die am besten übereinstimmt.  
  
-   Eine von IntelliSense *Vortragende* dient zum Anzeigen des Inhalts.  
  
 In den meisten Fällen empfiehlt es sich, dass Sie über mindestens einen Quell- und einen Domänencontroller bereitstellen. Wenn Sie die Anzeige anpassen möchten, können Sie auch eine Vortragende bereitstellen.  
  
### <a name="implementing-an-intellisense-source"></a>Implementieren eine IntelliSense-Quelle  
 Um eine Quelle anzupassen, müssen Sie (mindestens) von der folgenden Schnittstellen implementieren:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource>wurde als veraltet klassifiziert zugunsten des <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Darüber hinaus müssen Sie einen Anbieter der gleichen Art implementieren:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider>wurde als veraltet klassifiziert zugunsten des <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Sie müssen den Anbieter zusammen mit den folgenden Attributen exportieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name der Quelle.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die die Quelle gilt.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der die Quelle (in Bezug auf andere Quellen) angezeigt werden soll.  
  
-   Das folgende Beispiel zeigt ExportAttribute auf einen Abschluss Quellenanbieter.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 Weitere Informationen zu IntelliSense Quellen implementieren finden Sie unter den folgenden exemplarischen Vorgehensweisen:  
  
 [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen der Signaturhilfe](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Implementieren eine IntelliSense-Controller  
 Um einen Controller anzupassen, müssen Sie implementieren die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> Schnittstelle. Darüber hinaus müssen Sie einen Controller-Anbieter zusammen mit den folgenden Attributen implementieren:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Controllers.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. B. "Text" oder "code"), die für die der Controller gilt.  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der der Controller (in Bezug auf andere Domänencontroller) angezeigt werden soll.  
  
 Das folgende Beispiel zeigt ExportAttribute auf einen Abschluss Controller-Anbieter.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 Weitere Informationen zum Verwenden von IntelliSense-Controller finden Sie unter den folgenden exemplarischen Vorgehensweisen:  
  
 [Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)