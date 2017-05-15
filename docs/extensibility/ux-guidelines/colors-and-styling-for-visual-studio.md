---
title: "Farben und Styling für Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 93bfad7dc919364770a7d225c09db8b432cf1be0
ms.contentlocale: de-de
ms.lasthandoff: 05/04/2017

---
# <a name="colors-and-styling-for-visual-studio"></a>Farben und Styling für Visual Studio
## <a name="using-color-in-visual-studio"></a>Mithilfe von Farben in Visual Studio  
In Visual Studio wird die Farbe in erster Linie als Kommunikationstool, nicht nur als Ergänzung verwendet. Verwenden Sie Farbe, Minimal und für Situationen, in denen Sie möchten, zu reservieren:  
  
-   Kommunikation Bedeutung oder einer Zuordnung (z. B. Plattform oder Sprache Modifizierer)  
  
-   Gewinnen Sie Aufmerksamkeit (z. B., der angibt, einer Änderung des)  
  
-   Verbessern Sie der Lesbarkeit und geben Sie Informationen zum Navigieren in der Benutzeroberfläche  
  
-   Erhöhen Sie Serverupgrade  
  
Es sind mehrere Optionen zum Zuweisen von Farben für Elemente der Benutzeroberfläche in Visual Studio vorhanden. In einigen Fällen kann es in eine Form schwierig sein, welche Option Sie verwenden bestimmt, oder wie ordnungsgemäß verwendet werden kann. In diesem Thema helfen Ihnen:  
  
1.  Verstehen Sie die verschiedenen Dienste und Systeme, die zum Definieren von Farben in Visual Studio verwendet.  
  
2.  Wählen Sie die richtige Option für ein angegebenes Element ein.  
  
3.  Verwenden Sie die von Ihnen gewählten Option korrekt.  
  
