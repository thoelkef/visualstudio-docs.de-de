---
title: "Schriftarten und Formatierungen f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Schriftarten und Formatierungen f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_TheEnvironmentFont"></a> Die Umgebungsschriftart  
 Alle Zeichen innerhalb von Visual Studio müssen der Benutzer für die Anpassung verfügbar gemacht werden. Dies geschieht hauptsächlich durch die **Schriftarten und Farben** Seite der **Tools \> Optionen** Dialogfeld. Die drei Hauptkategorien von Schriftarten sind:  
  
-   **Umgebungsschriftart** – die primäre Schriftart für die IDE \(integrated Development Environment\), für alle Elemente der Benutzeroberfläche, z. B. Dialogfelder, Menüs, Toolfenstern und Dokumentfenstern. Standardmäßig ist die Umgebungsschriftart an eine Systemschriftart gebunden, die als 9 pt Segoe UI in aktuellen Versionen von Windows angezeigt. Mithilfe einer Schriftart für alle Elemente der Benutzeroberfläche, eine einheitliche Schriftarten Darstellung in der IDE sichergestellt.  
  
-   **Texteditor** \-Elementen, die Flächen in Code und andere textbasierte Editoren im Text\-Editor angepasst werden können, Seite **Tools \> Optionen**.  
  
-   **Bestimmte Sammlungen** – Designerfenstern, die Anpassung ihrer Elemente der Benutzeroberfläche unter Umständen Schriftarten speziell für ihren Entwurf ausgesetzt bieten eigene Einstellungen auf der Seite auf Fläche **Tools \> Optionen**.  
  
### Anpassung der Editor\-Schriftart und Größe  
 Benutzer werden häufig vergrößern oder verkleinern die Größe und\/oder die Farbe des Texts im Editor entsprechend ihren Einstellungen, unabhängig von der allgemeinen\-Benutzeroberfläche. Da die Umgebungsschriftart auf Elemente verwendet wird, die in oder als Teil einer Editor\-Designer angezeigt werden, ist es wichtig, das erwartete Verhalten beachten, wenn einer dieser Klassifizierungen Schriftart geändert wird.  
  
 Beim Erstellen der UI\-Elemente in Editor, jedoch sind nicht Teil der *Inhalt*, es ist wichtig, die Umgebungsschriftart und nicht die Schriftart des Texts zu verwenden, sodass Elemente in einer vorhersagbaren Weise angepasst werden.  
  
1.  Von Code in den Editor Größe mit Code Text festgelegt, und der Editor Text Zoomstufe beantworten.  
  
2.  Alle anderen Elemente der Benutzeroberfläche der Umgebung Schriftart Einstellung gebunden werden soll, und klicken Sie auf globale Änderungen in der Umgebung reagieren. Dies umfasst \(aber nicht beschränkt auf\):  
  
    -   Text in Kontextmenüs  
  
    -   Text in einem Zusatzelement Editor, z. B. Glühbirne Menütext, schnelle Suchen Editorbereich, und navigieren Sie zum Bereich  
  
    -   Beschriften von Text in Dialogfeldern, z. B. in Dateien suchen oder Umgestalten  
  
### Zugreifen auf die Umgebungsschriftart  
 In WinForms oder systemeigenen Code, die Umgebungsschriftart ist möglich durch Aufrufen der Methode **IUIHostLocale::GetDialogFont** nach der Abfrage der Schnittstelle aus der SID\_SUIHostLocale\-Dienst.  
  
 Für Windows Presentation Foundation \(WPF\), der Shell die Dialogfeld\-Fensterklasse abgeleitet **DialogWindow** \-Klasse anstelle der WPF **Fenster** Klasse.  
  
 In XAML sieht der Code folgendermaßen aus:  
  
