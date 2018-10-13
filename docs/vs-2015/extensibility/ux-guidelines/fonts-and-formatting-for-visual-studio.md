---
title: Schriftarten und Formatierungen für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44f9bff7fe1508094474b7067237e8c0b6620605
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275469"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Schriftarten und Formatierungen für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_TheEnvironmentFont"></a> Die Umgebungsschriftart verwendet  
 Alle Schriftarten in Visual Studio müssen der Benutzer für die Anpassung verfügbar gemacht werden. Dies erfolgt in erster Linie durch die **Schriftarten und Farben** auf der Seite die **Tools > Optionen** Dialogfeld. Die drei Hauptkategorien der schriftarteinstellungen sind:  
  
-   **Umgebungsschriftart** – die primären Schriftart für die IDE (integrated Development Environment), für alle Elemente der Benutzeroberfläche, einschließlich der Dialogfelder, Menüs, Toolfenster und Dokumentfenster. Standardmäßig ist die Umgebungsschriftart verwendet, eine Systemschriftart gebunden, die als 9 pt Segoe UI in aktuellen Versionen von Windows angezeigt wird. Verwenden eine Schriftart für alle Elemente der Benutzeroberfläche trägt dazu bei eine einheitlichen Schriftart Darstellung in der IDE.  
  
-   **Text-Editor** – Elemente, die Surface im Code und andere textbasierte Editoren im Text-Editor angepasst werden können, auf der Seite **Tools > Optionen**.  
  
-   **Bestimmte Sammlungen** – Designerfenstern, die bieten Anpassung ihrer Elemente der Benutzeroberfläche, Schriftarten, die speziell für ihren Entwurf kann ausgesetzt Oberfläche in ihre eigenen Seite "Einstellungen" im **Tools > Optionen**.  
  
### <a name="editor-font-customization-and-resizing"></a>-Editor-Schriftart Anpassung und Ändern der Größe  
 Benutzer häufig vergrößern oder verkleinern die Größe und/oder die Farbe des Texts im Editor nach Präferenz, unabhängig von der Benutzeroberfläche für die allgemeine. Da die Umgebungsschriftart für Elemente verwendet wird, die innerhalb oder als Teil einer Designer/Editor angezeigt werden kann, ist es wichtig, um das erwartete Verhalten zu beachten, wenn Sie eine der folgenden Klassifizierungen Schriftart geändert wird.  
  
 Beim Erstellen der UI-Elemente, die angezeigt werden im Editor, aber sind nicht Teil der *Inhalt*, es ist wichtig, die Umgebungsschriftart verwendet und nicht für die Schriftart des Texts zu verwenden, sodass Elemente in einer vorhersagbaren Weise angepasst.  
  
1.  Für den Codetext im Editor die mit der Einstellung "Code Text Schriftart" Größe und zur Zoomstufe für den EditorText zu reagieren.  
  
2.  Alle anderen Elemente der Benutzeroberfläche gebunden werden sollte, um die umgebungseinstellung für die Schriftart und reagieren auf eine beliebige globale Änderungen in der Umgebung. Dies umfasst (aber ist nicht beschränkt auf):  
  
    -   Text in Kontextmenüs  
  
    -   Text, z. B. Glühbirne Menütext, schnell ein Zusatzelement Editor finden im Bereich-Editor, und navigieren Sie zum Bereich  
  
    -   Bezeichnungstext in Dialogfeldern, z. B. in Dateien suchen oder Umgestalten  
  
### <a name="accessing-the-environment-font"></a>Zugreifen auf die Umgebungsschriftart verwendet  
 Im einheitlichen Modus oder WinForms-Code, die Umgebungsschriftart erfolgen kann durch Aufrufen der Methode **IUIHostLocale::GetDialogFont** nach Abfragen der Schnittstelle aus dem SID_SUIHostLocale-Dienst.  
  
 Für Windows Presentation Foundation (WPF), leiten Sie die Klasse der Dialogfeld-Fenster aus der Shell **DialogWindow** -Klasse anstelle der WPF **Fenster** Klasse.  
  
 In XAML sieht der Code folgendermaßen aus:  
  
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
  
 (Ersetzen Sie dies `Microsoft.VisualStudio.Shell.11.0` mit der aktuellen Version der Dll MPF.)  
  
 Um das Dialogfeld anzuzeigen, rufen "**ShowModal()**" für die Klasse über **OpenFileDialog**. **ShowModal()** den richtigen modalen Status in der Shell handelt, wird sichergestellt, das Dialogfeld wird in das übergeordnete Fenster, und So weiter zentriert.  
  
 Der Code lautet wie folgt aus:  
  