> **Hinweis:** nie hartcodieren Hex, RGB- oder Systemfarben für Ihre UI-Elemente. Unter Verwendung des Diensts ermöglicht Flexibilität bei der Feineinstellung von Farbton. Darüber hinaus ohne den Dienst nicht werden Nutzen der Design-switching-Funktionen von [des Diensts VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Methoden zum Zuweisen von Farben für Elemente der Visual Studio-Benutzeroberfläche  
Wählen Sie die Methode, die am besten geeignet für Ihre UI-Elemente.  
  
| Die Benutzeroberfläche | Methode | Was sind sie? |  
| --- | --- | --- |  
| Sie verfügen über eingebettete oder eigenständige Dialogfelder. | **Systemfarben** | Systemnamen, mit denen das Betriebssystem, um die Farbe und die Darstellung der Elemente der Benutzeroberfläche zu definieren, wie allgemeine Dialogfeldsteuerelemente. |
| Sie haben benutzerdefinierte Benutzeroberfläche, die mit der gesamten Visual Studio-Umgebung konsistent sein sollen und Sie Benutzeroberflächenelemente, die die Kategorie und die semantische Bedeutung der freigegebenen-Token entsprechen. | **Gemeinsam verwendeten Farben** | Vordefinierte Farben Tokennamen für bestimmte Elemente der Benutzeroberfläche |
| Sie haben eine einzelne Funktion oder eine Gruppe von Funktionen, und es gibt keine freigegebenen Farbe für ähnliche Elemente. | **Benutzerdefinierte Farben** | Tokennamen Farbe, die spezifisch für einen Bereich und nicht gemeinsam mit anderen UI verwendet werden sollen |
| Möchten Sie dem Endbenutzer zum Anpassen der Benutzeroberfläche oder Inhalt (z. B. für Text-Editoren oder spezielle Designerfenstern) ermöglichen. | **Endbenutzer-Anpassung**<br /><br />**(Extras &gt; Dialogfeld "Optionen")** | Auf der Seite "Schriftarten und Farben" des definierten Einstellungen der **Tools &gt; Optionen** Dialogfeld oder eine spezielle Seite, die spezifisch für ein UI-Funktion. |
| Sie haben die Benutzeroberfläche, die im HTML-Format erstellt wurde. | **Daytona** | Ermöglicht die Benutzeroberfläche, die in HTML für den Dienstzugriff Farbe und Schriftart erstellt. |
  
### <a name="visual-studio-themes"></a>Visual Studio-Designs  
Visual Studio bietet drei verschiedene Farbschemas, statusleisteneinstellungen: hell, dunkel und Blau. Außerdem wird erkannt, Modus für hohe Kontraste, die eine systemweite Farbschema für Eingabehilfen konzipiert ist.  
  
Benutzer werden aufgefordert, ein Design auswählen, während der ersten Verwendung von Visual Studio und Designs später zu wechseln, indem Sie möchten, können **Tools &gt; Optionen &gt; Umgebung &gt; allgemeine** und ein neues Design aus der Dropdown-Menü "Farbschema" auswählen.  
  
Benutzer können auch die Systemsteuerung verwenden, um ihre gesamten Systeme in einer von mehreren Designs mit hohem Kontrast zu wechseln. Wenn ein Benutzer ein Design "hoher Kontrast" auswählt, wirkt sich auf klicken Sie dann die Farbauswahl Design Visual Studio nicht mehr Farben in Visual Studio jedoch Designänderungen für gespeichert werden, wenn der Benutzer den Modus für hohe Kontraste beendet wird. Weitere Informationen zum Modus für hohe Kontraste finden Sie unter [auswählen kontrastreiche Farben](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).
  
### <a name="the-vscolor-service"></a>Der Dienst VSColor  
Visual Studio bietet einen Umgebung Farbe-Dienst bekannt, wie der VSColor-Dienst, der Sie die Farbwerte, die von Elementen der Benutzeroberfläche an einen benannten Eintrag Farbwerte für jedes Visual Studio-Designs mit binden kann. Dadurch wird sichergestellt, dass Ihre Farben automatisch geändert werden, entsprechend den aktuellen Benutzer ausgewählten Designs oder System Modus für hohe Kontraste. Verwenden des Diensts bedeutet, dass die Implementierung aller Farbe Design-bezogene Änderungen an einem Ort verarbeitet wird, und bei Verwendung von gemeinsam verwendeten Farben aus dem Dienst Ihre Benutzeroberfläche automatisch neue Designs in zukünftigen Versionen von Visual Studio wider.  
  
### <a name="implementation"></a>Implementierung  
Visual Studio Quellcode umfasst mehrere Paketdefinitionsdateien, die Listen von Tokennamen übernimmt und die jeweiligen Farbwerte für jedes Design enthalten. Der Color-Dienst liest die VSColors diese Paketdefinitionsdateien definiert. Diese Farben werden in XAML-Markup oder im Code verwiesen, und dann geladen wird, entweder durch die `IVsUIShell5.GetThemedColor` -Methode oder eine DynamicResource-Zuordnung.  
  
### <a name="system-colors"></a>Systemfarben  
Allgemeine Steuerelemente verweisen die Systemfarben standardmäßig. Wenn Ihre Benutzeroberfläche Systemfarben, z. B. beim Erstellen eines Dialogs eingebetteten oder eigenständig verwendet werden sollen, müssen Sie nichts zu tun.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>Gemeinsam verwendeten Farben im VSColor-Dienst  
Die Elemente der Benutzeroberfläche sollten die gesamte Visual Studio-Umgebung berücksichtigt werden. Durch das Wiederverwenden der gemeinsamen verwendeten Farben, die für die UI-Komponente geeignet sind, die Sie entwerfen, stellen Sie sicher, dass Ihre Benutzeroberfläche mit anderen Schnittstellen Visual Studio konsistent ist, und die Farben automatisch widergespiegelt werden, wenn Designs hinzugefügt oder aktualisiert werden.  
  
Stellen Sie vor der Verwendung von gemeinsam verwendeten Farben sicher, dass Sie verstehen, wie sie ordnungsgemäß verwendet. Falsche Verwendung von gemeinsam verwendeten Farben möglicherweise ein inkonsistentes, frustrierend oder verwirrend Erfahrungen Ihrer Benutzer.  
  
### <a name="user-customizable-colors"></a>Benutzer anpassbare Farben  
Siehe: [Verfügbarmachen von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
In einigen Fällen sollten Sie den Endbenutzern die Benutzeroberfläche, z. B. anpassen, bei der Erstellung einer Code-Editor oder die Entwurfsoberfläche erlauben. Anpassbare Benutzeroberflächenkomponenten befinden sich in der **Schriftarten und Farben** Teil der **Tools &gt; Optionen** Dialogfeld, in dem Benutzer so ändern Sie die Vordergrundfarbe, Hintergrundfarbe oder beides auswählen können.  
  
![Tools &gt; Dialogfeld "Optionen"](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Tools &gt; Dialogfeld "Optionen"
  
### <a name="web-ui-colors"></a>Web-benutzeroberflächenfarben  
Es wird immer für Autor UI-Komponenten, die mit HTML, sodass sie sowohl in Visual Studio Online und in Visual Studio verwendet werden können. Benutzeroberfläche, die in HTML geschrieben muss weiterhin den VSColor-Dienst verwenden, wenn innerhalb der Visual Studio-Umgebung ausgeführt wird. Informationen zu Daytona und seiner Verwendung finden Sie unter [Daytona und -Webbenutzeroberfläche](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="BKMK_TheVSColorService"></a>Der Dienst VSColor  
Visual Studio bietet einen Umgebung Farbe Dienst auch den VSColor-Dienst oder der Shell Farbe-Dienst genannt. Dieser Dienst ermöglicht Ihnen, das die Farbwerte anzeigt, der die Elemente der Benutzeroberfläche an Name / Wert-Farben, die Farben für jedes Design enthält binden. Der VSColor-Dienst muss für alle Elemente der Benutzeroberfläche verwendet werden, sodass Farben automatisch entsprechend das aktuelle Benutzer ausgewählten Design ändern und, damit zum Dienst Farbe Umgebung Benutzeroberfläche gebunden neue Designs in zukünftigen Versionen von Visual Studio integriert werden.  
  
### <a name="how-the-service-works"></a>Funktionsweise des Diensts  
Die Umgebung Farbe Dienst liest VSColors in der PKGDEF für die UI-Komponente definiert. Diese VSColors klicken Sie dann im XAML-Markup oder-Code referenziert werden und werden geladen, entweder über die `IVsUIShell5.GetThemedColor` oder ein `DynamicResource` Zuordnung.  
  
![Umgebungsfarbe – Dienstarchitektur](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Umgebungsfarbe – Dienstarchitektur
  
### <a name="accessing-the-service"></a>Zugriff auf den Dienst
Es gibt verschiedene Möglichkeiten, den Zugriff der VSColor-Dienst, je nachdem, welche Art von Farbe Sie Token verwenden und welche Art von Code stehen Ihnen.  

#### <a name="predefined-environment-colors"></a>Vordefinierte Umgebungsfarben  
  
##### <a name="from-native-code"></a>Von systemeigenem code  
Die Shell stellt einen Dienst, der Zugriff auf die `COLORREF` der vorhandenen Farben ab. Die Dienstschnittstelle ist:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
In der Datei VSShell80.idl, die Enumeration `__VSSYSCOLOREX` Shell Farbe Konstanten hat. Zur Verwendung als übergebenen den Indexwert entweder einen der Werte aus den `enum __VSSYSCOLOREX` dokumentierten in MSDN oder einen regulären Index, die das Windows-Dateisystem-API, Zahl `GetSysColor`, akzeptiert. Dies ruft wieder den RGB-Wert, der die Farbe, die im zweiten Parameter verwendet werden soll.  
  
Wenn ein Stift oder Pinsel mit eine neue Farbe zu speichern, müssen Sie `AdviseBroadcastMessages` (außerhalb der Visual Studio-Shell) und warten Sie `WM_SYSCOLORCHANGE` und `WM_THEMECHANGED` Nachrichten.  
  
  
Um den Dienst Farbe in systemeigenem Code zuzugreifen, müssen Sie einen Aufruf vornehmen, der Dies ähnelt: 

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);    
```  

> **Hinweis:** der `COLORREF` zurückgegebenen Werte `GetVSSysColorEx()` enthalten nur R, G, B Bestandteile ein Farbdesign. Wenn ein Eintrag Design Transparenz verwendet wird, wird vor der Rückgabe der Alpha-Kanal-Wert verworfen. Daher, wenn die Umgebung Farbe von Interesse muss an einer Stelle verwendet werden, in denen transparenzkanal wichtig ist, sollten Sie verwenden `IVsUIShell5.GetThemedColor` anstelle von `IVsUIShell2::GetVSSysColorEx`, wie weiter unten in diesem Thema beschrieben.  
  
##### <a name="from-managed-code"></a>Aus verwaltetem code  
Zugriff auf den VSColor-Dienst über systemeigenen Code ist recht einfach. Wenn Sie mithilfe von verwaltetem Code arbeiten, kann jedoch ermittelt werden, um den Dienst verwenden als kompliziert erweisen. Beachten Sie ist hier ein C#-Codeausschnitt veranschaulicht diesen Prozess:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)  
{  
    //getIVSUIShell2  
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;  
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");  
  
    if (uiShell2 != null)  
    {  
        //get the COLORREF structure  
        uint win32Color;  
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);  
  
        //translate it to a managed Color structure  
        Color myColor = ColorTranslator.FromWin32((int)win32Color);  
        //use it  
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);  
    }  
}  
```  
  
Wenn Sie in Visual Basic arbeiten, verwenden Sie:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### <a name="from-wpf-ui"></a>Über die WPF-Benutzeroberfläche  
Sie können Visual Studio Farben durch Werte, die in der Anwendungsverzeichnis exportiert binden `ResourceDictionary`. Es folgt ein Beispiel für die Verwendung von Ressourcen aus der Tabelle sowie zum Binden an die Umgebungsdaten für die Schriftart in XAML.  
  
```  
<Style TargetType="{x:Type Button}">  
    <Setter Property="TextBlock.FontFamily"  
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
    <Setter Property="TextBlock.FontSize"  
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
    <Setter Property="Background"  
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />  
</Style>  
```  
  
#### <a name="helper-classes-and-methods-for-managed-code"></a>Hilfsklassen und-Methoden für verwalteten code  
Für verwalteten Code, der Shell Managed Package Framework-Bibliothek (`Microsoft.VisualStudio.Shell.12.0.dll`) enthält eine Reihe von Hilfsklassen, die die Verwendung von Designs Farben erleichtern.  
  
Die Hilfsmethoden der `Microsoft.VisualStudio.Shell.VsColors` -Klasse in MPF enthalten `GetThemedGDIColor()` und `GetThemedWPFColor()`. Diese Hilfsmethoden Rückgabewert der Farbe eines Eintrags Design als `System.Drawing.Color` oder `System.Windows.Media.Color`, um in Windows Forms- oder WPF UI verwendet werden.  
  
```  
IVsUIShell5 shell5;  
Button button = new Button();  
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);  
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);  
  
/// <summary>  
/// Gets a System.Drawing.Color value from the current theme for the given color key.  
/// </summary>  
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>  
/// <param name="themeResourceKey">The key to find the color for.</param>  
/// <returns>The current theme's value of the named color.</returns>  
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);  
  
   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR  
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}  
  
private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Guid category = themeResourceKey.Category;  
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground  
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)  
   {  
      colorType = __THEMEDCOLORTYPE.TCT_Background;  
   }  
  
   // This call will throw an exception if the color is not found  
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);  
   return BitConverter.GetBytes(rgbaColor);  
}  
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);  
  
    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}    
```  
  
Die Klasse kann auch verwendet werden, um VSCOLOR-IDs für einen bestimmten WPF Farbe Ressource-Schlüssel zu erhalten oder umgekehrt.  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
Die Methoden der `VsColors` Klasse Abfragen des VSColor-Diensts zurückzugebenden Wert für die Farbe jedes Mal aufgerufen. Um einen Farbwert als erhalten `System.Drawing.Color`, eine Alternative mit besserer Leistung ist, verwenden Sie stattdessen die Methoden der der `Microsoft.VisualStudio.PlatformUI.VSThemeColor` -Klasse, die die Farbwerte, die vom Dienst VSColor zwischenspeichert. Die Klasse intern Shell Broadcastmeldungen Ereignisse abonniert und verwirft den zwischengespeicherten Wert aus, wenn es sich bei einem veränderlichen Design-Ereignis tritt auf. Die Klasse stellt außerdem ein. NET-freundliche Ereignis Designänderungen abonnieren. Verwenden Sie die `ThemeChanged` Ereignis, um einen neuen Handler hinzuzufügen, und verwenden die `GetThemedColor()` Methode, um Farbe abzurufen, Werte für die `ThemeResourceKeys` von Interesse sind. Beispielcode kann wie folgt aussehen:  
  
```  
public MyWindowPanel()  
{  
    InitializeComponent();  
  
    // Subscribe to theme changes events so we can refresh the colors  
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;  
  
    RefreshColors();  
}  
  
private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)  
{  
    RefreshColors();  
  
    // Also post a message to all the children so they can apply the current theme appropriately  
    foreach (System.Windows.Forms.Control child in this.Controls)  
    {  
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);  
    }  
}  
  
private void RefreshColors()  
{  
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);  
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);  
}  
  
protected override void Dispose(bool disposing)  
{  
    if (disposing)  
    {  
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;  
        base.Dispose(disposing);}  
}  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a>Kontrastreiche Farben auswählen  
  
### <a name="overview"></a>Übersicht  
Windows verwendet mehrere hohem Kontrast auf Systemebene Designs bereit, die die Farbe von Text, Hintergründen und Bilder, Kontrast ausführenden Elemente klarer auf dem Bildschirm angezeigt werden. Aus Gründen der Barrierefreiheit ist es wichtig, dass die Elemente der Visual Studio-Benutzeroberfläche richtig zu antworten, wenn Benutzer zum Design mit hohem Kontrast wechseln.  
  
Für hohen Kontrast Designs kann nur eine Handvoll Systemfarben verwendet werden. Wenn Sie Ihr System Farbnamen auswählen, beachten Sie die folgenden Tipps:  
  
1.  **Wählen Sie die Systemfarben, die die gleiche semantische Bedeutung haben** als das Element, das Sie Farbgebung sind. Für die Instanz, wenn Sie eine hohe Kontraste Farbe für den Text innerhalb eines Fensters auswählen, verwenden Sie WindowText und nicht ControlText.  
  
2.  **Auswählen von Vordergrund-/Hintergrundfarbe Paare** zusammen sein, oder Sie nicht sicher, dass die Farbauswahl in allen hoher Kontrast-Designs geeignet ist.  
  
3.  **Zu bestimmen, welche Teile der Benutzeroberfläche am wichtigsten sind, und stellen Sie sicher, dass Inhaltsbereiche hervorzuheben.** Viele Details, die normalerweise geringfügige Unterschiede bei Farbton Farbe unterscheiden würde, geht verloren, damit die Verwendung der starken Rahmenfarben allgemeine Inhaltsbereiche, definiert ist, da keine Farbe Varianten für verschiedene Inhaltsbereiche vorhanden sind.  
  
### <a name="system-color-set"></a>System-Farbpalette  
Die Tabelle auf [WPF-Teamblog: SystemColors Verweis](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) gibt den vollständigen Satz von Systemnamen für die Farbe und die entsprechenden Farbtöne im Design "Jeder" angezeigt.  
  
Beim Anwenden dieser Satz von Farben an die Benutzeroberfläche beschränkt *es wird erwartet, dass Sie feine Details verlieren, die in den "normale" Designs vorhanden waren*. Hier ist ein Beispiel der Benutzeroberfläche mit feine grauen Farben aus, die verwendet werden, um die Unterscheidung von Bereichen in einem Toolfenster ein. Wenn das gleiche Fenster angezeigt, die im Modus für hohe Kontraste zugeordnet, können Sie sehen, dass alle Hintergründe der gleiche Farbton und den Rahmen dieser Bereiche werden durch Rahmen allein angegeben:  
  
![Beispiel mit Details wie feine sind verlorene Bestätigungen in hoher Kontrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Beispiel mit Details wie feine sind verlorene Bestätigungen in hoher Kontrast
  
#### <a name="choosing-text-colors-in-an-editor"></a>Auswählen von Textfarben in einem editor  
Farbdruckoption Text wird in einem Editor oder auf einer Entwurfsoberfläche verwendet, um anzugeben, d. h., wie das Zulassen der für die einfache Identifikation von Gruppen mit ähnlichen Elementen. In einem Design "hoher Kontrast" jedoch müssen nicht die Möglichkeit der Unterscheidung zwischen mehr als drei Textfarben Sie. WindowText, GrayText und HotTrackText sind der einzigen Farben auf WindowBackground Flächen. Da Sie mehr als drei Farben verwenden können, sorgfältig wählen Sie die wichtigsten Unterschiede, die im Modus für hohe Kontraste angezeigt werden soll.  
  
Farbtöne für jede von den Tokennamen zulässig in einem Editor angezeigt, wie sie in jeder Design mit hohem Kontrast angezeigt werden:  
  
![Hoher Kontrast-Editor-Vergleich](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Editor im Design "Hoher Kontrast", Vergleich
  
Beispiele für die Editor-Entwurfsoberfläche in das Design "Blau":  
  
![Editor im Design "Blau"](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor im Design "Blau"
  
![Editor im Design "hoher Kontrast #1"](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor im Design "hoher Kontrast #1"
  
### <a name="usage-patterns"></a>Verwendungsmuster
Viele allgemeine Elemente der Benutzeroberfläche haben bereits kontrastreiche Farben definiert. Sie können diese Verwendungsmuster verweisen, wenn Sie Ihren eigenen System Farbnamen, auswählen, damit Ihre UI-Elemente mit ähnlichen Komponenten konsistent sind.  
  
| Systemfarbe | Verwendung |
| --- | --- |
| ActiveCaption | -Active IDE "und" rafted Fenster Schaltfläche Symbole auf, wenn darauf gezeigt wird, und drücken Sie<br />-Befehlsleisten-Hintergrund für die IDE und rafted Windows Titel<br />-Standard Statusleisten-Hintergrund |
| ActiveCaptionText | -Active IDE und rafted Windows für Titel Leiste Vordergrund (Text und Symbole)<br />-Im Hintergrund und Rahmen des aktiven Fensters Schaltflächen gezeigt wird, und drücken Sie |
| Steuerelement | -Kombinationsfeld, Dropdown-Liste, und suchen gesteuert und Hintergrund, einschließlich der Dropdown-Schaltfläche deaktiviert<br />-Dock Ziel-Schaltfläche im Hintergrund<br />-Befehlsleisten-Hintergrund<br />-Hintergrund für das Definitionsfenster tool |
| ControlDark | -IDE Hintergrund<br />-Menü- und Befehlsleiste Trennzeichen<br />-Rahmen Befehl<br />-Shadows Menü<br />-Tool Registerkarte Standard und Hover Fensterrahmens und Trennzeichen<br />-Dokument auch Überlauf Schaltflächenhintergrund<br />-Dock Ziel Glyphe Rahmen |
| ControlDarkDark |-Ohne Fokus, ausgewählte Registerkarte Dokumentfenster |
| ControlLight |-Automatisch ausgeblendete Registerkarte Rahmen<br />-Kombinationsfeld Feld und dem Dropdown Listenrahmen<br />-Ziel Hintergrund und Andocken |
| ControlLightLight | -Der ausgewählte, mit Fokus vorläufigen Rahmen |
| ControlText | -Symbol für Kombinationsfeld Feld und dem Dropdown Liste<br />-Tool-Fenster, die nicht ausgewählten Registerkartentext |
| GrayText |-Kombinationsfeld und ein Dropdown-Liste deaktiviert, Rahmen, Dropdown-Symbol, Text und Menüelementtext<br />– Deaktivierter Menütext<br />-Suchen Steuerelements "Suchoptionen" HeaderText<br />-Suchen Steuerelements Abschnittstrennzeichen |
| Hervorheben | -Alle Hover und gedrückten Hintergründe und Rahmen, mit Ausnahme von Kombinationsfeld Feld Dropdown-Schaltfläche im Hintergrund und Dokument gut Überlauf Schaltflächenrahmen<br />-Der ausgewählte Element Hintergründe |
| HighlightText | -Alle Hover und gedrückt Vordergrund (Text und Symbole)<br />-Fokussierte Tool Fenster- und Registerkarte Steuerelement Vordergrund<br />-Fokussierte Tool Fensterrahmen der Titelleiste<br />-Vordergrund fokussierten, ausgewählten provisorischen Registerkarte<br />-Dokument gut Überlauf Schaltflächenrahmen auf, wenn darauf gezeigt wird, und drücken Sie<br />-Der ausgewählte Symbolrahmen|
| HotTrack | -Bildlaufleiste Thumb-Hintergrund und drücken<br />-Pfeilsymbol, das auf der Bildlaufleiste |
| InactiveCaption | -Inaktive IDE "und" rafted Fenster Schaltfläche Symbole, wenn darauf gezeigt wird<br />-Befehlsleisten-Hintergrund für die IDE und rafted Windows Titel<br />-Hintergrund deaktivierte suchen-Steuerelements |
| InactiveCaptionText | -IDE inaktiv und rafted Windows Titel Leiste Vordergrund (Text und Symbole)<br />-Schaltflächen-Hintergrund inaktiven Fensters und wenn darauf gezeigt wird<br />-Ohne Fokus Toolfenster – Schaltflächenhintergrund und Rahmen<br />– Deaktivierter Suche Steuerelement Vordergrund |
| Menü | -Dropdown-im Menühintergrund<br />-Aktivierte und deaktivierte häkchenhintergrund |
| MenuText | -Dropdown-Menü "Rahmen"<br />-Häkchen<br />-Menü Symbole<br />-Text Dropdown-Menüs<br />-Der ausgewählte Symbolrahmen |  
| Bildlaufleiste | -Bildlauf Balken- und Pfeil Hintergrund, alle Bundesstaaten auf der Bildlaufleiste an |
| Fenster | -Registerkarte "-Hintergrund automatisch im Hintergrund<br />-Menü Leiste und jeder Befehl Regal-Hintergrund<br />-Ohne Fokus oder nicht ausgewählte Dokument Fenster Registerkarte Hintergrund und Dokumentrahmen für offene und vorläufige Registerkarten<br />-Ohne Fokus Tool Fenster Hintergrund der Titelleiste<br />-Tool-Fenster Registerkarte Hintergrund sowohl aktiviert und deaktiviert |
| WindowFrame | -IDE Rahmens |
| WindowText | -Die Registerkarte Vordergrund automatisch im Hintergrund<br />-Registerkarte "Vordergrund ausgewählte tool<br />-Ohne Fokus Dokumentregisterkarte für Fenster und provisorischen Registerkarte ohne Fokus oder nicht ausgewählten Vordergrund<br />-Struktur anzeigen standardmäßige Vordergrund- und Hover über nicht markierte Symbol<br />-Toolfenster ausgewählter Registerkarte Rahmen<br />-Der Bildlaufleiste Thumb-Hintergrund, Rahmen und Glyphe |
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a>Verfügbarmachen von Farben für Endbenutzer  
  
### <a name="overview"></a>Übersicht  
In einigen Fällen möchten Sie den Endbenutzern die Benutzeroberfläche wie anpassen, wenn Sie eine Code-Editor und der Entwurfsoberfläche erstellen erlauben. Die gängigste Methode hierfür ist die Verwendung der **Tools &gt; Optionen** Dialogfeld. Es sei denn, Sie hoch UI, die spezielle Steuerelemente erforderlich sind spezielle, ist die einfachste Möglichkeit zum Darstellen der anpassungs über die **Schriftarten und Farben** Seite innerhalb der **Umgebung** Abschnitt des Dialogfelds. Für jedes Element, das Sie für die Anpassung verfügbar machen, kann der Benutzer auswählen, so ändern Sie die Vordergrundfarbe, Hintergrundfarbe oder beides.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Erstellen eine VSPackage für die anpassbare Farben  
Eine VSPackage kann steuern, Schriftarten und Farben durch benutzerdefinierte Kategorien und Einblenden von Elementen auf der Eigenschaftenseite Schriftarten und Farben. VSPackages müssen implementieren, wenn Sie diesen Mechanismus verwenden, die [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) Schnittstelle und die zugehörigen Schnittstellen.  
  
Im Prinzip kann diesen Mechanismus verwendet werden, so ändern Sie alle vorhandenen Anzeigeelementen und die Kategorien, die sie enthalten. Allerdings sollten sie nicht verwendet werden, die Text-Editor-Kategorie oder ihre Anzeigeelemente zu ändern. Weitere Informationen zu den Text-Editor-Kategorie, finden Sie unter [Schriftart und Farbe (Übersicht)](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
Zum Implementieren benutzerdefinierter Kategorien oder Elemente anzeigen, müssen eine VSPackage ein:  
  
-   **Erstellen Sie oder identifizieren Sie der Kategorien in der Registrierung.** Die IDE-Implementierung von der **Schriftarten und Farben** Eigenschaftenseite anhand dieser Informationen ordnungsgemäß für die Unterstützung einer bestimmten Kategorie Dienst abzufragen.  
  
-   **Erstellen Sie oder identifizieren Sie Gruppen in der Registrierung (optional).** Es ist möglicherweise nützlich zum Definieren einer Gruppe, die die Vereinigung der zwei oder mehrere Kategorien darstellt. Wenn eine Gruppe definiert ist, wird die IDE automatisch Unterkategorien zusammengeführt und verteilt die Elemente innerhalb der Gruppe anzeigen.  
  
-   **Implementieren Sie IDE-Unterstützung.**  
  
-   **Behandeln Sie Schriftart- und farbänderungen an.**  
  
#### <a name="to-create-or-identify-categories"></a>Zum Erstellen oder Identifizieren von Kategorien  
Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrags unter `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` , in denen `<Category>` der nicht lokalisierte Name der Kategorie.
  
Füllen Sie die Registrierung mit zwei Werten:  

| Name | Typ | Daten | Beschreibung |
| --- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Eine GUID erstellt, um die Kategorie zu identifizieren. |
| Package | REG_SZ | GUID | Die GUID des VSPackage-Diensts, der die Kategorie unterstützt. |
  
 Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) für die entsprechende Kategorie.  
  
#### <a name="to-create-or-identify-groups"></a>Zum Erstellen oder identifizieren Gruppen  
Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrags unter `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` , in denen `<group>` der nicht lokalisierte Name der Gruppe.  
  
Füllen Sie die Registrierung mit zwei Werten:

| Name | Typ | Daten | Beschreibung |
|--- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Eine GUID erstellt, um die Kategorie zu identifizieren. |
| Package | REG_SZ | GUID | Die GUID des VSPackage-Diensts, der die Kategorie unterstützt. |
  
Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` für die entsprechende Gruppe.

![Implementierung von ivsfontandcolorgroup-Schnittstelle](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementierung von`IVsFontAndColorGroup`
  
### <a name="to-implement-ide-support"></a>IDE-Unterstützung implementieren  
Implementieren [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), womit entweder ein [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) Schnittstelle oder eine `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` Schnittstelle für die IDE für die einzelnen Kategorien oder eine Gruppe von angegebenen GUID.  
  
Für jede Kategorie unterstützt eine VSPackage implementiert eine separate Instanz von der [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) Schnittstelle.  
  
Die Methoden implementiert, über [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) müssen die IDE mit bereitstellen:  
  
-   Listen der Elemente in der Kategorie anzeigen  
  
-   Lokalisierbare Namen für Anzeigeelemente  
  
-   Anzeigen von Informationen für jedes Element der Kategorie  
  
 > **Hinweis:** jede Kategorie muss mindestens eine Anzeigeelement enthalten.
  
Die IDE verwendet die `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` Schnittstelle, um eine Union von verschiedene Kategorien definieren.

Die Implementierung stellt die IDE mit:

-   Eine Liste der Kategorien, die einer bestimmten Gruppe bilden  
  
-   Zugriff auf Instanzen von [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) unterstützen jede Kategorie innerhalb der Gruppe "  
  
-   Lokalisierbare Gruppennamen  
  
#### <a name="updating-the-ide"></a>Aktualisieren der IDE  
Die IDE werden Informationen zu den Schriftart-und Farbeinstellungen zwischengespeichert. Also nach jeder Änderung der Konfiguration IDE Schriftart und Farbe, sicherstellen, dass der Cache auf dem neuesten Stand ist eine bewährte Methode.  
  
Aktualisieren des Caches erfolgt über die [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) -Schnittstelle und ausgeführten global oder nur auf ausgewählten Elemente werden können.  
  
### <a name="handling-font-and-color-changes"></a>Behandlung von Schriftart- und farbänderungen an  
Um die farbliche Kennzeichnung von Text ordnungsgemäß zu unterstützen, die eine VSPackage anzeigt, muss die farbliche Kennzeichnung Dienst unterstützen das VSPackage, über die Seite "Schriftarten und Farben Eigenschaften" vorgenommenen Änderungen Benutzerinitiierte reagieren.  
  
Zu diesem Zweck müssen eine VSPackage ein:  
  
-   **IDE-Ereignisse behandeln** durch Implementieren der [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) Schnittstelle. Die IDE Ruft die entsprechende Methode, die folgenden Änderungen durch den Benutzer der Seite "Schriftarten und Farben". Beispielsweise ruft der [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) Methode, wenn eine neue Schriftart ausgewählt ist.  
  
 **OR**  
  
-   **Abrufen die IDE Änderungen**. Dies kann erfolgen über die vom System implementierte [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) Schnittstelle. Obwohl in erster Linie für die Unterstützung von Persistenz, die [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) Methode Informationen erhalten Sie Schriftart und Farbe für Elemente anzeigen. Weitere Informationen zu Schriftart und Farbe Einstellungen finden Sie im MSDN-Artikel [Zugriff auf gespeicherte Schriftart und Farbe Einstellungen](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
> **Hinweis:** verwenden, um sicherzustellen, dass die der Abfrageergebnisse richtig sind, die [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) Schnittstelle, um zu bestimmen, ob ein Cache leeren und Update benötigt werden, vor dem Aufrufen der Abrufmethoden, der die [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) Schnittstelle.
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrieren benutzerdefinierte Schriftart und Farbe Kategorie ohne Implementieren von Schnittstellen  
Im folgenden Codebeispiel wird veranschaulicht, wie zum Registrieren der benutzerdefinierten Schriftart und Farbe Kategorie ohne Schnittstellen zu implementieren:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  

Für dieses Codebeispiel:   
-   `"NameID"` die Ressourcen-ID, der Namen der lokalisierten Kategorie im Paket =
-   `"ToolWindowPackage"` = Paket-GUID
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`ist nur ein Beispiel, und der tatsächliche Wert kann eine neue GUID, die von der Implementierung bereitgestellt werden.  
  
### <a name="set-the-font-and-color-property-category-guid"></a>Legen Sie die Schriftart und Farbe Eigenschaftskategorie-GUID  
Das folgende Codebeispiel veranschaulicht das Festlegen der Category-GUIDs.  
  
```  
// m_pView is your IVsTextView  
IVsTextEditorPropertyCategoryContainer spPropCatContainer =  
(IVsTextEditorPropertyCategoryContainer)m_pView;  
if (spPropCatContainer != null)  
{  
IVsTextEditorPropertyContainer spPropContainer;  
Guid GUID_EditPropCategory_View_MasterSettings =  
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");  
hr = spPropCatContainer.GetPropertyCategory(  
ref GUID_EditPropCategory_View_MasterSettings,  
out spPropContainer);  
if(hr == 0)  
{  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,  
catGUID);  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,  
catGUID);  
}  
}  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a>Daytona und Web-Benutzeroberfläche  
  
### <a name="overview"></a>Übersicht  
"Daytona" ist ein Satz von APIs, Tools und Diensten, mit denen einen Benutzer zum Erstellen von Plug-Ins mit HTML, CSS und JavaScript, die in einer Vielzahl von Hosts, z. B. Visual Studio oder F12 verwendet werden kann. -Plug-Ins bestehen aus einer portablen-Komponente, die in HTML, CSS und JavaScript geschrieben ist, und optionale hostspezifische-Komponenten. Jeder Daytona-Host kann einen eigenen Satz von UI-Konventionen, entweder implizit oder explizit, die ein Plug-in entsprechen muss, um systemeigene in ihrer Umgebung angezeigt, besitzen. Einige der Hosts, z. B. Visual Studio können Endbenutzer "Standarddesign" ändern, damit der Host visuellen Aspekte statisch nicht als Ziel verwendet werden beim Erstellen eines Stylesheets. Dies stellt eine Herausforderung für Entwickler, die portablen-Plug-Ins erstellen. In diesem Thema wird erläutert, wie zum Erstellen von Web-Benutzeroberfläche in Visual Studio mit dem Host Daytona auf eine Weise, die die Designs und hoher Kontrast ordnungsgemäß unterstützt wird.  
  
### <a name="daytona-theming-mechanism"></a>Daytona Designumgebung Mechanismus  
Die Daytona-Laufzeit bietet eine Reihe von Diensten, die die UI-Konventionen abstrahiert und Designumgebung Funktionen des Hosts. Diese Dienste stellen Sie sicher, dass Plug-Ins entsprechen automatisch die visuellen Erwartungen der Benutzer auf Grundlage der Umgebung, in dem sie gehostet werden. Dieses Verhalten wird von drei primäre Funktionen bereitgestellt:  
  
1.  Eine Laufzeit eingefügter Stylesheet (plugin.css), die transparent wendet eine Menge von CSS-Regeln auf ein Plug-in-Benutzeroberfläche und die Formatvorlagen des Standardsatz von HTML-Steuerelemente (z. B. HTMLInputElement und HTMLButtonElement  
  
2.  Einen Satz von Host bereitgestellte Token, die zum Stil Benutzeroberflächenelemente, die mit Werten, die anstelle von hartcodierten Design-basiert sind verwendet werden kann  
  
    -  eine deklarative Syntax für den Zugriff auf diese Token mit CSS  
  
    -  eine API für den programmgesteuerten Zugriff auf Design-Token aus JavaScript  
  
3.  Bekanntgabe Designänderungen  
  
#### <a name="runtime-injected-style-sheet"></a>Common Language Runtime eingefügter Stylesheet  
Die Common Language Runtime Koordinaten Daytona, mit dem Host einen Stil einfügen Blatt, automatisch Designs standard Benutzeroberflächenelemente eines Plug-Ins. Dazu gehören auch formatieren, Informationen zu den folgenden Konzepten:  
  
-   Umgebungsschriftart  
  
-   Hintergrundfarben  
  
-   Links  
  
-   Formular Steuerelemente (z. B.: `<select>`, `<input>`,`<button>`  
  
-   Tabellen  
  
-   Kopfzeilen  
  
-   Bildlaufleisten  
  
Dies bedeutet, dass wenn Ihre Benutzeroberfläche vollständig aus HTML-UI-Standardsteuerelemente besteht, klicken Sie dann ohne zusätzliche Arbeit ordnungsgemäß auf Designänderungen reagieren und zur Unterstützung von hoher Kontrast benötigt werden sollte.  
  
#### <a name="custom-ui"></a>Benutzerdefinierte Benutzeroberfläche  
In nahezu jedem Fall nicht trivialen der Standard-HTML-UI steuert nicht ausreichend für eine umfassende Erfahrung für ein Plug-in bereitstellen und benutzerdefinierte Benutzeroberfläche eingeleitet werden muss. Um die richtige Schriftart Auswahl und die Farbe verwenden, unterstützen **Design Token** sollte verwendet werden, entweder deklarativ in CSS oder imperativ über die JavaScript-API, die im folgenden beschrieben. Die Laufzeit Daytona übernimmt aktualisieren die Stylesheets, die diese Token auf der Auslastungstest-Plug-in und Design ändert.  
  
##### <a name="theme-tokens"></a>Design-Token  
Beide standard und hostspezifische Design-Token sind verfügbar. Standardtokens sind Host eingefügter und immer verfügbar. Verwenden die standard-Token aus, wann immer möglich ist vorzuziehen. Standard-Token ist sichergestellt, dass von allen Daytona Hosts bereitgestellt werden, und deren Verwendung Ihr Plug-in ist grundsätzlich besser portierbar. Der Satz von Standardtokens unterliegt, obwohl nur neue Token hinzugefügt werden sollen und keine entfernt werden soll. Die Visual Studio 2013-Version wird im folgenden dokumentiert:  
  
| Tokenname | Beschreibung |
| --- | --- |
| `plugin-background-color` | Die Standardhintergrundfarbe für das Plug-in |
| `plugin-color` | Die Standardvordergrundfarbe für das Plug-in |
| `plugin-contextmenu-active-color` | Die Auswahl Standardvordergrundfarbe für Kontextmenüs, wenn sie aktiv sind (markiert sein) |
| `plugin-contextmenu-background-color` | Die Standardhintergrundfarbe für Kontextmenüs |
| `plugin-contextmenu-border-color` | Die Standardrahmenfarbe für Kontextmenüs |
| `plugin-contextmenu-color` | Die Standardvordergrundfarbe für Kontextmenüs |
| `plugin-contextmenu-hover-color` | Die Standardhintergrundfarbe für Kontextmenüs, das gezeigt wird |
| `plugin-contextmenu-hover-text-color` | Die Standardvordergrundfarbe für Kontextmenüs, das gezeigt wird |
| `plugin-contextmenu-icon-checkbox` | Kontrollkästchen Symbol Standardfarbe für die Kontextmenüs |
| `plugin-contextmenu-inactive-text-color` | Die Auswahl Standardvordergrundfarbe für Kontextmenüs, wenn sie inaktiv sind |
| `plugin-contextmenu-separator-color` | Die Standardfarbe für Trennzeichen für Kontextmenüs |
| `plugin-font-family` | Die Standardschriftfamilie für das Plug-in verwendet |
  
In Visual Studio die folgenden `plugin-font` Token basieren auf die schriftarteinstellungen für die Umgebung:  
  
-   `plugin-font-size`  
  
-   `plugin-font-weight`  
  
-   `plugin-highlight-background-color`  
  
-   `plugin-highlight-color`  
  
-   `plugin-inactive-color` 
  
Die folgenden `plugin-link` Token werden verwendet, um den Stil `HTMLElements` (links):
  
-   `plugin-link-color`  
  
-   `plugin-link-active-color`  
  
-   `plugin-link-hover-color`  
  
Plugin.CSS Formatvorlagen Bildlaufleisten standardmäßig mithilfe der folgenden Tokens, um besser zu unterstützen, die Designs in den verschiedenen Hosts (insbesondere Visual Studio):
  
-   `plugin-scrollbar-arrow-color`  
  
-   `plugin-scrollbar-background-color`  
  
-   `plugin-scrollbar-face-color`  
  
Die folgenden `plugin-select` Token werden verwendet, um den Stil der `HTMLSelectElement` (klicken Sie im Dropdown-Kombinationsfeld):  
  
-   `plugin-select-option-background-color` 
  
-   `plugin-select-option-color`  
  
-   `plugin-select-option-checked-background-color`  
  
-   `plugin-select-option-checked-border-color`  
  
-   `plugin-select-option-checked-foreground-color`  
  
-   `plugin-select-option-hover-background-color`  
  
-   `plugin-select-option-hover-border-color`  
  
-   `plugin-select-option-hover-foreground-color`  
  
-   `plugin-select-border-color`  
  
-   `plugin-select-background-color`  
  
-   `plugin-select-foreground-color`  
  
-   `plugin-select-hover-background-color`  
  
-   `plugin-select-hover-border-color`  
  
-   `plugin-select-hover-foreground-color`  
  
-   `plugin-table-border-color`  
  
-   `plugin-table-header-background-color`  
  
-   `plugin-table-header-color`  
  
-   `plugin-textbox-border-color`  
  
-   `plugin-textbox-background-color`  
  
-   `plugin-textbox-color`  
  
-   `plugin-textbox-disabled-background-color`  
  
-   `plugin-textbox-disabled-border-color`  
  
-   `plugin-textbox-disabled-color`  
  
Diese Token sollte verwendet werden, für die *alle* Struktur Systemsichten und-Tabellen, da sie die richtigen Standardwerte in den verschiedenen Hosts zur Unterstützung von Designs und hoher Kontrast festgelegt haben:  
  
-   `plugin-treeview-content-background-color`  
  
-   `plugin-treeview-content-color` 
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-mouseover-background-color`  
  
-   `plugin-treeview-content-mouseover-color`  
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-selected-background-color`  
  
-   `plugin-treeview-content-selected-border-color`  
  
-   `plugin-treeview-content-selected-color`  
  
##### <a name="host-specific-tokens"></a>Hostspezifische-Token  
Zusätzlich zur Unterstützung von des Standardsatz von Token, können Hosts auch nicht dem Standard entsprechende Token enthalten. Der Visual Studio-Host wird ermöglicht das Plug-in Design token Aliase in einem Visual Studio-spezifischen Abschnitt des Manifests an. Zum Beispiel:
  
```  
"vs": {  
    "theme_token_aliases": {   
        "diagnostics-host-border": {   
            "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22",   
            "key_type": "BackgroundColor",   
            "name": "Border"   
        },   
        ...   
    }   
}    
```  
  
 In diesem Beispiel führt ein Design-Token mit dem Namen `diagnostics-host-border`, die kann auf die oben genannten Standardtokens identisch verwiesen werden. Die `category`, `key_type`, und `name` werden verwendet, um die Farbe über Auflösen der `IVsFontAndColorStorage` Schnittstelle. In vielen Fällen ist es möglich, finden entsprechende Farben (zusammen mit den `category`, `key_type`, und `name` Informationen) in der XML-Dateien im `VSCommonContent\themes`. Denselben Mechanismus wird verwendet, wenn Ihr Paket neue konfigurierbare Farben eingeführt: entsprechen der `category`, `key_type`, und `name` die Farbe, die Sie verwenden möchten. Plug-in-Autoren sollten versuchen, nach Möglichkeit Standardtokens zu verwenden und nur verwenden hostspezifische-Token, wenn dies absolut notwendig.  
  
##### <a name="using-theme-tokens-in-css"></a>Verwenden von Design-Token in CSS  
 Design-Token werden über eine speziell formatierte Kommentarsyntax bezeichnet. Die Regeln für die Analyse von token:  
  
1.  Der Kommentarausdruck muss in eckige Klammern eingeschlossen werden (`[ ]`).  
  
2.  Alle Leerzeichen innerhalb des Kommentars, jedoch außerhalb der Ausdruck wird ignoriert.  
  
3.  Der Kommentarausdruck muss direkt führen Sie die Eigenschaft, die es ersetzt.  
  
4.  Führenden oder nachgestellten Leerzeichen innerhalb des Ausdrucks wird gekürzt werden.  
  
5.  Jedes token-Namen innerhalb des Ausdrucks muss in geschweifte Klammern eingeschlossen werden (z. B. `{font-family}` und `{button-hover-color}`). Andernfalls wird er als Literalwert behandelt.  
  
 Im folgenden sind Beispiele für wie der token-Parser CSS-Werten, vorausgesetzt, dass ersetzen, wird die `plugin-background-color` Token hat den Wert der `#000` und die `plugin-font-family` Token hat den Wert des `Verdana`.
  
| Erstellte CSS | Analysierte CSS | Notizen |  
| --- | --- | --- |
| `background-color: #fff; /*[{plugin-background-color}]*/` | `background-color: #000;` | Der Standardwert wird durch die dynamische hostspezifische Wert ersetzt. |  
| `background-color: #fff; /*   [{plugin-background-color}]   */` | `background-color: #000;` | Den Leerraum außerhalb des Ausdrucks wird ignoriert. |  
| `background-color: #fff; /*[   {plugin-background-color}   ]*/` | `background-color: #000;` | Die, führende und nachfolgende Leerzeichen innerhalb des Ausdrucks werden entfernt. |
| `background-color: #fff; /*{plugin-background-color}*/` | `background-color: #fff;` | Dieser Ausdruck wird nicht in eckige Klammern eingeschlossen, und der Kommentar wird daher ignoriert. |
| `background-color: #fff; /*[plugin-background-color]*/` | `background-color: plugin-background-color;` | Das Token ist nicht in der geschweiften Klammern eingeschlossen und wird daher als Literalwert behandelt. |
| `/*[{plugin-background-color}]*/ background-color: #fff;` | `background-color: #fff;` | Der Kommentar folgt nicht den Wert der Eigenschaft und wird daher ignoriert. |
| `background-color: #fff;  /*[{plugin-background-color}]*/` | `background-color: #fff;`| *Wie oben* |
| `/*[{plugin-background-color}]*/  background-color: #fff;` | `background-color: #fff;` | *Wie oben* |
| `font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/` | `font-family: Verdana, sans-serif;` | Das Token ersetzt, und die Literale Inhalt verwaltet wird. |
| `background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/` | `background-image: linear-gradient(0% #000, 100% #000);` | *Wie oben* |
  
Eine CSS-Datei enthält das Design Token müssen sie durch markiert die `data-plugin-theme` -Attribut auf die `link` Element in der HTML-Datei. Zum Beispiel:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```

##### <a name="using-theme-tokens-from-javascript"></a>Verwenden von Design-Token aus JavaScript  
Während der benutzerdefinierten Benutzeroberfläche von CSS Designs, sofern möglich sein soll, gibt es Szenarien, wenn der Wert eines Designs token muss programmgesteuert zugegriffen werden. Wenn benutzerdefinierte Benutzeroberfläche auf gezeichnet wird z. B. eine `CanvasElement` , die vom Kundendienst Styling erbt nicht, oder wenn ein Element der Benutzeroberfläche wird dem verweisen auf Stylesheets Gegensatz als dynamisch erstellt wird. Die Szenarien werden mithilfe der API Daytona aktiviert `Plugin.Theme.getValue`. Diese Funktion gibt einen Host bereitgestellte Designwert, wenn token benannt.  
  
| Nicht Designs | Designs |
| --- | --- |
| `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = "#ccc";  surface.fillRect(0, 0, 200, 200);` | `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = ("plugin-background-color");  surface.fillRect(0, 0, 200, 200);` |
| `var el = document.createElement("div");  el.style.backgroundColor = "#ccc";` | `var el = document.createElement("div");  el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");` |  
  
Wenn Token, aus JavaScript verwendet werden **das Änderungsereignis Design muss zum Reagieren auf Updates behandelt werden**. Dies ist nicht erforderlich, für Design-Token, das deklarativ in CSS verwendet, wie die Runtime Daytona es für das Plug-in übernimmt. Das Design-Ereignis kann auf folgende Weise behandelt werden:

**Member (einzelner Handler)**
```
Plugin.Theme.onchange = function () 
{
    // re-draw dynamic UI here
}
```

**DOM-Ereignis (mehrere Handler)**
```
Plugin.Theme.addEventListener("change", function () 
{
    // re-draw dynamic UI here
});
```
  
In diesem Fall wäre es üblich, rufen Sie erneut `Plugin.Theme.getValue` in diese Handler, als der Wert der Design-Token auf, die wahrscheinlich beim Ändern des Designs geändert wurde.  
  
##### <a name="standard-token-mapping"></a>Standard-token-Zuordnung  
Die standard-Token werden Umgebung, und Shell Farben zugeordnet. Die nachfolgenden Liste bietet eine Art von was diese Zuordnungen sind.  
  
| Tokenname | Zuordnen von VS (`EnvironmentColors`) |  
| --- | --- |  
| `plugin-color` | `ToolWindowTextColorKey` |
| `plugin-background-color` | `ToolWindowBackgroundColorKey` |
| `plugin-link-color` | `ControlLinkTextColorKey` |
| `plugin-link-hover-color` | `ControlLinkTextHoverColorKey` |
| `plugin-link-active-color` | `ControlLinkTextPressedColorKey` |
| `plugin-highlight-color` | `HighlightTextColorKey` |
| `plugin-highlight-background-color` | `HighlightColorKey` |
| `plugin-table-header-background-color` | `GridHeadingBackgroundColorKey` |
| `plugin-table-header-color` | `GridHeadingTextColorKey` |
| `plugin-table-border-color` | `GridLineColorKey` |
| `plugin-button-background-color` | `ButtonFaceColorKey` |
| `plugin-button-hover-background-color` | `ButtonHighlightColorKey` | 
| `plugin-button-color` | `ButtonTextColorKey` |
| `plugin-button-border-color` | `ButtonBorderColorKey` |
  
##### <a name="theme-changes"></a>Designänderungen  
Der Visual Studio-Host Trigger-Plug-Ins Design ändert, wenn ein Endbenutzer werden Änderungen an den folgenden Einstellungen:  
  
**Farbschema:**  
  
![Farbe, Designänderungen](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305-a_ColorTheme")<br />Farbe, Designänderungen  
  
**Design der Umgebung:**  
  
![Umgebung, Designänderungen](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305-b_EnvironmentTheme")<br />Umgebung, Designänderungen  
  
**Betriebssystem-Design** (nur bei zu und von hoher Kontrast zu ändern):  
  
![Betriebssystem-Designänderungen](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305-c_OSTheme")<br />Betriebssystem-Designänderungen
