---
title: Schriftarten und Formatierungen für Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 83c1d4e20dd372d3b76362b9f06ee894b045333c
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Schriftarten und Formatierungen für Visual Studio
##  <a name="BKMK_TheEnvironmentFont"></a> Die Umgebungsschriftart verwendet
 Alle Schriftarten in Visual Studio müssen der Benutzer für die Anpassung verfügbar gemacht werden. Dies erfolgt in erster Linie durch die **Schriftarten und Farben** auf der Seite der **Tools > Optionen** Dialogfeld. Die drei Hauptkategorien von schriftarteinstellungen sind:  
  
-   **Umgebungsschriftart** – die primäre Schriftart für die IDE (integrated Development Environment), für alle Elemente der Benutzeroberfläche, z. B. Dialogfelder, Menüs, Toolfenstern und Dokumentfenstern verwendet. Standardmäßig ist die Umgebungsschriftart an eine Systemschriftart gebunden, die als 9 pt Segoe UI in der aktuellen Version von Windows angezeigt wird. Verwenden eine Schriftart für alle Elemente der Benutzeroberfläche kann sichergestellt werden eine konsistente Schriftart Darstellung in der IDE.  
  
-   **Text-Editor** -Elementen, die im Code und andere-Oberfläche textbasierten Editoren im Text-Editor angepasst werden können, auf der Seite **Tools > Optionen**.  
  
-   **Bestimmte Sammlungen** -Designer-Fenster, in denen bieten Anpassung ihrer Elemente der Benutzeroberfläche, Schriftarten, die spezifisch für ihren Entwurf kann ausgesetzt Oberfläche in ihre eigenen Seite "Einstellungen" in **Tools > Optionen**.  
  
### <a name="editor-font-customization-and-resizing"></a>Editor-Schriftart-Anpassung und Ändern der Größe  
 Benutzer werden häufig vergrößern oder Verkleinern der Größe und/oder die Farbe des Texts im Editor entsprechend ihre Voreinstellung, unabhängig von der allgemeinen-Benutzeroberfläche. Da die Umgebungsschriftart für Elemente, die innerhalb oder als Teil einer-Editor-Designer angezeigt werden verwendet wird, ist es wichtig, um das erwartete Verhalten beachten, wenn einer dieser Klassifizierungen Schriftart geändert wird.  
  
 Beim Erstellen der UI-Elemente, die angezeigt werden im Editor, aber sind nicht Teil der *Inhalt*, es ist wichtig, die Umgebungsschriftart verwendet und nicht die Schriftart des Texts zu verwenden, damit Elemente auf einer vorhersagbaren Weise ändern.  
  
1.  Für den Codetext im Editor die mit dem Code Text schriftarteinstellung Größe und zur Zoomstufe für den Editor Text zu reagieren.  
  
2.  Alle anderen Elemente der Benutzeroberfläche an Schriftart umgebungseinstellung gebunden werden soll und auf alle globalen Änderungen in der Umgebung reagieren. Dies umfasst (aber nicht beschränkt auf):  
  
    -   Text in Kontextmenüs  
  
    -   Text in eine Editor-Randsteuerelement wie Glühbirne Menütext, Schnellsuche-Editorfenster, und navigieren Sie zum Bereich  
  
    -   Bezeichnen von Text in Dialogfeldern, z. B. **in Dateien suchen** oder **Umgestalten**  
  
### <a name="accessing-the-environment-font"></a>Zugreifen auf die Umgebungsschriftart verwendet  
 Im einheitlichen Modus oder WinForms-Code, der Umgebungsschriftart möglich durch Aufrufen der Methode `IUIHostLocale::GetDialogFont` nach der Abfrage der Schnittstelle aus dem `SID_SUIHostLocale` Dienst.  
  
 Für Windows Presentation Foundation (WPF), leiten Sie eine Dialogfeld Fenster-Klasse von der Shell `DialogWindow` Klasse anstelle der WPF `Window` Klasse.  
  
 In XAML sieht der Code:
  
```xaml
<ui:DialogWindow  
    x:Class"MyNameSpace.MyWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"  
    ShowInTaskbar="False"  
    WindowStartupLocation="CenterOwner"  
    Title="My Dialog">  
</ui:DialogWindow>  
```