```  
MyWindow window = new MyWindow();  
window.ShowModal()  
  
```  
  
 **ShowModal** Ruft einen Boolschen Wert? (NULL-Werte zulässt, Boolean) mit der **DialogResult**, die bei Bedarf verwendet werden kann. Der zurückgegebene Wert ist true, wenn das Dialogfeld geschlossen wurde **OK**.  
  
 Wenn Sie eine WPF-UI, die kein Dialogfeld und gehostet wird in einem eigenen anzeigen müssen **HwndSource**, z. B. ein Popup-Fenster oder ein WPF-untergeordnetes Fenster von einem übergeordneten Fenster Fenster von Win32/WinForms, Sie müssen Festlegen der **FontFamily**und **FontSize** für das Stammelement der WPF-Elements. (Die Shell legt die Eigenschaften im Hauptfenster, aber sie werden nicht nach einem HWND geerbt werden). Die Shell bietet Ressourcen, die an die die Eigenschaften können, wie folgt gebunden werden:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="BKMK_Formatting"></a> Formatierung (Skalierung/in Fettdruck zu setzen)-Referenz  
 Einige Dialogfelder erfordern bestimmte Text fett formatiert wird, oder eine andere Größe als die Umgebungsschriftart verwendet. Zuvor waren Schriftarten, die größer als die Umgebungsschriftart codierten als "Umgebungsschriftart + 2" oder ähnlich. Verwenden die bereitgestellten Codeausschnitte werden hohe DPI-Monitore unterstützen und sicherstellen, dass es sich bei Anzeigetext immer an die richtige Größe und Gewicht (z. B. "Light" oder "semilight als") angezeigt wird.  
  