```  
<ui:DialogWindow x:Class"MyNameSpace.MyWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0" ShowInTaskbar="False" WindowStartupLocation="CenterOwner" Title="My Dialog"> </ui:DialogWindow> code behind: internal partial class WebConfigModificationWindow : DialogWindow { }  
  
```  
  
 \(Ersetzen Sie `Microsoft.VisualStudio.Shell.11.0` mit der aktuellen Version der Dll MPF.\)  
  
 Um das Dialogfeld anzuzeigen, rufen Sie "**ShowModal\(\)**" für die Klasse über **OpenFileDialog**.**ShowModal\(\)** legt den richtigen modalen Status in der Shell, wird sichergestellt, das Dialogfeld ist zentriert im übergeordneten Fenster und So weiter.  
  
 Der Code lautet wie folgt:  
  
```  
MyWindow window = new MyWindow(); window.ShowModal()  
  
```  
  
 **ShowModal** gibt einen booleschen Wert? \(auf NULL festlegbare Boolean\) mit den **DialogResult**, die verwendet werden kann, falls erforderlich. Der Rückgabewert ist True, wenn das Dialogfeld geschlossen wurde, mit **OK**.  
  
 Wenn Sie einige WPF UI, das ist ein Dialogfeld, und befindet sich in einem eigenen anzeigen müssen **HwndSource**, z. B. ein Popup\-Fenster oder ein untergeordnetes Fenster WPF, der eine Win32\/WinForms übergeordneten Fenster, müssen Sie festlegen der **FontFamily** und **FontSize** für das Stammelement der WPF\-Elements. \(Die Shell die Eigenschaften für das Hauptfenster festgelegt, aber wird nicht nach einem HWND vererbt werden\). Die Shell stellt Ressourcen, die an die Eigenschaften können, wie folgt gebunden werden:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="BKMK_Formatting"></a> Formatierung \(Skalierung\/\-Stärke\)\-Referenz  
 Einige Dialogfelder erfordern bestimmte Text fett formatiert wird oder eine andere Größe als die Umgebungsschriftart. Bisher waren die Schriftarten, die größer als die Umgebungsschriftart codierten als "Umgebungsschriftart \+ 2" oder ähnlich. Mithilfe der bereitgestellten Codeausschnitte wird Hochauflösenden Monitors unterstützen und sicherzustellen, dass Anzeigetext immer an die richtige Größe und Gewicht \(z. B. "Light" oder "Semilight"\) angezeigt wird.  
  