CodeBehind:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow  
{  
}  
```
  
 (Ersetzen Sie `Microsoft.VisualStudio.Shell.11.0` mit der aktuellen Version der Dll MPF.)  
  
 Um das Dialogfeld anzuzeigen, rufen Sie "`ShowModal()`" für die Klasse über `ShowDialog()`. `ShowModal()` den richtigen modalen Status in der Shell wird festgelegt, wird sichergestellt, dass das Dialogfeld "in das übergeordnete Fenster usw. zentriert ist.  
  
 Der Code sieht folgendermaßen aus:  
  
```csharp
MyWindow window = new MyWindow();  
window.ShowModal()  
```
  
 `ShowModal` Gibt einen booleschen Wert an? (NULL-Werte zulässt, Boolean) mit der `DialogResult`, die bei Bedarf verwendet werden können. Der Rückgabewert ist true, wenn das Dialogfeld geschlossen wurde, mit **OK**.  
  
 Wenn Sie einige WPF UI, das ein Dialogfeld ist und gehostet wird in eine eigene anzeigen müssen `HwndSource`, z. B. ein Popupfenster oder ein untergeordnetes Fenster WPF, der eine Win32/WinForms übergeordnete Fenster, müssen Sie festlegen der `FontFamily` und `FontSize` für das Stammelement des WPF-e Element. (Die Shell legt die Eigenschaften fest, auf das Hauptfenster, aber wird nicht nach geerbt werden eine `HWND`). Die Shell stellt Ressourcen, die an die die Eigenschaften können, wie folgt gebunden werden:  
  
```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```
  
###  <a name="BKMK_Formatting"></a> Formatierung (Skalierung/Fettformatieren)-Referenz  
 Einige Dialogfelder erforderlich bestimmtem Text fett formatiert wird eine Größe als die Umgebungsschriftart verwendet wird. Zuvor, Schriftarten, die größer als die Umgebungsschriftart codiert wurde, als "`environment font +2`" oder ähnliches. Mithilfe der bereitgestellten Codeausschnitte wird Unterstützung hoher DPI-Einstellung überwacht, und stellen Sie sicher, dass Anzeigetext immer an die richtige Größe und Gewicht (z. B. Licht oder halb dünne Darstellung) angezeigt wird.  
  
> **Hinweis: Bevor Sie die Formatierung anwenden, stellen Sie sicher sind Sie die Anleitungen in die folgenden [Textart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Wenn die Umgebungsschriftart skaliert werden sollen, legen Sie den Stil der TextBlock oder Bezeichnung wie angegeben. Jede diese Codeausschnitte, die bei korrekter Verwendung generiert die richtige Schriftart, einschließlich der entsprechenden Größe und Gewicht Variationen.  
  
 Wobei "`vsui`" ist ein Verweis auf den Namespace `Microsoft.VisualStudio.Shell`:  

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```
  
#### <a name="375-environment-font--light"></a>Umgebungsschriftart 375 % + dünne Darstellung  
 **Wird als:** 34 pt Segoe UI Light  
 **Verwendung:** (selten) eindeutige Marke Benutzeroberfläche, z. B. auf der Startseite

 **Prozeduraler Code:** , in denen `textBlock` ist ein zuvor definierter TextBlock und `label` ist eine zuvor definierte Bezeichnung:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```
  
 **XAML:** den Stil der TextBlock oder Bezeichnung wie dargestellt festgelegt.  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```
  
#### <a name="310-environment-font--light"></a>Umgebungsschriftart 310 % + dünne Darstellung  
 **Wird als:** 28 pt Segoe UI Light   
 **Verwendung:** große Signatur Dialogfeld Titel, main Überschrift in Berichten  
  
 **Prozeduraler Code:** , in denen `textBlock` ist ein zuvor definierter TextBlock und `label` ist eine zuvor definierte Bezeichnung:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```
  
 **XAML:** den Stil der TextBlock oder Bezeichnung wie dargestellt festgelegt.  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```
  
