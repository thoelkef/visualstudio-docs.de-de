---
title: "Farben und Styling für Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 07/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40e795238e46885707cfd6eff715a27a5f53f85c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
  
### <a name="visual-studio-themes"></a>Visual Studio-Designs  
Visual Studio bietet drei verschiedene Farbschemas, statusleisteneinstellungen: hell, dunkel und Blau. Außerdem wird erkannt, Modus für hohe Kontraste, die eine systemweite Farbschema für Eingabehilfen konzipiert ist.  
  
Benutzer werden aufgefordert, ein Design auswählen, während der ersten Verwendung von Visual Studio und Designs später zu wechseln, indem Sie möchten, können **Tools &gt; Optionen &gt; Umgebung &gt; allgemeine** und wählen Sie ein neues Design aus das Dropdownmenü "Farbschema" aus.  
  
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
  
![Tools &gt; Dialogfeld "Optionen"](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 A_ToolsOptionsDialog")<br />Tools &gt; Dialogfeld "Optionen"
  
##  <a name="BKMK_TheVSColorService"></a>Der Dienst VSColor  
Visual Studio bietet einen Umgebung Farbe Dienst auch den VSColor-Dienst oder der Shell Farbe-Dienst genannt. Dieser Dienst ermöglicht Ihnen, das die Farbwerte anzeigt, der die Elemente der Benutzeroberfläche an Name / Wert-Farben, die Farben für jedes Design enthält binden. Der VSColor-Dienst muss für alle Elemente der Benutzeroberfläche verwendet werden, sodass Farben automatisch entsprechend das aktuelle Benutzer ausgewählten Design ändern und, damit zum Dienst Farbe Umgebung Benutzeroberfläche gebunden neue Designs in zukünftigen Versionen von Visual Studio integriert werden.  
  
### <a name="how-the-service-works"></a>Funktionsweise des Diensts  
Die Umgebung Farbe Dienst liest VSColors in der PKGDEF für die UI-Komponente definiert. Diese VSColors klicken Sie dann im XAML-Markup oder-Code referenziert werden und werden geladen, entweder über die `IVsUIShell5.GetThemedColor` oder ein `DynamicResource` Zuordnung.  
  
![Umgebungsfarbe – Dienstarchitektur](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 A_EnvironmentColorServiceArchitecture")<br />Umgebungsfarbe – Dienstarchitektur
  
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
  
![Beispiel mit Details wie feine sind verlorene Bestätigungen hohem Kontrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 A_PropertiesWindow")<br />Beispiel mit Details wie feine sind verlorene Bestätigungen in hoher Kontrast
  
#### <a name="choosing-text-colors-in-an-editor"></a>Auswählen von Textfarben in einem editor  
Farbdruckoption Text wird in einem Editor oder auf einer Entwurfsoberfläche verwendet, um anzugeben, d. h., wie das Zulassen der für die einfache Identifikation von Gruppen mit ähnlichen Elementen. In einem Design "hoher Kontrast" jedoch müssen nicht die Möglichkeit der Unterscheidung zwischen mehr als drei Textfarben Sie. WindowText, GrayText und HotTrackText sind der einzigen Farben auf WindowBackground Flächen. Da Sie mehr als drei Farben verwenden können, sorgfältig wählen Sie die wichtigsten Unterschiede, die im Modus für hohe Kontraste angezeigt werden soll.  
  
Farbtöne für jede von den Tokennamen zulässig in einem Editor angezeigt, wie sie in jeder Design mit hohem Kontrast angezeigt werden:  
  
![Hoher Kontrast Editor Vergleich](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 B_HCEditorComparison")<br />Editor im Design "Hoher Kontrast", Vergleich
  
Beispiele für die Editor-Entwurfsoberfläche in das Design "Blau":  
  
![Editor im Design "Blau"](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 C_EditorBlue")<br />Editor im Design "Blau"
  
![Editor im Design "hoher Kontrast #1"](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Editor im Design "hoher Kontrast #1"
  
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
| Hervorheben | -Alle Hover und gedrückten Hintergründe und Rahmen, mit Ausnahme von Kombinationsfeld klicken Sie im Dropdown-Schaltfläche im Hintergrund und Dokument gut Überlauf Schaltflächenrahmen<br />-Der ausgewählte Element Hintergründe |
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
  
Im Prinzip kann diesen Mechanismus verwendet werden, so ändern Sie alle vorhandenen Anzeigeelementen und die Kategorien, die sie enthalten. Allerdings sollten sie nicht verwendet werden, die Text-Editor-Kategorie oder ihre Anzeigeelemente zu ändern. Weitere Informationen zu den Text-Editor-Kategorie, finden Sie unter [Schriftart und Farbe (Übersicht)](../font-and-color-overview.md).  
  
Zum Implementieren benutzerdefinierter Kategorien oder Elemente anzeigen, müssen eine VSPackage ein:  
  
-   **Erstellen Sie oder identifizieren Sie der Kategorien in der Registrierung.** Die IDE-Implementierung von der **Schriftarten und Farben** Eigenschaftenseite anhand dieser Informationen ordnungsgemäß für die Unterstützung einer bestimmten Kategorie Dienst abzufragen.  
  
-   **Erstellen Sie oder identifizieren Sie Gruppen in der Registrierung (optional).** Es ist möglicherweise nützlich zum Definieren einer Gruppe, die die Vereinigung der zwei oder mehrere Kategorien darstellt. Wenn eine Gruppe definiert ist, wird die IDE automatisch Unterkategorien zusammengeführt und verteilt die Elemente innerhalb der Gruppe anzeigen.  
  
-   **Implementieren Sie IDE-Unterstützung.**  
  
-   **Behandeln Sie Schriftart- und farbänderungen an.**  
  
#### <a name="to-create-or-identify-categories"></a>Zum Erstellen oder Identifizieren von Kategorien  
Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrags unter `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` , in denen `<Category>` der nicht lokalisierte Name der Kategorie.
  
Füllen Sie die Registrierung mit zwei Werten:  

| name | Typ | Daten | Beschreibung |
| --- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Eine GUID erstellt, um die Kategorie zu identifizieren. |
| Package | REG_SZ | GUID | Die GUID des VSPackage-Diensts, der die Kategorie unterstützt. |
  
 Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) für die entsprechende Kategorie.  
  
#### <a name="to-create-or-identify-groups"></a>Zum Erstellen oder identifizieren Gruppen  
Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrags unter `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` , in denen `<group>` der nicht lokalisierte Name der Gruppe.  
  
Füllen Sie die Registrierung mit zwei Werten:

| name | Typ | Daten | Beschreibung |
|--- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Eine GUID erstellt, um die Kategorie zu identifizieren. |
| Package | REG_SZ | GUID | Die GUID des VSPackage-Diensts, der die Kategorie unterstützt. |
  
Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` für die entsprechende Gruppe.

![Implementierung von ivsfontandcolorgroup-Schnittstelle](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 A_FontAndColorGroup")<br />Implementierung von`IVsFontAndColorGroup`
  
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
  
-   **Abrufen die IDE Änderungen**. Dies kann erfolgen über die vom System implementierte [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) Schnittstelle. Obwohl in erster Linie für die Unterstützung von Persistenz, die [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) Methode Informationen erhalten Sie Schriftart und Farbe für Elemente anzeigen. Weitere Informationen zu Schriftart und Farbe Einstellungen finden Sie im MSDN-Artikel [Zugriff auf gespeicherte Schriftart und Farbe Einstellungen](../accessing-stored-font-and-color-settings.md).  
  
> **Hinweis:** verwenden, um sicherzustellen, dass die der Abfrageergebnisse richtig sind, die [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) Schnittstelle, um zu bestimmen, ob ein Cache leeren und Update benötigt werden, vor dem Aufrufen der Abrufmethoden, der die [ IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) Schnittstelle.
  
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
-   `"NameID"`die Ressourcen-ID, der Namen der lokalisierten Kategorie im Paket =
-   `"ToolWindowPackage"`= Paket-GUID
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