> **Hinweis: Bevor Sie die Formatierung anwenden, sicherzustellen, folgen Sie die Anleitung finden Sie in [Textstil](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Legen Sie den Stil des TextBlock oder der Bezeichnung wie angegeben, um die Umgebungsschriftart zu skalieren. Alle diese Codeausschnitte ordnungsgemäß verwendet wird, wird die richtige Schriftart, einschließlich der entsprechenden Größe und Gewicht Variationen generiert.  
  
 "Vsui" ist, in dem ein Verweis auf den Namespace Microsoft.VisualStudio.Shell:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### Umgebungsschriftart 375 % \+ dünne Darstellung  
 **Wird als:** 34 pt Segoe UI Light  
  
 **Für verwenden:** \(selten\) eindeutig mit Branding\-Benutzeroberfläche, z. B. die Startseite  
  
 **Prozedurcode:** in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### Umgebungsschriftart 310 % \+ dünne Darstellung  
 **Wird als:** 28 pt Segoe UI Light  
  
 **Für verwenden:** große Signatur Dialogfeld Titel, main Überschrift in Berichten  
  
 **Prozedurcode:** in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### Umgebungsschriftart 200 % \+ halb dünne Darstellung  
 **Wird als:** 18 pt Segoe UI Semilight  
  
 **Für verwenden:** Unterüberschriften, Titel in kleinen und mittleren Dialogfelder  
  
 **Prozedurcode:** in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### Umgebungsschriftart mit 155 %  
 **Wird als:** 14 pt Segoe UI  
  
 **Für verwenden:** Abschnittsüberschriften in Dokument auch Benutzeroberflächen oder Berichten  
  
 **Prozedurcode:** in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### Umgebungsschriftart mit 133 %  
 **Wird als:** 12 pt Segoe UI  
  
 **Für verwenden:** kleinere Unterüberschriften Signatur Dialoge und Dokument und Benutzeroberfläche  
  
 **Prozedurcode:** in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### Umgebungsschriftart mit 122 %  
 **Wird als:** 11 pt Segoe UI  
  
 **Für verwenden:** Abschnitt Überschriften in der Signatur Dialoge, top\-Knoten in der Strukturansicht vertikaler Tabulator\-Navigation  
  
 **Prozedurcode:** in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### Umgebungsschriftart \+ fett  
 **Wird als:** Fett 9 pt Segoe UI  
  
 **Für verwenden:** Bezeichnungen und Unterüberschriften in Signatur Dialogfelder, Berichte und Dokument und Benutzeroberfläche  
  
 **Prozedurcode:** in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironmentBoldStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML:** legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### Lokalisierbare Stile  
 In einigen Fällen müssen Lokalisierer Schriftschnitte für verschiedene Gebietsschemas, z. B. das Entfernen von\-Stärke aus Text für ostasiatische Sprachen zu ändern. Um die Lokalisierung von Schriftarten zu ermöglichen, müssen diese Formate in der RESX\-Datei sein. Die beste Möglichkeit, dies und noch bearbeiten Schriftschnitte in der Visual Studio\-Formular\-Designer ist die Schriftarten zur Entwurfszeit explizit festlegen. Obwohl dies ein Schriftartobjekt für die vollständige erstellt und scheint unterbrechen die Vererbung von übergeordneten Schriftarten, wird nur die FontStyle\-Eigenschaft verwendet, die Schriftart fest.  
  
 Die Lösung besteht darin, Verknüpfen des Formulars Dialog **FontChanged** Ereignis. In der **FontChanged** Ereignis, das Durchlaufen aller Steuerelemente, und überprüfen Sie, ob die Schriftart festgelegt ist. Wenn sie festgelegt ist, ändern Sie ihn auf eine neue Schriftart basierend auf der Schriftart des Formulars und vorherigen Schriftart des Steuerelements. Ein Beispiel dafür im Code ist:  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e) { SetFontStyles(); } /// <summary> /// SetFontStyles - This function will iterate all controls on a page /// and recreate their font with the desired fontstyle. /// It should be called in the OnFontChanged handler (and also in the constructor /// in case the IUIService is not available so OnFontChange doesn't fire). /// This way, when the VS shell font is given to us the controls that have /// a different style for the font (bolded for example) will recreate their font /// and use the VS shell font but with a style variation (bolded ...). /// </summary> protected void SetFontStyles() { SetFontStyles(this, this, this.Font); } protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont) { foreach(Control c in parent.Controls) { if (c.Controls != null && c.Controls.Count > 0) { SetFontStyles(topControl, c, referenceFont); } if (c.Font != topControl.Font) { c.Font = new Font(referenceFont, c.Font.Style); } } }  