#### <a name="200-environment-font--semilight"></a>Umgebungsschriftart 200 % + halb dünne Darstellung  
 **Wird als:** 18 pt Segoe UI semilight als    
 **Verwendung:** Aufgliederung, Titel in kleinen und mittleren Dialogfeldern  
  
 **Prozeduraler Code:** , in denen `textBlock` ist ein zuvor definierter TextBlock und `label` ist eine zuvor definierte Bezeichnung: 
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```
  
 **XAML:** den Stil der TextBlock oder Bezeichnung wie dargestellt festgelegt:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```
  
#### <a name="155-environment-font"></a>Umgebungsschriftart mit 155 %  
 **Wird als:** 14 pt Segoe UI    
 **Verwendung:** Überschriften im Dokument gut Benutzeroberflächen oder Berichten  
  
 **Prozeduraler Code:** , in denen `textBlock` ist ein zuvor definierter TextBlock und `label` ist eine zuvor definierte Bezeichnung:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```
  
 **XAML:** den Stil der TextBlock oder Bezeichnung wie dargestellt festgelegt:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```
  
#### <a name="133-environment-font"></a>Umgebungsschriftart mit 133 %  
 **Wird als:** 12 pt Segoe UI    
 **Verwendung:** kleinere Aufgliederung Signatur Dialogfelder und Dokument gut UI  
  
 **Prozeduraler Code:** , in denen `textBlock` ist ein zuvor definierter TextBlock und `label` ist eine zuvor definierte Bezeichnung:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```
  
 **XAML:** den Stil der TextBlock oder Bezeichnung wie dargestellt festgelegt:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```
  
#### <a name="122-environment-font"></a>Umgebungsschriftart mit 122 %  
 **Wird als:** 11 pt Segoe UI    
 **Verwendung:** Abschnitt Überschriften in Dialogfeldern Signatur, die ersten Knoten in der Strukturansicht vertikaler Tabulator-Navigation  
  
 **Prozeduraler Code:** , in denen `textBlock` ist ein zuvor definierter TextBlock und `label` ist eine zuvor definierte Bezeichnung:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```
  
 **XAML:** den Stil der TextBlock oder Bezeichnung wie dargestellt festgelegt:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```
  
#### <a name="environment-font--bold"></a>Umgebungsschriftart + fett  
 **Wird als:** Fett 9 pt Segoe UI    
 **Verwendung:** Bezeichnungen und untergeordnete in Signatur Dialogfelder, Berichte und Dokumente sowie UI  
  
 **Prozeduraler Code:** , in denen `textBlock` ist ein zuvor definierter TextBlock und `label` ist eine zuvor definierte Bezeichnung:  
  
```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```
  
 **XAML:** den Stil der TextBlock oder Bezeichnung wie dargestellt festgelegt:  
  
```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```
  
### <a name="localizable-styles"></a>Lokalisierbare Stile  
 In einigen Fällen müssen Lokalisierungsexperten Schriftschnitte für verschiedene Gebietsschemas, z. B. Fettformatieren von Text für ostasiatische Sprachen entfernen ändern. Um die Lokalisierung von Schriftschnitte möglich ist, müssen diese Stile in die RESX-Datei sein. Die beste Möglichkeit, dies zu erreichen und trotzdem bearbeiten Schriftschnitte in der Visual Studio-Formular-Designer ist die Schriftschnitte zur Entwurfszeit explizit festlegen. Obwohl dies eine vollständige Font-Objekt erstellt und scheinen unterbrechen die Vererbung von übergeordneten Schriftarten, wird der FontStyle-Eigenschaft verwendet, die Schriftart fest.  
  
 Die Lösung besteht darin, Verknüpfen des Formulars Dialog `FontChanged` Ereignis. In der `FontChanged` -Ereignis, alle Steuerelemente zu durchlaufen, und überprüfen Sie, ob ihre Schriftart festgelegt ist. Wenn sie festgelegt ist, ändern Sie ihn auf eine neue Schriftart auf Grundlage des Formulars Schriftart und vorherigen Schriftschnitt des Steuerelements ein. Ein Beispiel dafür im Code ist:  
  
