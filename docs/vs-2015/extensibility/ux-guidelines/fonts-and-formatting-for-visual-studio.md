---
title: Schriftarten und Formatierungen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ede8844b34473e1c900bd6af040cac99ceee1514
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301320"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Schriftarten und Formatierung für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>Die Umgebungsschriftart
 Alle Schriftarten in Visual Studio müssen für die Anpassung verfügbar gemacht werden. Dies geschieht in erster Linie über die Seite **Schriftarten und Farben** im Dialogfeld **Tools >-Optionen.** Die drei Hauptkategorien der Schriftarteinstellungen sind:

- **Umgebungsschriftart** – die primäre Schriftart für die IDE (integrierte Entwicklungsumgebung), die für alle Schnittstellenelemente verwendet wird, einschließlich Dialogfeldern, Menüs, Toolfenstern und Dokumentfenstern. Standardmäßig ist die Umgebungsschriftart an eine Systemschriftart gebunden, die in aktuellen Windows-Versionen als 9-Punkte-Segoe-Benutzeroberfläche angezeigt wird. Die Verwendung einer Schriftart für alle Schnittstellenelemente trägt dazu bei, eine konsistente Schriftartdarstellung in der gesamten IDE zu gewährleisten.

- **Texteditor** – Elemente, die in Code und anderen textbasierten Editoren auftauchen, können auf der Seite Texteditor in **Tools > Options**angepasst werden.

- **Bestimmte Sammlungen** – Designerfenster, die benutzerspezifische Anpassungen ihrer Schnittstellenelemente ermöglichen, können Schriftarten, die für ihre Entwurfsoberfläche spezifisch sind, auf ihrer eigenen Einstellungsseite in **Tools > Options**verfügbar machen.

### <a name="editor-font-customization-and-resizing"></a>Anpassung und Größenänderung der Editor-Schriftart
 Benutzer vergrößern oder zoomen oft die Größe und/oder Farbe des Textes im Editor nach ihren Wünschen, unabhängig von der allgemeinen Benutzeroberfläche. Da die Umgebungsschriftart für Elemente verwendet wird, die innerhalb oder als Teil eines Editors/Designers angezeigt werden können, ist es wichtig, das erwartete Verhalten zu beachten, wenn eine dieser Schriftartklassifizierungen geändert wird.

 Beim Erstellen von UI-Elementen, die im Editor angezeigt werden, aber nicht Teil des *Inhalts*sind, ist es wichtig, die Umgebungsschriftart und nicht die Textschriftart zu verwenden, damit die Größe der Elemente auf vorhersehbare Weise geändert wird.

1. Ändern Sie bei Codetext im Editor die Größe mit der Codetextschriftarteinstellung, und reagieren Sie auf die Zoomstufe des Editortexts.

2. Alle anderen Elemente der Schnittstelle sollten an die Umgebungsschriftart-Einstellung gebunden sein und auf globale Änderungen in der Umgebung reagieren. Dazu gehören (aber nicht beschränkt auf):

    - Text in Kontextmenüs

    - Text in einer Editor-Verzierung, z. B. Glühbirnenmenütext, Schnellfindungs-Editorbereich, und Navigieren zum Bereich

    - Beschriftung von Text in Dialogfeldern, z. B. Suchen in Dateien oder Refactor

### <a name="accessing-the-environment-font"></a>Zugriff auf die Umgebungsschriftart
 Im nativen oder WinForms-Code kann auf die Umgebungsschriftart zugegriffen werden, indem die Methode **IUIHostLocale::GetDialogFont** aufgerufen wird, nachdem die Schnittstelle vom SID_SUIHostLocale-Dienst abgefragt wurde.

 Leiten Sie für Windows Presentation Foundation (WPF) die Dialogfensterklasse von der **DialogWindow-Klasse** der Shell anstelle der **Windows-Klasse** von WPF ab.

 In XAML sieht der Code wie folgt aus:

```
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>

code behind:

internal partial class WebConfigModificationWindow : DialogWindow
{
}

```

 (Ersetzen `Microsoft.VisualStudio.Shell.11.0` Sie dies durch die aktuelle Version der MPF-DLL.)

 Um das Dialogfeld anzuzeigen, rufen Sie "**ShowModal()**" in der Klasse über **ShowDialog()** auf. **ShowModal()** legt den richtigen Modalzustand in der Shell fest, stellt sicher, dass das Dialogfeld im übergeordneten Fenster zentriert ist usw.

 Der Code lautet wie folgt:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** gibt einen Bool zurück? (nullable Boolean) mit dem **DialogResult**, das bei Bedarf verwendet werden kann. Der Rückgabewert ist true, wenn das Dialogfeld mit **OK**geschlossen wurde.

 Wenn Sie eine WPF-Benutzeroberfläche anzeigen müssen, die kein Dialogfeld ist und in einer eigenen **HwndSource**gehostet wird, z. B. in einem Popupfenster oder einem untergeordneten WPF-Fenster eines übergeordneten Win32/WinForms-Fensters, müssen Sie **FontFamily** und **FontSize** für das Stammelement des WPF-Elements festlegen. (Die Shell legt die Eigenschaften für das Hauptfenster fest, aber sie werden nicht an einem HWND vorbei vererbt). Die Shell stellt Ressourcen bereit, an die die Eigenschaften gebunden werden können, wie folgt:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Formatierungsreferenz (Skalierung/Fettung)
 In einigen Dialogfeldern muss ein bestimmter Text fett oder eine andere Größe als die Umgebungsschriftart sein. Zuvor wurden Schriftarten, die größer als die Umgebungsschriftart sind, als "Umgebungsschriftart +2" oder ähnlich codiert. Die Verwendung der bereitgestellten Codeausschnitte unterstützt Monitore mit hohem DPI und stellt sicher, dass Anzeigetext immer in der richtigen Größe und Gewichtung angezeigt wird (z. B. Light oder Semilight).