```  
  
 Mit diesem Code wird sichergestellt, dass bei der Aktualisierung der Schriftart des Formulars sowie die Schriftarten Steuerelemente aktualisiert werden. Diese Methode sollte ebenfalls vom Konstruktor des Formulars aufgerufen werden, da das Dialogfeld fehlschlagen kann, um eine Instanz des **IUIService** und **FontChanged** Ereignis wird nie ausgelöst. Einbinden von **FontChanged** können Dialoge dynamisch die neue Schriftart auswählen, auch wenn das Dialogfeld bereits geöffnet ist.  
  
### Testen die Umgebungsschriftart  
 Um sicherzustellen, dass die Benutzeroberfläche die Umgebungsschriftart und die Einstellungen berücksichtigt, öffnen **Extras \> Optionen \> Umgebung \> Schriftarten und Farben** und wählen Sie unter "Umgebungsschriftart" der "Einstellungen anzeigen für:" im Dropdown\-Menü.  
  
 ![Fonts and Colors page in Tools &#62; Options dialog](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201\-a\_OptionsFonts")  
  
 **Schriftarten und Farben Einstellungen im Menü Extras \> Dialogfeld "Optionen"**  
  
 Legen Sie die Schriftart auf etwas ganz anderes als die Standardeinstellung. Um es offensichtlich, die Benutzeroberfläche nicht aktualisiert wird, wählen Sie eine Schriftart mit Serifen \(z. B. "Times New Roman"\) und legen Sie sehr groß. Anschließend testen Sie die Benutzeroberfläche, um sicherzustellen, dass die Umgebung berücksichtigt. Hier ist ein Beispiel mit dem Dialogfeld Lizenz:  
  
 ![Example of dialog not using the environment font](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201\-b\_WrongFontDialog")  
  
 **Beispiel für Benutzeroberflächen\-Text, der berücksichtigen nicht die Umgebungsschriftart verwendet**  
  
 In diesem Fall werden "Benutzerinformationen" und "Produktinformationen" die Schriftart nicht beachten. In einigen Fällen möglicherweise eine explizite entwurfsentscheidung, aber es kann ein Fehler sein, wenn die explizite Schriftart nicht als Teil der Spezifikationen \(rote Linie\) angegeben wird.  
  
 Um die Schriftart zurückzusetzen, klicken Sie auf "Standard verwenden" unter **Extras \> Optionen \> Umgebung \> Schriftarten und Farben**.  
  
##  <a name="BKMK_TextStyle"></a> Textstil  
 Textformat bezieht sich auf den Schriftgrad, Gewichtung und Groß\-\/Kleinschreibung. Implementierungsleitfaden für die finden Sie unter [Die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### Text Groß\-\/Kleinschreibung  
  
#### Großbuchstaben  
 Verwenden Sie nicht Großbuchstaben für Titel oder Bezeichnungen in Visual Studio.  
  
#### Kleinbuchstaben  
 Verwenden Sie nur Kleinbuchstaben für Titeln oder Bezeichnungen in Visual Studio.  
  
#### Satz\- und Titel Groß\-\/Kleinschreibung  
 Text in Visual Studio sollten Anfangsbuchstaben oder Großbuchstaben, je nach Situation verwenden.  
  
|Verwenden Sie für große Anfangsbuchstaben:|Verwenden Sie Großbuchstaben für:|  
|------------------------------------------------|---------------------------------------|  
|Dialogfeld\-Titel|Bezeichnungen|  
|Gruppenfelder|Kontrollkästchen|  
|Menüelemente|Optionsfelder|  
|Elemente des Kontextmenüs|Listenfeldelemente|  
|Schaltflächen|Statusleisten|  
|Tabelle labels||  
|Spaltenüberschriften||  
|QuickInfos||  
  
##### Großschreibung  
 Großschreibung ist ein Format, in dem die ersten Buchstaben der meisten oder alle Wörter in einem Satz groß geschrieben werden. In Visual Studio wird die Großschreibung für viele Elemente, einschließlich verwendet:  
  
-   **QuickInfos.** Beispiel: "Vorschau der ausgewählten Elemente"  
  
-   **Spaltenüberschriften.** Beispiel: "Antwort"  
  
-   **Menüelemente.** Beispiel: "Alle speichern"  
  
 Wenn große Anfangsbuchstaben verwenden, sind dies die Richtlinien für wann Wörter in Großbuchstaben umwandelt und wann lassen sie Kleinbuchstaben:  
  
|Großbuchstaben|Kommentare und Beispiele|  
|--------------------|------------------------------|  
|Alle Nomen||  
|Alle Verben|Einschließlich "Is" und andere Arten von "werden"|  
|Alle Adverbien|"Als" sowie ""|  
|Alle Adjektive|Z. B. "This" und ""|  
|Alle Pronomen|Einschließlich der Possessive "Die" sowie ", wird" ein Zusammenschluss der das Pronomen "it" und das Verb "is"|  
|Vor\- und Nachnamen ausgedrückt, unabhängig von Wortarten||  
|Präpositionen, in der ein Ausdruck sind|"Schließt alle Fenster" oder "Das System herunterzufahren"|  
|Alle Buchstaben der Abkürzung|HTML, XML, URL, IDE, RGB|  
|Die zweite Wort im ein zusammengesetztes Wort, wenn es ein Nomen oder Adjektiv, das richtige ist oder Wörter die gleiche Gewichtung haben|Querverweis vor Microsoft\-Software, Lese\-\/Schreibzugriff auf, die zur Laufzeit|  
  
|Kleinbuchstaben|Beispiele|  
|---------------------|---------------|  
|Das zweite Wort ein zusammengesetztes Wort, wenn er einen anderen Teil der Sprache oder eine Änderung des ersten Worts Partizip|Gewusst\-wie\-Take\-aus|  
|Die Artikel, es sei denn, eine das erste Wort im Titel|ein, der|  
|Koordinieren von Konjunktionen|und, aber für, noch ist, oder|  
|Präpositionen mit Wörtern von vier oder weniger Zeichen als ein Ausdruck|in auf, wie für out\-of, auf den|  
|Option "zu", wenn Sie in eine unendliche Ausdruck verwendet|"Gewusst wie: Formatieren der Festplatte"|  
  
##### Großbuchstaben  
 Großbuchstaben ist die Großschreibung\-Methode zum Schreiben in die nur das erste Wort des Satzes groß geschrieben wird, sowie alle Eigennamen und das Pronomen "I". Großbuchstaben ist im Allgemeinen einfacher für einem weltweiten Publikum zu lesen, insbesondere wenn der Inhalt von einem Computer übersetzt werden. Verwenden Sie Großbuchstaben für:  
  
1.  **Statusleistenmeldungen.** Diese sind also einfach und liefert nur Statusinformationen. Beispiel: "Laden Projektdatei"  
  
2.  **Alle anderen Elemente der Benutzeroberfläche**, einschließlich Etiketten, Kontrollkästchen, Optionsfelder und Kontrollkästchen Listenelemente. Beispiel: "wählen alle Elemente in der Liste"  
  
### Formatieren von Text  
 Standardtext\-Formatierung in Visual Studio 2013 wird gesteuert, indem eine [Die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Dieser Dienst ermöglicht eine einheitliche Schriftarten Darstellung in der IDE \(integrated Development Environment\) stellen Sie sicher, und Sie müssen es verwenden, um eine konsistente Umgebung für Ihre Benutzer zu gewährleisten.  
  
 Die Standardgröße von der Visual Studio\-Schriftart\-Dienst verwendeten stammt aus Windows und wird als 9 pt.  
  
 Sie können die Formatierung in die Umgebungsschriftart anwenden. In diesem Thema, wie und wo Formate verwendet werden. Implementierungsinformationen finden Sie unter [Die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### Fett formatierter text  
 Fett formatierter Text wird in Visual Studio nur selten verwendet und für reserviert werden soll:  
  
-   Frage Bezeichnungen in Assistenten  
  
-   Festlegen des aktiven Projekts im Projektmappen\-Explorer  
  
-   überschreiben die Werte im Eigenschaftenfenster  
  
-   bestimmte Ereignisse in den Dropdownlisten für Visual Basic\-editor  
  
-   Server erstellte Inhalte im Dokumentgliederungsfenster für Webseiten  
  
-   Abschnittsnamen in komplexer oder Designer\-Benutzeroberfläche  
  
#### Kursiv  
 Visual Studio verwendet nicht kursiv oder fett kursiv.  
  
#### Farbe  
  
-   Blau ist für Links \(Navigation und Befehle\) reserviert und sollte nie für die Ausrichtung verwendet werden.  
  
-   Größere Überschriften \(Umgebungsschriftart x 155 % oder höher\) können für diese Zwecke zugewiesen werden:  
  
    -   Die Signatur Visual Studio\-Benutzeroberfläche visuell ansprechender bereitstellen  
  
    -   Die Aufmerksamkeit auf einen bestimmten Bereich  
  
    -   Fehleranfällige die Farbe des dunklen Grau\/schwarzen Umgebung anbieten  
  
-   Farbe in Überschriften sollten vorhandene Visual Studio Marke Farben in erster Linie die wichtigsten Violett \#FF68217A nutzen.  
  
-   Wenn Farbe in Überschriften verwenden möchten, müssen Sie folgen, die [Windows Farbe Richtlinien](https://msdn.microsoft.com/en-us/library/dn742482.aspx), einschließlich Kontrastverhältnis und andere Aspekte der Eingabehilfen.  
  
### Schriftgrad  
 Entwurf der Visual Studio\-Benutzeroberfläche bietet eine hellere Darstellung mit mehr Leerzeichen. Wo möglich, Chrome und Titelleisten reduziert oder entfernt wurden. Während der informationsdichte in Visual Studio ist, weiterhin Typografie wichtig, mit Schwerpunkt auf offenen Zeilenabstand und eine Variante der Schriftgrade und Weights.  
  
 Die folgenden Tabellen enthält Einzelheiten und Beispiele für die in Visual Studio verwendeten Schriftarten. Einige anzeigevarianten müssen, die Größe und Gewicht, z. B. Semilight oder Licht in ihrer Darstellung codiert.  
  
 Implementierung von Codeausschnitte für alle Schriftarten Sie unter finden anzeigen [Formatierung (Skalierung/-Stärke)-Referenz](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### Umgebungsschriftart 375 % \+ dünne Darstellung  
  
|||  
|-|-|  
|**Verwendung:** selten. Eindeutige Branding UI nur.<br /><br /> **Führen Sie aus:**<br /><br /> -   Verwenden Sie Großbuchstaben<br />-   Verwenden Sie immer Lightweight<br /><br /> **Beachten Sie:**<br /><br /> -   Verwenden für die Benutzeroberfläche als Signatur Benutzeroberfläche, z. B. Startseite<br />-   Fett, kursiv oder fett kursiv<br />-   Verwenden Sie für den Textkörper<br />-   Verwenden Sie im Toolfenster|**Wird als:** 34 pt Segoe UI Light<br /><br /> **Visual\-Beispiel:**<br /><br /> *Derzeit nicht verwendet. Kann auf der Startseite verwendet werden.*|  
  
#### Umgebungsschriftart 310 % \+ dünne Darstellung  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -   Größere Überschrift in der Signatur\-Dialogfelder<br />-   Hauptbericht Überschrift<br /><br /> **Führen Sie aus:**<br /><br /> -   Verwenden Sie Großbuchstaben<br />-   Verwenden Sie immer Lightweight<br /><br /> **Beachten Sie:**<br /><br /> -   Verwenden für die Benutzeroberfläche als Signatur Benutzeroberfläche, z. B. Startseite<br />-   Fett, kursiv oder fett kursiv<br />-   Verwenden Sie für den Textkörper<br />-   Verwenden Sie im Toolfenster|**Wird als:** 28 pt Segoe UI Light<br /><br /> **Visual\-Beispiel:**<br /><br /> ![Example of 310% Environment font &#43; Light heading](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202\-a\_EF310")|  
  
#### Umgebungsschriftart 200 % \+ halb dünne Darstellung  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -   Untertitel<br />-   Titel in kleinen und mittleren Dialogfelder<br /><br /> **Führen Sie aus:**<br /><br /> -   Verwenden Sie Großbuchstaben<br />-   Verwenden Sie immer Semilight Gewicht<br /><br /> **Beachten Sie:**<br /><br /> -   Fett, kursiv oder fett kursiv<br />-   Verwenden Sie für den Textkörper<br />-   Verwenden Sie im Toolfenster|**Wird als:** 18 pt Segoe UI Semillight<br /><br /> **Visual\-Beispiel:**<br /><br /> ![Example of 200% Environment font &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202\-b\_EF200")|  
  
#### Umgebungsschriftart mit 155 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -   Überschriften im Dokument und Benutzeroberfläche<br />-   Berichte<br /><br /> **Führen:** Satz Anwendungsfall<br /><br /> **Beachten Sie:**<br /><br /> -   Fett, kursiv oder fett kursiv<br />-   Verwenden Sie für den Textkörper<br />-   Verwenden Sie im Standard\-Steuerelemente von Visual Studio<br />-   Verwenden Sie im Toolfenster|**Wird als:** 14 pt Segoe UI<br /><br /> **Visual\-Beispiel:**<br /><br /> ![Example of 155% Environment font heading](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202\-c\_EF155")|  
  
#### Umgebungsschriftart mit 133 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -   Kleinere Unterüberschriften in der Signatur\-Dialogfelder<br />-   Kleinere Unterüberschriften im Dokument und Benutzeroberfläche<br /><br /> **Führen:** Satz Anwendungsfall<br /><br /> **Beachten Sie:**<br /><br /> -   Fett, kursiv oder fett kursiv<br />-   Verwenden Sie für den Textkörper<br />-   Verwenden Sie im Standard\-Steuerelemente von Visual Studio<br />-   Verwenden Sie im Toolfenster|**Wird als:** 12 pt Segoe UI<br /><br /> **Visual\-Beispiel:**<br /><br /> ![Example of 133% Environment font heading](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202\-d\_EF133")|  
  
#### Umgebungsschriftart mit 122 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -   Abschnittsüberschriften von Signatur\-Dialogfelder<br />-   Knoten auf oberster Ebene in der Strukturansicht<br />-   Vertikaler Tabulator\-navigation<br /><br /> **Führen:** Satz Anwendungsfall<br /><br /> **Beachten Sie:**<br /><br /> -   Fett, kursiv oder fett kursiv<br />-   Verwenden Sie für den Textkörper<br />-   Verwenden Sie im Standard\-Steuerelemente von Visual Studio<br />-   Verwenden Sie im Toolfenster|**Wird als:** 11 pt Segoe UI<br /><br /> **Visual\-Beispiel:**<br /><br /> ![Example of 122% Environment font heading](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202\-e\_EF122")|  
  
#### Umgebungsschriftart \+ fett  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -   Etiketten und Unterüberschriften in Dialogfeldern Signatur<br />-   Etiketten und Unterüberschriften in Berichten<br />-   Etiketten und Unterüberschriften im Dokument und Benutzeroberfläche<br /><br /> **Führen Sie aus:**<br /><br /> -   Verwenden Sie Großbuchstaben<br />-   Verwenden Sie die Schriftbreite fett<br /><br /> **Beachten Sie:**<br /><br /> -   Kursiv oder fett kursiv<br />-   Verwenden Sie für den Textkörper<br />-   Verwenden Sie im Standard\-Steuerelemente von Visual Studio<br />-   Verwenden Sie im Toolfenster|**Wird als:** Fett 9 pt Segoe UI<br /><br /> **Visual\-Beispiel:**<br /><br /> ![Example of Environment font &#43; Bold heading](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202\-f\_EFB")|  
  
#### Umgebungsschriftart  
  
|||  
|-|-|  
|**Verwendung:** alle anderen Text<br /><br /> **Führen:** Satz Anwendungsfall<br /><br /> **Nicht:** kursiv oder kursiv|**Wird als:** 9 pt Segoe UI<br /><br /> **Visual\-Beispiel:**<br /><br /> ![Example of Environment font](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202\-g\_EF")|  
  
### Abstand  
 Überschriften erfordern zwischen ihnen die entsprechenden Betonung gewähren. Dieser Speicherplatz variiert je nach Größe und was in der Nähe der Überschrift, z. B. eine horizontale Linie oder eine Textzeile in der Umgebungsschriftart befindet.  
  
-   Die ideale Auffüllung für eine Überschrift allein sollte 90 % des Speicherplatzes Höhe großes Zeichen sein. Z. B. Überschrift Segoe UI Light 28 pt hat eine Höhe von 26 pt und der Textabstand sollte ungefähr 23 pt oder ungefähr 31 Pixel sein.  
  
-   Der mindestens erforderliche Speicherplatz, um eine Überschrift sollte es sich um 50 % der Zeichenhöhe großes sein. Weniger Speicherplatz kann verwendet werden, wenn eine Regel oder ein anderes Element eine enge Anpassung eine Überschrift begleitet wird.  
  
-   Fett formatierte Umgebung Schriftart Text befolgen Höhe von Standard\-Zeilenabstand und Abstände.  
  
## Siehe auch  
 [MSDN: Schriftarten \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Benutzeroberflächentext \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)