```csharp
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
  
 Mit diesem Code wird sichergestellt, dass bei der Aktualisierung des Formulars Schriftart sowie die Schriftarten Steuerelemente aktualisiert werden. Diese Methode sollte auch aus den Konstruktor des Formulars, aufgerufen werden, da das Dialogfeld "nicht, zum Abrufen einer Instanz des ausgeführt kann `IUIService` und `FontChanged` Ereignis wird nie ausgelöst. Einbinden `FontChanged` lässt Dialogfelder, um zu der neuen Schriftart dynamisch übernehmen, auch wenn das Dialogfeld "bereits geöffnet ist.  
  
### <a name="testing-the-environment-font"></a>Testen der Umgebungsschriftart  
 Um sicherzustellen, dass die Benutzeroberfläche der Umgebungsschriftart verwendet und die größeneinstellungen respektiert, öffnen Sie **Extras > Optionen > Umgebung > Schriftarten und Farben** , und wählen Sie unter "Umgebungsschriftart" der "Einstellungen anzeigen für:" Dropdown-Menü.  
  
 ![Schriftarten und Farben Einstellungen in den Tools &gt; Dialogfeld "Optionen"](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 A_OptionsFonts")<br />Schriftarten und Farben Einstellungen in den Tools &gt; Dialogfeld "Optionen"
  
 Legen Sie etwas ganz anderes als die Standardzeit. Um es offensichtlich, die Benutzeroberfläche nicht aktualisiert wird, wählen Sie eine Schriftart mit Serifen (z. B. "Times New Roman") und legen Sie sehr groß. Anschließend testen Sie die Benutzeroberfläche, um sicherzustellen, dass die Umgebung berücksichtigt. Hier ist ein Beispiel mit dem Dialogfeld "Lizenz":  
  
 ![Beispiel für die UI-Text, der berücksichtigen nicht die Umgebungsschriftart](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 B_WrongFontDialog")<br />Beispiel für die UI-Text, der berücksichtigen nicht die Umgebungsschriftart verwendet
  
 In diesem Fall werden "Benutzerinformationen" und "Produktinformationen" die Schriftart nicht ressourcenbezogene. In einigen Fällen möglicherweise einen expliziten Entwurfsoption allerdings möglich einen Fehler, wenn die explizite Schriftart nicht als Teil von den Spezifikationen (rote Linie) angegeben wird.  
  
 Um die Schriftart zurückzusetzen, klicken Sie auf "Standard verwenden" unter **Extras > Optionen > Umgebung > Schriftarten und Farben**.  
  
##  <a name="BKMK_TextStyle"></a> Textformat  
 Textart bezieht sich auf Schriftgrad, Gewichtung und Groß-/Kleinschreibung. Implementierungsleitfaden für die finden Sie unter [der Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Text Groß-/Kleinschreibung  
  
#### <a name="all-caps"></a>GROSSBUCHSTABEN  
 Verwenden Sie nicht alle gross für Titeln oder Bezeichnungen in Visual Studio.  
  
#### <a name="all-lowercase"></a>Kleinbuchstaben  
 Verwenden Sie nicht alle Kleinbuchstaben für Titeln oder Bezeichnungen in Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Satz- und Titel Groß-/Kleinschreibung  
 Text in Visual Studio sollten Anfangsbuchstaben oder Satz Groß-/Kleinschreibung, je nach Situation verwenden.  
  
|Verwenden Sie die Anfangsbuchstaben für:|Satz-Anwendungsfall für:|  
|-------------------------|----------------------------|  
|Dialogfeld-Titel|Bezeichnungen|  
|Gruppenfelder|Kontrollkästchen|  
|Menüelemente|Optionsfelder|  
|Elemente des Kontextmenüs|Listenfeldelemente|  
|Schaltflächen|Statusleisten|  
|Tabelle-Bezeichnungen||  
|Spaltenheader||  
|QuickInfos||  
  
##### <a name="title-case"></a>Titel Groß-/Kleinschreibung  
 Titel Groß-/Kleinschreibung ist ein Format, in dem die ersten Buchstaben der meisten oder alle Wörter in einem Satz groß geschrieben werden. In Visual Studio wird die Anfangsbuchstaben für viele Elemente, einschließlich verwendet:  
  
-   **QuickInfos.** Beispiel: "Vorschau der ausgewählten Elemente"  
  
-   **Spaltenheader.** Beispiel: "Systemantwort"  
  
-   **Menüelemente.** Beispiel: "Alle speichern"  
  
 Wenn Sie Titel Groß-/Kleinschreibung zu verwenden, sind dies die Richtlinien für wann Wörter in Großbuchstaben umwandelt und wann sie Kleinbuchstaben lassen:  
  
|Großbuchstaben|Kommentare und Beispiele|  
|---------------|---------------------------|  
|Alle Nomen||  
|Alle Verben|Z. B. "Is" und andere Formen von "be"|  
|Alle Adverbien|Einschließlich "Als" und ""|  
|Alle Adjektive|Z. B. "This" und ""|  
|Alle Pronomen|Einschließlich der Possessive "Der" sowie ", wird" ein Zusammenschluss der das Pronomen "es" und das Verb "is"|  
|Vor- und Nachnamen Wörter, unabhängig von Wortarten||  
|Präpositionen, die Teil eines Ausdrucks verb|"Alle Windows wird geschlossen" oder "Das System herunterzufahren"|  
|Alle Buchstaben des Abkürzung|HTML, XML, URL, IDE, RGB|  
|Die zweite word im ein zusammengesetztes Wort wird jedoch ein Nomen oder Adjektiv Eigennamens oder ggf. die Wörter gleich Gewichtung|Querverweisen vor Microsoft-Software-Lese-/Schreibzugriff, zur Laufzeit|  
  
|Kleinbuchstaben|Beispiele|  
|---------------|--------------|  
|Das zweite Worte im ein zusammengesetztes Wort, wenn sie einen anderen Teil der Sprache oder eine Partizip ändern das erste Wort ist|Gewusst wie: Take deaktivieren|  
|Die Artikel, es sei denn, eine auf das erste Wort im Titel ist|ein, der|  
|Koordinieren Konjunktionen|und, aber für, nor, oder|  
|Präpositionen mit Wörtern von maximal vier Buchstaben außerhalb einer Verb-Ausdruck|in auf, wie für out, auf den Anfang|  
|Option "to", bei der Verwendung in eine unendliche Ausdruck|"Gewusst wie: Formatieren der Festplatte"|  
  
##### <a name="sentence-case"></a>Satz Groß-/Kleinschreibung  
 Satz Groß-/Kleinschreibung ist die standardmäßige Groß-/Kleinschreibung-Methode zum Schreiben in die nur das erste Wort des Satzes großgeschrieben ist, sowie alle Eigennamen und das Pronomen "I". Satz Groß-/Kleinschreibung ist im Allgemeinen einfacher für einem weltweiten Publikum zu lesen, insbesondere wenn der Inhalt von einem Computer übersetzt wird. Satz-Anwendungsfall für:  
  
1.  **Statusleistenmeldungen.** Diese einfache, kurz und geben Sie nur die Statusinformationen. Beispiel: "Laden Projektdatei"  
  
2.  **Alle anderen Benutzeroberflächenelementen**, einschließlich Bezeichnungen, die relevanten Kontrollkästchen, Optionsfelder und Kontrollkästchen Listenelemente. Beispiel: "Wählen Sie alle Elemente in der Liste"  
  
### <a name="text-formatting"></a>Formatieren von Text  
 Standardtextformatierung an, die in Visual Studio 2013 wird gesteuert, indem [der Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Dieser Dienst unterstützt eine konsistente Schriftart Darstellung in der IDE (integrated Development Environment) stellen Sie sicher, und Sie müssen ihn verwenden, um eine konsistente Umgebung für Ihre Benutzer zu gewährleisten.  
  
 Die Standardgröße von Visual Studio-Schriftart-Dienst verwendete stammt von Windows und als 9 pt angezeigt wird.  
  
 Sie können die Formatierung der Schriftart, die Umgebung anwenden. Dieses Thema behandelt, wie und wo Formate verwendet werden. Informationen der Implementierung finden Sie unter [der Umgebungsschriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Fett formatierter text  
 Fett formatierter Text wird in Visual Studio nur selten verwendet und für reserviert werden sollten:  
  
-   Frage Bezeichnungen Assistenten  
  
-   Festlegen des aktiven Projekts im Projektmappen-Explorer  
  
-   überschreiben die Werte in den Eigenschaften-Toolfenster  
  
-   bestimmte Ereignisse in den Dropdownlisten Visual Basic-editor  
  
-   vom Server generierte Inhalt in der dokumentgliederung für Webseiten  
  
-   Abschnittsheader in komplexen Dialog- oder Designer-Benutzeroberfläche  
  
#### <a name="italics"></a>Kursiv  
 Visual Studio verwendet keine kursiv oder fett formatierten Text kursiven.  
  
#### <a name="color"></a>Farbe  
  
-   Blau ist für Links (Navigation und Befehle) reserviert und sollte nie für die Ausrichtung verwendet werden.  
  
-   Größere Überschriften (Umgebungsschriftart x mit 155 % oder höher) können für diese Zwecke gefärbt:  
  
    -   Bereitstellen von visuell ansprechender Signatur Visual Studio-Benutzeroberfläche  
  
    -   Die Aufmerksamkeit auf einen bestimmten Bereich  
  
    -   Die Textfarbe standardumgebung dunkel grau/schwarzen Rahmen anbieten.  
  
-   Farbe in Überschriften sollten vorhandene Visual Studio Brand Farben, in erster Linie die wichtigsten Violett #FF68217A nutzen.  
  
-   Bei Farbe in Überschriften verwenden zu können, müssen Sie berücksichtigt werden die [Windows Farbe Richtlinien](https://msdn.microsoft.com/en-us/library/dn742482.aspx), einschließlich Kontrast und andere Aspekte der Barrierefreiheit.  
  
### <a name="font-size"></a>Schriftgrad  
 Entwurf von Visual Studio-Benutzeroberfläche bietet eine hellere Darstellung mit mehr Leerzeichen. Wenn möglich, haben Titel-und Chrome reduziert oder entfernt wurde. Während informationsdichte in Visual Studio erforderlich ist, weiterhin Typografie mit Schwerpunkt auf Zeilenabstand mehr öffnen und eine Variante der Schriftgrade Ihren Bedürfnissen und Gewichtungen wichtig sein.  
  
 Die folgenden Tabellen enthält Details zum Design und visual Beispiele für die Schriftarten in Visual Studio verwendet. Einige Schriftart datenvisualisierungsoption müssen die Größe und die Gewichtung, z. B. halb dünne Darstellung oder Licht, in deren Darstellung codiert.  
  
 Codeausschnitte für alle Schriftarten Implementierung finden Sie im [Formatierung (Skalierung/Fettformatieren) Verweis](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Umgebungsschriftart 375 % + dünne Darstellung  
  
|||  
|-|-|  
|**Syntax:** selten. Eindeutige Branding UI nur.<br /><br /> **Do:**<br /><br /> -Satz Groß-/Kleinschreibung verwendet<br />-Lightweight immer verwenden<br /><br /> **Tue nicht:**<br /><br /> -Verwendung für die Benutzeroberfläche als Signatur Benutzeroberfläche, z. B. die Startseite<br />-Fett, kursiv oder fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie im Toolfenster|**Wird als:** 34 pt Segoe UI Light<br /><br /> **Bildbeispiel:**<br /><br /> *Derzeit verwendet nicht. Kann auf der Startseite verwendet werden.*|  
  
#### <a name="310-environment-font--light"></a>Umgebungsschriftart 310 % + dünne Darstellung  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Größere Überschrift in der Signatur-Dialogfelder<br />-Main Berichtskopf<br /><br /> **Do:**<br /><br /> -Satz Groß-/Kleinschreibung verwendet<br />-Lightweight immer verwenden<br /><br /> **Tue nicht:**<br /><br /> -Verwendung für die Benutzeroberfläche als Signatur Benutzeroberfläche, z. B. die Startseite<br />-Fett, kursiv oder fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie im Toolfenster|**Wird als:** 28 pt Segoe UI Light<br /><br /> **Bildbeispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart 310 % &#43; Überschrift](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>Umgebungsschriftart 200 % + halb dünne Darstellung  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Aufgliederung<br />-Titel in kleinen und mittleren Dialogfelder<br /><br /> **Do:**<br /><br /> -Satz Groß-/Kleinschreibung verwendet<br />-Verwenden Sie immer Gewichtung halb dünne Darstellung<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv oder fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie im Toolfenster|**Wird als:** 18 pt Segoe UI Semillight<br /><br /> **Bildbeispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart 200 % &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|  
  
#### <a name="155-environment-font"></a>Umgebungsschriftart mit 155 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Section-Überschriften in Dokument gut UI<br />-Berichte<br /><br /> **:** Satz Groß-/Kleinschreibung<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv oder fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie in Visual Studio-Standardsteuerelementen<br />– Verwenden Sie im Toolfenster|**Wird als:** 14 pt Segoe UI<br /><br /> **Bildbeispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 155 %, Überschrift](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|  
  
#### <a name="133-environment-font"></a>Umgebungsschriftart mit 133 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Kleinere Aufgliederung in Dialogfeldern Signatur<br />-Im Dokument kleinere Aufgliederung gut UI<br /><br /> **:** Satz Groß-/Kleinschreibung<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv oder fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie in Visual Studio-Standardsteuerelementen<br />– Verwenden Sie im Toolfenster|**Wird als:** 12 pt Segoe UI<br /><br /> **Bildbeispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 133 %, Überschrift](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|  
  
#### <a name="122-environment-font"></a>Umgebungsschriftart mit 122 %  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -Section-Überschriften in Signatur-Dialogfelder<br />-Obersten Knoten in der Strukturansicht<br />-Navigation vertikaler Tabulator<br /><br /> **:** Satz Groß-/Kleinschreibung<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv oder fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie in Visual Studio-Standardsteuerelementen<br />– Verwenden Sie im Toolfenster|**Wird als:** 11 pt Segoe UI<br /><br /> **Bildbeispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 122 %, Überschrift](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|  
  
#### <a name="environment-font--bold"></a>Umgebungsschriftart + fett  
  
|||  
|-|-|  
|**Syntax:**<br /><br /> -"Bezeichnungen" und untergeordnete in Dialogfeldern Signatur<br />-"Bezeichnungen" und untergeordnete in Berichten<br />-"Bezeichnungen" Unterüberschriften im Dokument außerdem UI<br /><br /> **Do:**<br /><br /> -Satz Groß-/Kleinschreibung verwendet<br />– Verwenden Sie die fett formatierten Gewichtung<br /><br /> **Tue nicht:**<br /><br /> -Auswahl kursiver oder fett kursiv<br />-Verwendung für den Textkörper<br />– Verwenden Sie in Visual Studio-Standardsteuerelementen<br />– Verwenden Sie im Toolfenster|**Wird als:** Fett 9 pt Segoe UI<br /><br /> **Bildbeispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart &#43; Überschrift in Fettformatierung](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 F_EFB")|  
  
#### <a name="environment-font"></a>Umgebungsschriftart  
  
|||  
|-|-|  
|**Syntax:** gesamten anderen Text<br /><br /> **:** Satz Groß-/Kleinschreibung<br /><br /> **Keine:** kursiv oder kursiv|**Wird als:** 9 pt Segoe UI<br /><br /> **Bildbeispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 G_EF")|  
  
### <a name="padding-and-spacing"></a>Abstand  
 Überschriften Speicherplatz darum geben die entsprechenden Betonung benötigt wird. Dieser Speicherplatz variiert je nach Größe und was in der Nähe der Überschrift, z. B. eine horizontale Linie oder einer Zeile des Texts in der Umgebungsschriftart ist.  
  
-   Die ideale Auffüllung für eine Überschrift allein sollte 90 % des Speicherplatzes Höhe Kapitalkosten Zeichen sein. Z. B. eine 28 pt Segoe UI Light Überschrift hat eine Höhe von 26 pt, und die Auffüllung sollte ungefähr 23 pt oder ungefähr 31 Pixel sein.  
  
-   Die minimale Platz, um eine Überschrift sollte 50 % der Zeichenhöhe Kapitalkosten sein. Weniger Speicherplatz kann verwendet werden, wenn eine Regel oder ein anderes Element enge Anpassung eine Überschrift begleitet wird.  
  
-   Fett formatierte Umgebung Schriftart Text sollte standardmäßig Höhe Zeilenabstand und Auffüllung folgen.  
  
## <a name="see-also"></a>Siehe auch  
 [MSDN: Schriftarten (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Benutzeroberflächentext (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)