> **Hinweis: Stellen Sie vor dem Anwenden der Formatierung sicher, dass Sie die Anleitung im [Format Text](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)befolgen.**

 Um die Umgebungsschriftart zu skalieren, legen Sie den Stil des TextBlocks oder der Beschriftung wie angegeben fest. Jeder dieser Codeausschnitte, richtig verwendet, generiert die richtige Schriftart, einschließlich der entsprechenden Größen- und Gewichtsvariationen.

 Wobei "vsui" ein Verweis auf den Namespace Microsoft.VisualStudio.Shell ist:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>375% Umgebungsschriftart + Licht
 **Erscheint als:** 34 pt Segoe UI Light

 **Verwendung für:** (seltene) eindeutige Marken-Benutzeroberfläche, z. B. auf der Startseite

 **Verfahrenscode:** Wobei "textBlock" ein zuvor definierter TextBlock und "label" eine zuvor definierte Bezeichnung ist.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** Legen Sie den Stil des TextBlocks oder der Beschriftung wie dargestellt fest.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>310% Umgebungsschriftart + Licht
 **Erscheint als:** 28 pt Segoe UI Light

 **Verwendung für:** große Signaturdialogtitel, Hauptüberschrift in Berichten

 **Verfahrenscode:** Wobei "textBlock" ein zuvor definierter TextBlock und "label" eine zuvor definierte Bezeichnung ist.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** Legen Sie den Stil des TextBlocks oder der Beschriftung wie dargestellt fest.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>200% Umgebungsschrift + Semilight
 **Erscheint als:** 18 pt Segoe UI Semilight

 **Verwendung für:** Unterpositionen, Titel in kleinen und mittleren Dialogen

 **Verfahrenscode:** Wobei "textBlock" ein zuvor definierter TextBlock und "label" eine zuvor definierte Bezeichnung ist.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** Legen Sie den Stil des TextBlocks oder der Beschriftung wie dargestellt fest.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>155% Umgebungsschriftart
 **Erscheint als:** 14 pt Segoe UI

 **Verwendung für:** Abschnittsüberschriften in Dokument gut UI oder Berichte

 **Verfahrenscode:** Wobei "textBlock" ein zuvor definierter TextBlock und "label" eine zuvor definierte Bezeichnung ist.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** Legen Sie den Stil des TextBlocks oder der Beschriftung wie dargestellt fest.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>133% Umgebungsschriftart
 **Erscheint als:** 12 pt Segoe UI

 **Verwendung für:** kleinere Unterüberschriften in Signaturdialogen und Dokument gut UI

 **Verfahrenscode:** Wobei "textBlock" ein zuvor definierter TextBlock und "label" eine zuvor definierte Bezeichnung ist.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** Legen Sie den Stil des TextBlocks oder der Beschriftung wie dargestellt fest.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>122% Umgebungsschriftart
 **Erscheint als:** 11 pt Segoe UI

 **Verwendung für:** Abschnittsüberschriften in Signaturdialogfeldern, oberste Knoten in der Strukturansicht, vertikale Tab-Navigation

 **Verfahrenscode:** Wobei "textBlock" ein zuvor definierter TextBlock und "label" eine zuvor definierte Bezeichnung ist.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** Legen Sie den Stil des TextBlocks oder der Beschriftung wie dargestellt fest.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Umgebungsschriftart + fett
 **Erscheint als:** fett gedruckt 9 pt Segoe UI

 **Verwendung für:** Beschriftungen und Unterköpfe in Signaturdialogen, Berichten und Dokumenten gut UI

 **Verfahrenscode:** Wobei "textBlock" ein zuvor definierter TextBlock und "label" eine zuvor definierte Bezeichnung ist.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** Legen Sie den Stil des TextBlocks oder der Beschriftung wie dargestellt fest.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Lokalisierbare Stile
 In einigen Fällen müssen Lokalisierer Schriftarten für verschiedene Gebietsschemata ändern, z. B. das Entfernen von Fettschrift aus Text für ostasiatische Sprachen. Um die Lokalisierung von Schriftstilen zu ermöglichen, müssen sich diese Formatvorlagen in der .resx-Datei befinden. Die beste Möglichkeit, dies zu erreichen und immer noch Schriftarten im Visual Studio-Formular-Designer zu bearbeiten, besteht darin, die Schriftarten zur Entwurfszeit explizit festzulegen. Obwohl dadurch ein vollständiges Schriftartobjekt erstellt wird und die Vererbung übergeordneter Schriftarten zu unterbrechen scheint, wird nur die FontStyle-Eigenschaft zum Festlegen der Schriftart verwendet.

 Die Lösung besteht darin, das **FontChanged-Ereignis** des Dialogformulars zu verbinden. Gehen Sie im **FontChanged-Ereignis** alle Steuerelemente, und überprüfen Sie, ob ihre Schriftart festgelegt ist. Wenn diese Festgelegte ist, ändern Sie sie in eine neue Schriftart, die auf der Schriftart des Formulars und dem vorherigen Schriftstil des Steuerelements basiert. Ein Beispiel dafür im Code ist:

```
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 Die Verwendung dieses Codes stellt sicher, dass bei der Aktualisierung der Schriftart des Formulars auch die Schriftarten der Steuerelemente aktualisiert werden. Diese Methode sollte auch vom Konstruktor des Formulars aufgerufen werden, da das Dialogfeld möglicherweise keine Instanz von **IUIService** abfeuert und das **FontChanged-Ereignis** nie ausgelöst wird. Hooking **FontChanged** ermöglicht es Dialogen, die neue Schriftart dynamisch aufzunehmen, auch wenn das Dialogfeld bereits geöffnet ist.

### <a name="testing-the-environment-font"></a>Testen der Umgebungsschriftart
 Um sicherzustellen, dass Ihre Benutzeroberfläche die Umgebungsschriftart verwendet und die Größeneinstellungen beachtet, öffnen Sie **Tools > Optionen > Umgebung > Schriftarten und Farben** und wählen Sie "Umgebungsschriftart" unter dem Dropdownmenü "Einstellungen für:" aus.

 ![Seite Schriftarten und Farben im Dialogfeld "Tools &#62; Options"](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201-a_OptionsFonts")

 **Schriftarten und Farben einstellungen im Dialogfeld Tools > Optionen**

 Legen Sie die Schriftart auf etwas ganz anderes als die Standardeinstellung fest. Um deutlich zu machen, welche Benutzeroberfläche nicht aktualisiert wird, wählen Sie eine Schriftart mit Serifen (z. B. "Times New Roman") und legen Sie eine sehr große Größe fest. Testen Sie dann die Benutzeroberfläche, um sicherzustellen, dass sie die Umgebung respektiert. Hier ist ein Beispiel für das Lizenzdialogfeld:

 ![Beispiel eines Dialogfelds, das nicht die Umgebungsschriftart verwendet](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201-b_WrongFontDialog")

 **Beispiel für UI-Text, der die Umgebungsschriftart nicht respektiert**

 In diesem Fall werden "Benutzerinformationen" und "Produktinformationen" nicht in Derschrift behandelt. In einigen Fällen kann dies eine explizite Entwurfsauswahl sein, aber es kann ein Fehler sein, wenn die explizite Schriftart nicht als Teil der Redline-Spezifikationen angegeben ist.

 Um die Schriftart zurückzusetzen, klicken Sie unter **Werkzeuge > Optionen > Umgebung > Schriftarten und Farben**auf "Standardeinstellungen verwenden".

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Textstil
 Textstil bezieht sich auf Schriftgröße, Gewichtung und Groß-/Kleinschreibung. Implementierungsanleitung finden Sie unter [Die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Textgehäuse

#### <a name="all-caps"></a>Alle Kappen
 Verwenden Sie nicht alle Kappen für Titel oder Beschriftungen in Visual Studio.

#### <a name="all-lowercase"></a>Alle Kleinbuchstaben
 Verwenden Sie nicht alle Kleinbuchstaben für Titel oder Beschriftungen in Visual Studio.

#### <a name="sentence-and-title-case"></a>Satz- und Titelfall
 Text in Visual Studio sollte je nach Situation entweder Titelfall oder Satzfall verwenden.

|Verwenden Sie den Titelfall für:|Verwenden Sie den Satzfall für:|
|-------------------------|----------------------------|
|Dialogtitel|Bezeichnungen|
|Gruppenboxen|Kontrollkästchen|
|Menüelemente|Optionsfelder|
|Kontextmenüelemente|Listenfeldelemente|
|Schaltflächen|Statusleisten|
|Tabellenbeschriftungen||
|Spaltenüberschriften||
|QuickInfos||

##### <a name="title-case"></a>Großschreibung
 Title Case ist ein Stil, in dem die ersten Buchstaben der meisten oder aller Wörter innerhalb eines Ausdrucks groß geschrieben werden. In Visual Studio wird der Titelfall für viele Elemente verwendet, z. B.:

- **Quickinfos.** Beispiel: "Ausgewählte Elemente anzeigen"

- **Spaltenüberschriften.** Beispiel: "Systemantwort"

- **Menüelemente.** Beispiel: "Alle speichern"

  Bei Verwendung des Titelfalls sind dies die Richtlinien für das Großwerden von Wörtern und das Belassen in Kleinbuchstaben:

|Großbuchstaben|Kommentare und Beispiele|
|---------------|---------------------------|
|Alle Substantive||
|Alle Verben|Einschließlich "Is" und anderer Formen von "sein"|
|Alle Adverbien|Einschließlich "Than" und "When"|
|Alle Adjektive|Einschließlich "Dies" und "Das"|
|Alle Pronomen|Einschließlich des possessiven "Its" sowie "It's", einer Kontraktion des Pronopaares "it" und des Verbs "is"|
|Erste und letzte Worte, unabhängig von Sprachteilen||
|Präpositionen, die Teil einer Verbphrase sind|"Schließen aller Windows" oder "Herunterfahren des Systems"|
|Alle Buchstaben eines Akronyms|HTML, XML, URL, IDE, RGB|
|Das zweite Wort in einem zusammengesetzten Wort, wenn es sich um ein Nov oder ein richtiges Adjektiv handelt oder wenn die Wörter das gleiche Gewicht haben|Querverweis, Pre-Microsoft-Software, Lese-/Schreibzugriff, Laufzeit|

|Kleinbuchstaben|Beispiele|
|---------------|--------------|
|Das zweite Wort in einem zusammengesetzten Wort, wenn es sich um einen anderen Teil der Sprache oder ein Partizip handelt, das das erste Wort ändert|How-to, Take-off|
|Artikel, es sei denn, man ist das erste Wort im Titel|a, an, the|
|Koordinatenkonjunktionen|und, aber, für, noch, oder|
|Präpositionen mit Wörtern von vier oder weniger Buchstaben außerhalb eines Verbsatzes|in, wie für, aus, oben auf|
|"An" bei Verwendung in einer infinitiven Phrase|"Wie Sie Ihre Festplatte formatieren"|

##### <a name="sentence-case"></a>Urteil-Fall
 Satzfall ist die Standard-Großschreibungsmethode für das Schreiben, in der nur das erste Wort des Satzes groß geschrieben wird, zusammen mit allen richtigen Substantiven und dem Pronomen "Ich". Im Allgemeinen ist der Satzfall für ein weltweites Publikum leichter zu lesen, vor allem, wenn der Inhalt von einer Maschine übersetzt wird. Verwenden Sie den Satzfall für:

1. **Statusleistenmeldungen.** Diese sind einfach, kurz und enthalten nur Statusinformationen. Beispiel: "Projektdatei laden"

2. **Alle anderen UI-Elemente**, einschließlich Beschriftungen, Kontrollkästchen, Optionsfelder und Listenfeldelemente. Beispiel: "Alle Elemente in der Liste auswählen"

### <a name="text-formatting"></a>Textformatierung
 Die Standardtextformatierung in Visual Studio 2013 wird durch eine [Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)gesteuert. Dieser Dienst trägt dazu bei, ein konsistentes Schriftbild in der gesamten IDE (integrierte Entwicklungsumgebung) sicherzustellen, und Sie müssen ihn verwenden, um eine konsistente Benutzererfahrung zu gewährleisten.

 Die vom Visual Studio-Schriftartdienst verwendete Standardgröße stammt von Windows und wird als 9 pt angezeigt.

 Sie können die Formatierung auf die Umgebungsschriftart anwenden. In diesem Thema wird erläutert, wie und wo Stile verwendet werden. Informationen zur Implementierung finden Sie unter [Die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Fetter Text
 Fetttext wird sparsam in Visual Studio verwendet und sollte für Folgendes reserviert werden:

- Fragebeschriftungen in Assistenten

- Anzeigen des aktiven Projekts im Projektmappen-Explorer

- überschriebene Werte im Eigenschaften-Toolfenster

- Bestimmte Ereignisse in den Dropdownlisten des Visual Basic-Editors

- Servergenerierter Inhalt in der Dokumentgliederung für Webseiten

- Abschnittsheader in komplexen Dialog- oder Designer-UI

#### <a name="italics"></a>Kursiv
 Visual Studio verwendet weder kursiven noch fett formatierten kursiven Text.

#### <a name="color"></a>Color

- Blau ist für Hyperlinks (Navigation und Befehl) reserviert und sollte niemals zur Orientierung verwendet werden.

- Größere Überschriften (Umgebungsschriftart x 155% oder höher) können für folgende Zwecke eingefärbt werden:

  - So bieten Sie visuellen Reiz für die Visual Studio-Signatur-Benutzeroberfläche

  - Um die Aufmerksamkeit auf einen bestimmten Bereich zu lenken

  - Um eine Entlastung von der standardmäßigen Dunkelgrau/Schwarz-Umgebungstextfarbe zu bieten

- Farbe in Überschriften sollte vorhandene Visual Studio-Markenfarben nutzen, in erster Linie die wichtigsten violetten, #FF68217A.

- Wenn Sie Farbe in Überschriften verwenden, müssen Sie die [Windows-Farbrichtlinien](https://msdn.microsoft.com/library/dn742482.aspx)einhalten, einschließlich kontrastreicher und anderer Überlegungen zur Barrierefreiheit.

### <a name="font-size"></a>Schriftgrad
 Das Visual Studio-UI-Design bietet ein helleres Erscheinungsbild mit mehr Leerraum. Nach Möglichkeit wurden Chrom- und Titelleisten reduziert oder entfernt. Während die Informationsdichte in Visual Studio eine Anforderung ist, ist die Typografie nach wie vor wichtig, wobei der Schwerpunkt auf offeneren Zeilenabständen und einer Variation der Schriftgrößen und -gewichte liegt.

 Die folgenden Tabellen enthalten Entwurfsdetails und visuelle Beispiele für die in Visual Studio verwendeten Anzeigeschriftarten. Einige Anzeigeschriftvariationen haben sowohl die Größe als auch die Gewichtung, z. B. Semilight oder Light, die in ihr Erscheinungsbild codiert sind.

 Implementierungscodeausschnitte für alle Anzeigeschriftarten finden Sie in [der Referenz Formatierung (Skalierung/Fetterstellung).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)

#### <a name="375-environment-font--light"></a>375% Umgebungsschriftart + Licht

|||
|-|-|
|**Verwendung:** Selten. Nur eindeutige Marken-UI.<br /><br /> **tun:**<br /><br /> - Verwenden Sie satzfall<br />- Verwenden Sie immer geringes Gewicht<br /><br /> **Vermeiden Sie Folgendes:**<br /><br /> - Verwendung für andere Benutzeroberfläche als Signatur-UI wie Startseite<br />- Fett, kursiv oder fett kursiv<br />- Verwendung für Textkörper<br />- Verwendung in Werkzeugfenstern|**Erscheint als:** 34 pt Segoe UI Light<br /><br /> **Visuelles Beispiel:**<br /><br /> *Derzeit nicht verwendet. Kann auf der Startseite verwendet werden.*|

#### <a name="310-environment-font--light"></a>310% Umgebungsschriftart + Licht

|||
|-|-|
|**Syntax:**<br /><br /> - Größere Überschrift in Signaturdialogen<br />- Hauptberichtsüberschrift<br /><br /> **tun:**<br /><br /> - Verwenden Sie satzfall<br />- Verwenden Sie immer geringes Gewicht<br /><br /> **Vermeiden Sie Folgendes:**<br /><br /> - Verwendung für andere Benutzeroberfläche als Signatur-UI wie Startseite<br />- Fett, kursiv oder fett kursiv<br />- Verwendung für Textkörper<br />- Verwendung in Werkzeugfenstern|**Erscheint als:** 28 pt Segoe UI Light<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für 310 % Umgebungsschrift art &#43; Light-Überschrift](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202-a_EF310")|

#### <a name="200-environment-font--semilight"></a>200% Umgebungsschrift + Semilight

|||
|-|-|
|**Syntax:**<br /><br /> - Unterpositionen<br />- Titel in kleinen und mittleren Dialogen<br /><br /> **tun:**<br /><br /> - Verwenden Sie satzfall<br />- Verwenden Sie immer Semilight-Gewicht<br /><br /> **Vermeiden Sie Folgendes:**<br /><br /> - Fett, kursiv oder fett kursiv<br />- Verwendung für Textkörper<br />- Verwendung in Werkzeugfenstern|**Erscheint als:** 18 pt Segoe UI Semillight<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für 200% Umgebungsschrift art &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% Umgebungsschriftart

|||
|-|-|
|**Syntax:**<br /><br /> - Abschnittsüberschriften in Dokument gut UI<br />- Berichte<br /><br /> **Tun Sie:** Verwenden des Satzfalls<br /><br /> **Vermeiden Sie Folgendes:**<br /><br /> - Fett, kursiv oder fett kursiv<br />- Verwendung für Textkörper<br />- Verwendung in Standard Visual Studio-Steuerelementen<br />- Verwendung in Werkzeugfenstern|**Erscheint als:** 14 pt Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 155 %, Überschrift](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% Umgebungsschriftart

|||
|-|-|
|**Syntax:**<br /><br /> - Kleinere Unterpositionen in Signaturdialogen<br />- Kleinere Unterpositionen in Dokument gut UI<br /><br /> **Tun Sie:** Verwenden des Satzfalls<br /><br /> **Vermeiden Sie Folgendes:**<br /><br /> - Fett, kursiv oder fett kursiv<br />- Verwendung für Textkörper<br />- Verwendung in Standard Visual Studio-Steuerelementen<br />- Verwendung in Werkzeugfenstern|**Erscheint als:** 12 pt Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Beispiel für Umgebungsschriftart mit 133 %, Überschrift](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% Umgebungsschriftart

|||
|-|-|
|**Syntax:**<br /><br /> - Abschnittsüberschriften in Signaturdialogen<br />- Top-Knoten in der Baumansicht<br />- Vertikale Tab-Navigation<br /><br /> **Tun Sie:** Verwenden des Satzfalls<br /><br /> **Vermeiden Sie Folgendes:**<br /><br /> - Fett, kursiv oder fett kursiv<br />- Verwendung für Textkörper<br />- Verwendung in Standard Visual Studio-Steuerelementen<br />- Verwendung in Werkzeugfenstern|**Erscheint als:** 11 pt Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Beispiel für Umgebungsschriftart mit 122 %, Überschrift](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Umgebungsschriftart + fett

|||
|-|-|
|**Syntax:**<br /><br /> - Etiketten und Unterköpfe in Signaturdialogen<br />- Etiketten und Unterköpfe in Berichten<br />- Etiketten und Unterköpfe in Dokument gut UI<br /><br /> **tun:**<br /><br /> - Verwenden Sie satzfall<br />- Verwenden Sie fettes Gewicht<br /><br /> **Vermeiden Sie Folgendes:**<br /><br /> - Kursiv oder fett kursiv<br />- Verwendung für Textkörper<br />- Verwendung in Standard Visual Studio-Steuerelementen<br />- Verwendung in Werkzeugfenstern|**Erscheint als:** fett gedruckt 9 pt Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart &#43; Bold-Überschrift](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Umgebungsschriftart

|||
|-|-|
|**Verwendung:** Alle anderen Texte<br /><br /> **Tun Sie:** Verwenden des Satzfalls<br /><br /> **Nicht:** Kursiv oder fett kursiv|**Erscheint als:** 9 pt Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Polsterung und Abstand
 Überschriften benötigen Raum um sie herum, um ihnen die entsprechende Betonung zu verleihen. Dieser Bereich variiert je nach Punktgröße und dem anderen Bereich der Überschrift, z. B. einer horizontalen Regel oder einer Textzeile in der Umgebungsschriftart.

- Die ideale Polsterung für eine Überschrift allein sollte 90% des Großzeichenhöhenraums sein. Beispielsweise hat eine 28-Punkte-Segoe UI Light-Überschrift eine Kappenhöhe von 26 pkT, und die Auffüllung sollte etwa 23 Punkte oder etwa 31 Pixel betragen.

- Der Mindestabstand um eine Überschrift sollte 50 % der Größe des Hauptzeichens betragen. Weniger Platz kann verwendet werden, wenn eine Überschrift von einer Regel oder einem anderen eng anliegenden Element begleitet wird.

- Fettformatierter Umgebungsschrifttext sollte dem Standardabstand der Zeilenhöhe und dem Auffüllen folgen.

## <a name="see-also"></a>Weitere Informationen
 [MSDN: Schriftarten (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: Benutzeroberflächentext (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