> **Hinweis: Bevor Sie die Formatierung anwenden, stellen Sie sicher Sie folgen den Anleitungen unter [Textart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Um die Umgebungsschriftart skalieren zu können, legen Sie den Stil der TextBlock oder Label wie angegeben. Jede diese Codeausschnitte, die ordnungsgemäß verwendet wird, wird die richtige Schriftart, einschließlich der entsprechenden Größe und Gewicht Variationen generiert.  
  
 "Vsui" ist, in denen ein Verweis auf den Namespace Microsoft.VisualStudio.Shell:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### <a name="375-environment-font--light"></a>Umgebungsschriftart mit 375 % + dünne Darstellung  
 **Wird als:** 34 pt Segoe UI Light  
  
 **Verwendung:** (selten vorkommenden) eindeutig mit Branding Benutzeroberfläche, z. B. in der Startseite  
  
 **Prozeduraler Code:** , in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** den Stil der TextBlock oder Label wie dargestellt festgelegt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### <a name="310-environment-font--light"></a>Umgebungsschriftart mit 310 % + dünne Darstellung  
 **Wird als:** 28 pt Segoe UI Light  
  
 **Verwendung:** große Signatur Dialogfeld Titel, main Überschrift in Berichten  
  
 **Prozeduraler Code:** , in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** den Stil der TextBlock oder Label wie dargestellt festgelegt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### <a name="200-environment-font--semilight"></a>Umgebungsschriftart mit 200 % + halb dünne Darstellung  
 **Wird als:** 18 pt Segoe UI semilight als  
  
 **Verwendung:** Unterüberschriften, Titel in Dialogfeldern für kleine und mittlere  
  
 **Prozeduraler Code:** , in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** den Stil der TextBlock oder Label wie dargestellt festgelegt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### <a name="155-environment-font"></a>Umgebungsschriftart mit 155 %  
 **Wird als:** 14 pt Segoe UI  
  
 **Verwendung:** Abschnittsüberschriften in Dokument gut, Benutzeroberflächen oder Berichten  
  
 **Prozeduraler Code:** , in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** den Stil der TextBlock oder Label wie dargestellt festgelegt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### <a name="133-environment-font"></a>Umgebungsschriftart mit 133 %  
 **Wird als:** 12 pt Segoe UI  
  
 **Verwendung:** kleinere Unterüberschriften in der Signatur-Dialogfelder und Dokument und Benutzeroberfläche  
  
 **Prozeduraler Code:** , in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** den Stil der TextBlock oder Label wie dargestellt festgelegt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### <a name="122-environment-font"></a>Umgebungsschriftart mit 122 %  
 **Wird als:** 11 pt Segoe UI  
  
 **Verwendung:** Abschnitt Spaltenüberschriften in der Signatur Dialogfelder, top-Knoten in der Strukturansicht vertikaler Tabulator-Navigation  
  
 **Prozeduraler Code:** , in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** den Stil der TextBlock oder Label wie dargestellt festgelegt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### <a name="environment-font--bold"></a>Umgebungsschriftart + fettformatierung  
 **Wird als:** Fett 9 pt Segoe UI  
  
 **Verwendung:** Bezeichnungen und Teilüberschriften Signatur Dialogfelder, Berichte und Dokument und Benutzeroberfläche  
  
 **Prozeduraler Code:** , in denen "TextBlock" wird eine zuvor definierte TextBlock und "Label" ist eine zuvor definierte Bezeichnung.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML:** den Stil der TextBlock oder Label wie dargestellt festgelegt.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### <a name="localizable-styles"></a>Lokalisierbare Stile  
 In einigen Fällen müssen Lokalisierungsexperten Schriftschnitte für verschiedene Gebietsschemas, z. B. Fettformatieren von Text für ostasiatische Sprachen entfernen zu ändern. Um die Lokalisierung von Schriftarten zu ermöglichen, müssen diese Stile in die RESX-Datei sein. Die beste Möglichkeit, dies zu erreichen und immer noch bearbeiten Schriftschnitte in der Visual Studio-Formular-Designer werden explizit die Schriftschnitte zur Entwurfszeit festgelegt. Obwohl dies ein Schriftartobjekt für die vollständige erstellt und scheint die Vererbung von übergeordneten Schriftarten zu unterbrechen, wird nur der FontStyle-Eigenschaft verwendet, die Schriftart fest.  
  
 Die Lösung besteht darin, Verknüpfen des Formulars Dialog **FontChanged** Ereignis. In der **FontChanged** -Ereignis, führen Sie alle Steuerelemente, und überprüfen Sie, ob die Schriftart festgelegt ist. Wenn sie festgelegt ist, ändern Sie ihn auf eine neue Schriftart, die auf der Grundlage der Schriftart des Formulars und vorherigen Font Format des Steuerelements ein. Ein Beispiel dafür im Code ist:  
  
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
  
 Mit dem folgenden Code wird sichergestellt, dass wenn der Schriftart des Formulars aktualisiert wird, sowie die Schriftarten Steuerelemente aktualisiert werden. Diese Methode sollte ebenfalls über den Konstruktor des Formulars, aufgerufen werden, da der Dialog einen Fehler möglicherweise, um eine Instanz des **IUIService** und **FontChanged** Ereignis wird niemals ausgelöst werden. Einbinden von **FontChanged** ermöglicht Dialogfelder, dynamisch um die neue Schriftart zu übernehmen, selbst wenn das Dialogfeld bereits geöffnet ist.  
  
### <a name="testing-the-environment-font"></a>Testen die Umgebungsschriftart verwendet  
 Um sicherzustellen, dass die Benutzeroberfläche die Umgebungsschriftart verwendet wird und die Einstellungen für die berücksichtigt, öffnen Sie **Tools > Optionen > Umgebung > Schriftarten und Farben** , und wählen Sie "Umgebungsschriftart" unter den "Einstellungen anzeigen für:" im Dropdownmenü.  
  
 ![Seite "Schriftarten und Farben" in den Tools &#62; Dialogfeld "Optionen"](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201-A_OptionsFonts")  
  
 **Einstellungen für Schriftarten und Farben in den Tools > Dialogfeld "Optionen"**  
  
 Legen Sie etwas ganz anderes als den Standardwert. Damit offensichtlich können die Benutzeroberfläche nicht aktualisiert wird, wählen Sie eine Schriftart mit Serifen an (z. B. "Times New Roman"), und legen Sie sehr groß. Anschließend testen Sie die Benutzeroberfläche, um sicherzustellen, dass sie die Umgebung berücksichtigt. Hier ist ein Beispiel mit dem Dialogfeld "Lizenz":  
  
 ![Beispiel des Dialogfelds ", die nicht über die Umgebungsschriftart](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201-B_WrongFontDialog")  
  
 **Beispiel für die UI-Text, der berücksichtigen nicht die Umgebungsschriftart verwendet**  
  
 "Benutzerinformationen" und "Produktinformationen" Benennung in diesem Fall werden nicht von der Schriftart. In einigen Fällen kann dies eine explizite entwurfsentscheidung sein, aber es kann ein Fehler sein, wenn die explizite Schriftart nicht als Teil der Spezifikationen (rote Linie) angegeben wird.  
  
 Um die Schriftart zurückzusetzen, klicken Sie auf "Standard verwenden" unter **Tools > Optionen > Umgebung > Schriftarten und Farben**.  
  
##  <a name="BKMK_TextStyle"></a> Textstil  
 Textformat bezieht sich auf den Schriftgrad, Gewichtung und Groß-/Kleinschreibung. Leitfaden für die Implementierung, finden Sie unter [die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Text Groß-/Kleinschreibung  
  
#### <a name="all-caps"></a>Großbuchstaben  
 Verwenden Sie nicht Großbuchstaben für Titel und Bezeichnungen in Visual Studio.  
  
#### <a name="all-lowercase"></a>Alles Kleinbuchstaben  
 Verwenden Sie nicht ausschließlich Kleinbuchstaben für Titeln oder Bezeichnungen in Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Satz- und Titel Groß-/Kleinschreibung  
 Text in Visual Studio muss entweder große Anfangsbuchstaben Satz groß, je nach Situation verwenden.  
  
|Verwenden Sie große Anfangsbuchstaben für:|Verwenden Sie bei der Satz:|  
|-------------------------|----------------------------|  
|Dialogfeld-Titel|Bezeichnungen|  
|Gruppenfelder|Kontrollkästchen|  
|Menüelemente|Optionsfelder|  
|Kontextmenüelemente|Listenfeldelemente|  
|Schaltflächen|Statusleisten|  
|Tabelle-Bezeichnungen||  
|Spaltenheader||  
|QuickInfos||  
  
##### <a name="title-case"></a>Große Anfangsbuchstaben  
 Große Anfangsbuchstaben ist ein Format, in dem die ersten Buchstaben des meisten oder alle der Wörter in einem Ausdruck in Großbuchstaben angegeben werden. In Visual Studio wird die große Anfangsbuchstaben für viele Elemente, einschließlich verwendet:  
  
-   **QuickInfos.** Beispiel: "Vorschau der ausgewählten Elemente"  
  
-   **Spaltenüberschriften.** Beispiel: "System Antworten"  
  
-   **Menüelemente.** Beispiel: "Alle speichern"  
  
 Wenn Sie große Anfangsbuchstaben verwenden zu können, sind dies die Richtlinien, wenn Wörter in Großbuchstaben umwandelt und wann Sie Kleinbuchstaben ausgelassen werden:  
  
|Großbuchstaben|Kommentare und Beispiele|  
|---------------|---------------------------|  
|Alle Nomen||  
|Alle Verben|Wie "Is" und andere Formen von "be"|  
|Alle Adverbien|Einschließlich "Als" und "Wann"|  
|Alle Adjektive|Einschließlich "This" und ""|  
|Alle Pronomen|Einschließlich der Hauptwortgruppe "Die" ebenfalls unverändert"," ein Zusammenschluss der das Pronomen "it" und das Verb "is"|  
|Vor- und Nachnamen Wörter, unabhängig von Wortarten||  
|Präpositionen, die Teil eines Ausdrucks verb|"Wird geschlossen, alle Windows" oder "Das System herunterzufahren"|  
|Alle Buchstaben der Abkürzung|HTML-"," XML "," URL "," IDE "," RGB|  
|Die zweite Begriff im ein zusammengesetztes Wort angezeigt, wenn es sich um ein Nomen oder Adjektiv, das richtige ist, oder wenn die Wörter die gleiche Gewichtung haben|Querverweis, vor der Microsoft-Software-Lese-/Schreibzugriff, Laufzeit|  
  
|Kleinbuchstaben|Beispiele|  
|---------------|--------------|  
|Das zweite Wort in einem zusammengesetzten Wort, wenn sie einen anderen Teil der Sprache oder einem Partizip, ändern das erste Wort ist|Exemplarische Vorgehensweise, Take-off|  
|Die Artikel, es sei denn, eine ist, dass das erste Wort im Titel|a, ein, die|  
|Koordinieren von Konjunktionen|und für, nor, oder|  
|Präpositionen mit Wörtern, die von vier oder weniger Zeichen als ein Ausdruck|in auf, wie für out-of, oben|  
|Option "zu", bei der Verwendung in eine unendliche Ausdruck|"Gewusst wie: Formatieren der Festplatte"|  
  
##### <a name="sentence-case"></a>Großgeschrieben  
 Großgeschrieben ist die Großschreibung-Methode zum Schreiben in die nur das erste Wort des Satzes groß geschrieben wird, sowie alle Eigennamen und das Pronomen "I". Im Allgemeinen ist die großgeschrieben einfacher für eine weltweite Zielgruppe zu lesen, insbesondere wenn der Inhalt von einem Computer übersetzt wird. Verwenden Sie bei der Satz:  
  
1.  **Statusleistenmeldungen.** Diese sind einfach, kurz gesagt, und geben Sie nur die Statusinformationen. Beispiel: "Laden-Projektdatei"  
  
2.  **Alle anderen Elemente der Benutzeroberfläche**, z. B. Bezeichnungen, Kontrollkästchen, Optionsfelder und Einträge aufzulisten. Beispiel: "wählen alle Elemente in der Liste"  
  
### <a name="text-formatting"></a>Formatieren von Text  
 Standardtextformatierung an, die in Visual Studio 2013 wird gesteuert, indem ein [die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Dieser Dienst trägt dazu bei eine einheitlichen Schriftart Darstellung in der IDE (integrated Development Environment), und Sie müssen ihn verwenden, um eine konsistente Umgebung für Ihre Benutzer zu gewährleisten.  
  
 Die Standardgröße von der Visual Studio-Schriftart-Dienst verwendeten Windows entnommen und wird als 9 pt.  
  
 Sie können die Formatierung in die Umgebungsschriftart anwenden. Dieses Thema behandelt, wie und wo Formate verwendet werden. Implementierungsinformationen, finden Sie unter [die Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Fett formatierter text  
 Fett formatierter Text ist in Visual Studio nur selten verwendet und für die reserviert werden sollten:  
  
-   Frage Bezeichnungen in Assistenten  
  
-   Festlegen des aktiven Projekts im Projektmappen-Explorer  
  
-   überschreiben die Werte in das Toolfenster "Eigenschaften"  
  
-   bestimmte Ereignisse in der Dropdownliste von Visual Basic-editor  
  
-   Server erstellte Inhalte in der dokumentgliederung für Webseiten  
  
-   Abschnittsheadern in komplexen Dialog oder Designer-Benutzeroberfläche  
  
#### <a name="italics"></a>Kursiv  
 Visual Studio verwendet entweder "Kursiv" oder "Fett kursiv formatierten Text nicht.  
  
#### <a name="color"></a>Farbe  
  
-   Blau ist für Links (Navigation und Befehle) reserviert und sollte nie für die Ausrichtung verwendet werden.  
  
-   Größere Überschriften (Umgebungsschriftart x mit 155 % oder höher) können für diese Zwecke zugewiesen werden:  
  
    -   Um visuelle Elemente, die Signatur von Visual Studio-Benutzeroberfläche bereitzustellen.  
  
    -   Die Aufmerksamkeit auf einen bestimmten Bereich  
  
    -   Die Textfarbe der standardumgebung dunkel grau/schwarzen Rahmen anbieten.  
  
-   Farbe in Überschriften sollten vorhandene Visual Studio markenfarben, in erster Linie die wichtigsten Violett, #FF68217A nutzen.  
  
-   Bei Verwendung von Farbe in Überschriften müssen eingehalten werden die [Windows Farbe Richtlinien](https://msdn.microsoft.com/library/dn742482.aspx), einschließlich Kontrastverhältnis und weitere Überlegungen für die Barrierefreiheit.  
  
### <a name="font-size"></a>Schriftgrad  
 Entwurf von Visual Studio-Benutzeroberfläche verfügt über eine hellere Darstellung mit mehr Leerzeichen. Wo möglich, Chrome und Titelleisten verringert oder entfernt wurden. Während die informationsdichte in Visual Studio erforderlich ist, weiterhin Typografie wichtig ist, mit dem Schwerpunkt offenere Zeilenabstand und eine Variante der Schriftgrade und Gewichtungen.  
  
 Die folgenden Tabellen enthält, Designdetails und Beispiele für die Anzeigeschriftarten in Visual Studio verwendet. Einige Schriftart datenvisualisierungsoption müssen sowohl die Größe und Gewicht, z. B. semilight als "oder" Light in ihre Darstellung codiert.  
  
 Implementierung von Codeausschnitten für alle Schriftarten finden Sie im [Formatierung (Skalierung/fettformatierung) Verweis](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Umgebungsschriftart mit 375 % + dünne Darstellung  
  
|||  
|-|-|  
|**Syntax:** selten. Eindeutige mit Branding nur über die Benutzeroberfläche.<br /><br /> **Führen Sie aus:**<br /><br /> – Verwenden Sie großgeschrieben<br />-Verwenden Sie einfache immer<br /><br /> **Tue nicht:**<br /><br /> -Verwendung für die Benutzeroberfläche als Signatur Benutzeroberfläche, z. B. die Startseite<br />-Fett, kursiv und fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie das im Toolfenster|**Wird als:** 34 pt Segoe UI Light<br /><br /> **Visual-Beispiel:**<br /><br /> *Derzeit verwendet nicht. Auf der Startseite die Option kann verwendet werden.*|  
  
#### <a name="310-environment-font--light"></a>Umgebungsschriftart mit 310 % + dünne Darstellung  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Größere Überschrift in der Signatur-Dialogfelder<br />-Main Berichtskopf<br /><br /> **Führen Sie aus:**<br /><br /> – Verwenden Sie großgeschrieben<br />-Verwenden Sie einfache immer<br /><br /> **Tue nicht:**<br /><br /> -Verwendung für die Benutzeroberfläche als Signatur Benutzeroberfläche, z. B. die Startseite<br />-Fett, kursiv und fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie das im Toolfenster|**Wird als:** 28 pt Segoe UI Light<br /><br /> **Visual-Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 310 % &#43; hell Überschrift](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202-a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>Umgebungsschriftart mit 200 % + halb dünne Darstellung  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> : Unterüberschriften<br />: Titel in Dialogfeldern für kleine und mittlere<br /><br /> **Führen Sie aus:**<br /><br /> – Verwenden Sie großgeschrieben<br />-Verwenden Sie immer semilight als Gewichtung<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv und fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie das im Toolfenster|**Wird als:** 18 pt Segoe UI Semillight<br /><br /> **Visual-Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 200 % &#43; semilight als](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202-b_EF200")|  
  
#### <a name="155-environment-font"></a>Umgebungsschriftart mit 155 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Section-Überschriften in Dokument und Benutzeroberfläche<br />-Berichte<br /><br /> **:** Großgeschrieben verwenden<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv und fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie in Visual Studio-Standardsteuerelementen<br />– Verwenden Sie das im Toolfenster|**Wird als:** 14 pt Segoe UI<br /><br /> **Visual-Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 155 %, Überschrift](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202-c_EF155")|  
  
#### <a name="133-environment-font"></a>Umgebungsschriftart mit 133 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Kleinere Unterüberschriften in der Signatur-Dialogfelder<br />-Kleinere Unterüberschriften im Dokument und Benutzeroberfläche<br /><br /> **:** Großgeschrieben verwenden<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv und fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie in Visual Studio-Standardsteuerelementen<br />– Verwenden Sie das im Toolfenster|**Wird als:** 12 pt Segoe UI<br /><br /> **Visual-Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 133 %, Überschrift](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202-d_EF133")|  
  
#### <a name="122-environment-font"></a>Umgebungsschriftart mit 122 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Section-Spaltenüberschriften in der Signatur-Dialogfelder<br />-Obersten Knoten in der Strukturansicht<br />-Vertikaler Tabulator-navigation<br /><br /> **:** Großgeschrieben verwenden<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv und fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie in Visual Studio-Standardsteuerelementen<br />– Verwenden Sie das im Toolfenster|**Wird als:** 11 pt Segoe UI<br /><br /> **Visual-Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 122 %, Überschrift](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202-e_EF122")|  
  
#### <a name="environment-font--bold"></a>Umgebungsschriftart + fettformatierung  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Bezeichnungen und Teilüberschriften in Dialogfeldern für Signature<br />-Bezeichnungen und untergeordnete in Berichten<br />-Bezeichnungen und Teilüberschriften im Dokument gut UI<br /><br /> **Führen Sie aus:**<br /><br /> – Verwenden Sie großgeschrieben<br />– Verwenden Sie die Schriftbreite fett<br /><br /> **Tue nicht:**<br /><br /> -Kursiv und fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie in Visual Studio-Standardsteuerelementen<br />– Verwenden Sie das im Toolfenster|**Wird als:** Fett 9 pt Segoe UI<br /><br /> **Visual-Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart &#43; Überschrift in Fettformatierung](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202-F_EFB")|  
  
#### <a name="environment-font"></a>Umgebungsschriftart  
  
|||  
|-|-|  
|**Syntax:** gesamten anderen Text<br /><br /> **:** Großgeschrieben verwenden<br /><br /> **Nicht der Fall:** kursiv oder fett kursiv|**Wird als:** 9 pt Segoe UI<br /><br /> **Visual-Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202-G_EF")|  
  
### <a name="padding-and-spacing"></a>Abstand und Abstände  
 Überschriften erfordern eingerahmt um ihnen die entsprechenden Betonung zu gewähren. Dieser Speicherplatz variiert je nach Größe und weiteren neuerungen in der Nähe der Überschrift, z. B. eine horizontale Linie oder einer Zeile des Texts in die Umgebungsschriftart verwendet wird.  
  
-   Die ideale Auffüllung für eine Überschrift selbst sollte 90 % des Speicherplatzes Höhe Großbuchstaben Zeichen sein. Z. B. eine 28 pt Segoe UI Light-Überschrift hat eine Obergrenze-Höhe der 26 pt aus, und die Auffüllung sollte ungefähr 23 pt oder etwa 31 Pixel sein.  
  
-   Der minimale Abstand zu einer Überschrift sollte es sich um 50 % der Zeichenhöhe Großbuchstaben sein. Weniger Speicherplatz kann verwendet werden, wenn eine Regel oder ein anderes Element eine enge Anpassung eine Überschrift begleitet wird.  
  
-   Fett formatiertem Umgebung Schriftart Text sollte es sich um Standard-Zeilenabstand Höhe und Abstand folgen.  
  
## <a name="see-also"></a>Siehe auch  
 [MSDN: Schriftarten (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Text der Benutzeroberfläche (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)

