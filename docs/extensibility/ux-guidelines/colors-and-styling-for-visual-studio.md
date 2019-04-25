---
title: Farben und Stile für Visual Studio | Microsoft-Dokumentation
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ba49e1ab3e25e3f22a9ca8642673aa0a62869f6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114768"
---
# <a name="colors-and-styling-for-visual-studio"></a>Farben und Stile für Visual Studio

## <a name="use-color-in-visual-studio"></a>Verwenden von Farbe in Visual Studio

In Visual Studio wird die Farbe in erster Linie als ein Tool für die Kommunikation, nicht nur als Dekoration verwendet. Verwenden Sie die Farbe minimal, und reservieren sie für Situationen, in denen Sie möchten:

- Kommunikation von Bedeutung bzw. den Partner (z. B. Plattform oder Sprache Modifizierer)

- Wecken Sie (z. B., der angibt, einer Änderung des)

- Verbessern Sie Lesbarkeit zu, und geben Sie Orientierungshilfen für die Navigation in der Benutzeroberfläche

- Erhöhen Sie Serverupgrade

Es sind mehrere Optionen zum Zuweisen von Farben für Elemente der Benutzeroberfläche in Visual Studio vorhanden. Manchmal kann es schwierig, in eine Form sein, welche Option Sie aufgefordert werden, verwenden oder wie Sie sie ordnungsgemäß verwenden. In diesem Thema helfen Ihnen:

- Erfahren Sie, die verschiedene Dienste und Systeme, die zum Definieren von Farben in Visual Studio verwendet.

- Wählen Sie die richtige Option für ein angegebenes Element ein.

- Ordnungsgemäß verwenden Sie die Option, die Sie ausgewählt haben.

> [!NOTE]
> Nie hartcodieren Hexadezimal, RGB oder Systemfarben für Ihre UI-Elemente. Nutzung der Dienste ermöglicht Flexibilität bei der Feineinstellung von Hue. Darüber hinaus ohne den Dienst nicht werden nutzen designswitching Funktionen von [der VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Methoden für die Zuweisung von Farben für Elemente der Visual Studio-Benutzeroberfläche

Wählen Sie die Methode, die am besten geeignet ist, um Ihre UI-Elemente.

| Die Benutzeroberfläche | Methode | Was sind sie? |
| --- | --- | --- |
| Sie verfügen über eingebettete oder eigenständige-Dialogfelder. | **Systemfarben** | System-Namen, mit denen das Betriebssystem zum Definieren der Farbe und die Darstellung der Elemente der Benutzeroberfläche, wie allgemeine Dialogfeld-Steuerelemente. |
| Sie haben benutzerdefinierten Benutzeroberfläche, die mit der gesamten Visual Studio-Umgebung konsistent sein sollen, und Sie haben es sich um UI-Elemente, die die Kategorie und die semantische Bedeutung der freigegebenen Token entsprechen. | **Gemeinsam verwendeten Farben** | Vordefinierte Farben Tokennamen für bestimmte Elemente der Benutzeroberfläche |
| Sie haben eine einzelne Funktion oder eine Gruppe von Funktionen und keine gemeinsam genutzten Farben für ähnliche Elemente vorhanden sind. | **Benutzerdefinierte Farben** | Token-Namen von Farben, die spezifisch für einen Bereich und nicht für andere Benutzeroberfläche freigegeben werden sollen |
| Möchten Sie dem Endbenutzer zum Anpassen der Benutzeroberfläche oder Inhalt (z. B. für Text-Editoren oder spezielle Designerfenstern) ermöglichen. | **Durch den Endbenutzer-Anpassung**<br /><br />**(Tools &gt; Dialogfeld "Optionen")** | Einstellungen, die auf der Seite "Schriftarten und Farben" definiert die **Tools &gt; Optionen** Dialogs oder einer speziellen Seite für eine UI-Funktion. |

### <a name="visual-studio-themes"></a>Visual Studio-Designs

Visual Studio verfügt über drei verschiedene Farbschemas: hell, dunkel und Blau. Außerdem wird erkannt, Modus für hohe Kontraste, eine systemweite Farbschema für Eingabehilfen entworfen wird.

Benutzer werden aufgefordert, die bei ihrer ersten Verwendung von Visual Studio ein Design auswählen und können später Designs wechseln, indem Sie zu **Tools &gt; Optionen &gt; Umgebung &gt; allgemeine** und wählen ein neues Design aus das Dropdownmenü "Farbschema" aus.

Benutzer können auch die Systemsteuerung verwenden, um ihre gesamten Systeme in einer von mehreren Designs mit hohem Kontrast zu wechseln. Wenn ein Benutzer ein Design mit hohem Kontrast ausgewählt hat, wirkt sich auf klicken Sie dann die Farbauswahl Design Visual Studio nicht mehr Farben in Visual Studio, jedoch Designänderungen für gespeichert werden, wenn der Benutzer den Modus für hohe Kontraste beendet. Weitere Informationen zu den Modus für hohe Kontraste, finden Sie unter [Farben mit hohem Kontrast auswählen](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Die VSColor service

Visual Studio bietet einen Umgebung Farbe Dienst bekannt, wie der Dienst VSColor, in der Sie die Farbwerte, die Elemente der Benutzeroberfläche an einen benannten Eintrag mit Farbwerten für jedes Visual Studio-Design binden kann. Dadurch wird sichergestellt, dass Sie Farben entsprechend den aktuellen Benutzer ausgewählten Designs oder Modus für hohe Kontraste automatisch geändert werden. Verwendung des Diensts bedeutet, dass die Implementierung aller Farbe mit Design-bezogene Änderungen an einem Ort erfolgt, und wenn Sie gemeinsame verwendeten Farben aus dem Dienst verwenden, wird Ihre Benutzeroberfläche automatisch neuen Designs in zukünftigen Versionen von Visual Studio angewendet.

### <a name="implementation"></a>Implementierung

Der Quellcode für Visual Studio enthält mehrere Paketdefinitionsdateien, die Listen von token-Namen und die Werte der entsprechenden Farbe für jedes Design enthalten. Der Color-Dienst liest die VSColors in diese Paketdefinitionsdateien definiert. Diese Farben werden in XAML-Markup oder Code auf die verwiesen wird und dann geladen wird, entweder durch die `IVsUIShell5.GetThemedColor` Methode oder eine DynamicResource-Zuordnung.

### <a name="system-colors"></a>Systemfarben

Allgemeine Steuerelemente auf die Systemfarben standardmäßig verweisen. Wenn Sie Ihre Benutzeroberfläche mit Systemfarben verwenden, z. B. Wenn Sie eine eingebettete oder eigenständige Dialogfeld erstellen möchten, müssen Sie nichts weiter tun.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Gemeinsam verwendeten Farben im VSColor service

Ihre Benutzeroberflächenelemente sollten die gesamte Visual Studio-Umgebung widerspiegeln. Durch die Wiederverwendung, der gemeinsamen verwendeten Farben, die für die UI-Komponente geeignet sind, die Sie entwerfen, stellen Sie sicher, dass Ihre Benutzeroberfläche mit anderen Schnittstellen für die Visual Studio konsistent ist und dass Sie Farben automatisch aktualisiert werden, wenn Designs hinzugefügt oder aktualisiert werden.

Stellen Sie vor der Verwendung von gemeinsam verwendeten Farben sicher, dass Sie erfahren, wie sie ordnungsgemäß verwenden. Falsche Verwendung von gemeinsam verwendeten Farben kann zu einer inkonsistenten, frustrierend und verwirrend Erfahrung für Ihre Benutzer führen.

### <a name="user-customizable-colors"></a>Benutzer anpassbare Farben

Thema [Verfügbarmachen von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

In einigen Fällen möchten Sie ermöglicht dem Endbenutzer die Benutzeroberfläche, z. B. anpassen, bei der Erstellung einer Code-Editor oder die Entwurfsoberfläche. Anpassbare UI-Komponenten finden Sie in der **Schriftarten und Farben** Teil der **Tools &gt; Optionen** Dialogfeld, in dem Benutzer so ändern Sie die Vordergrundfarbe, Hintergrundfarbe oder beides auswählen können.

![Tools &gt; Dialogfeld "Optionen"](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-A_ToolsOptionsDialog")<br />Tools &gt; Dialogfeld "Optionen"

## <a name="BKMK_TheVSColorService"></a> Die VSColor Service

Visual Studio bietet einen Umgebung Farbe Dienst auch die VSColor Service oder der Color-Shell-Dienst genannt. Dieser Dienst ermöglicht Ihnen, binden die Farbwerte, die Elemente der Benutzeroberfläche in eine Name / Wert-Farbe, die Farben für jedes Design enthält. Die VSColor Service muss für alle Elemente der Benutzeroberfläche verwendet werden, damit Farben automatisch entsprechend der aktuellen vom Benutzer ausgewählten Thema zu ändern und so, dass die Umgebung-Farben-Benutzeroberfläche gebunden mit neuen Designs in zukünftigen Versionen von Visual Studio integriert werden.

### <a name="how-the-service-works"></a>Funktionsweise des Diensts

Die Umgebung-Farben-liest, dass VSColors in der PKGDEF für die UI-Komponente definiert. Diese VSColors klicken Sie dann in XAML-Markup oder Code referenziert werden und werden geladen, entweder durch die `IVsUIShell5.GetThemedColor` oder `DynamicResource` Zuordnung.

![Umgebungsfarbe – Dienstarchitektur](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-A_EnvironmentColorServiceArchitecture")<br />Umgebungsfarbe – Dienstarchitektur

### <a name="accessing-the-service"></a>Zugreifen auf den Dienst

Es gibt mehrere Möglichkeiten, den Zugriff, die die VSColor Service, je nachdem, welche Art von Farbe, die Sie Token verwenden und welche Art von Code haben.

#### <a name="predefined-environment-colors"></a>Vordefinierte Umgebungsfarben

##### <a name="from-native-code"></a>Von nativem code

Die Shell bietet einen Dienst, der Zugriff auf die Aufgabenbereiche der `COLORREF` der Farben. Die Dienstschnittstelle ist:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

In der Datei die Enumeration VSShell80.idl `__VSSYSCOLOREX` Farbkonstanten Shell hat. Um es zu verwenden, übergeben Sie als den Indexwert entweder einen der Werte aus der `enum __VSSYSCOLOREX` dokumentiert in MSDN oder ein normaler Index, der die Windows-System-API, Nummer `GetSysColor`, akzeptiert. Auf diese Weise ruft wieder den RGB-Wert, der die Farbe, die im zweiten Parameter verwendet werden soll.

Wenn einem Stift oder Pinsel, mit der eine neue Farbe zu speichern, müssen Sie `AdviseBroadcastMessages` (außerhalb der Visual Studio-Shell) und zum Lauschen auf `WM_SYSCOLORCHANGE` und `WM_THEMECHANGED` Nachrichten.

Um die Farbe-Dienst in systemeigenem Code zuzugreifen, stellen Sie einen Aufruf, der folgende angezeigt:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Die `COLORREF` Rückgabewerte `GetVSSysColorEx()` enthalten nur R, G, B Komponenten ein Farbdesign aus. Wenn ein Eintrag Design Transparenz verwendet wird, wird der Alpha-Kanal-Wert vor der Rückgabe verworfen. Aus diesem Grund werden, wenn die gewünschten Farbe Umgebung muss an einer Stelle verwendet werden, in denen transparenzkanal wichtig ist, verwenden Sie `IVsUIShell5.GetThemedColor` anstelle von `IVsUIShell2::GetVSSysColorEx`, wie weiter unten in diesem Thema beschrieben.

##### <a name="from-managed-code"></a>Aus verwaltetem code

Zugreifen auf die VSColor Service durch systemeigenen Code ist ziemlich einfach. Wenn Sie mithilfe von verwaltetem Code arbeiten, kann jedoch bestimmen, wie Sie den Dienst verwenden knifflig sein. Beachten Sie, ist hier ein C#-Codeausschnitt veranschaulicht diesen Prozess:

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Wenn Sie in Visual Basic arbeiten, verwenden Sie:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Von WPF-Benutzeroberfläche

Sie können Visual Studio-Farben, durch die Werte, die in der Anwendung exportiert binden `ResourceDictionary`. Es folgt ein Beispiel für die Verwendung von Ressourcen aus der Tabelle sowie zum Binden an die Umgebungsdaten für die Schriftart in XAML.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Hilfsklassen und Methoden für verwalteten code

Für verwalteten Code, der Shell Managed Package Framework-Bibliothek (`Microsoft.VisualStudio.Shell.12.0.dll`) enthält einige Hilfsklassen, die es vereinfacht die Verwendung von Farben mit Design versehen.

Die Hilfsmethoden in den `Microsoft.VisualStudio.Shell.VsColors` Klasse in MPF enthalten `GetThemedGDIColor()` und `GetThemedWPFColor()`. Diese Hilfsmethoden zurückgeben den Farbwert eines Eintrags Design als `System.Drawing.Color` oder `System.Windows.Media.Color`, um in Windows Forms oder WPF-UI verwendet werden.

```csharp
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

Die Klasse kann auch verwendet werden, um VSCOLOR-IDs für einen bestimmten WPF Farbe Resource-Schlüssel erhalten oder umgekehrt.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Die Methoden der `VsColors` Abfragen-Klasse die VSColor Service zurückzugebenden Wert für die jedes Mal, sie werden aufgerufen. Zum Abrufen von eines Farbwert als `System.Drawing.Color`, Alternative mit besserer Leistung wird stattdessen die Methoden verwenden die `Microsoft.VisualStudio.PlatformUI.VSThemeColor` -Klasse, die die Farbwerte, die vom Dienst VSColor zwischengespeichert. Die Klasse intern Shell Broadcastmeldungen Ereignisse abonniert und verwirft den zwischengespeicherten Wert, wenn eine Änderung Design-Ereignis tritt auf. Die Klasse bietet außerdem ein. NET-freundliche Ereignis Designänderungen abonnieren. Verwenden Sie die `ThemeChanged` Ereignis, um einen neuen Handler hinzuzufügen, und Verwenden der `GetThemedColor()` Methode zum Abrufen von Farbe, Werte für die `ThemeResourceKeys` von Interesse sind. Ein Beispielcode könnte folgendermaßen aussehen:

```csharp
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

## <a name="BKMK_ChoosingHighContrastColors"></a> Farben mit hohem Kontrast auswählen

### <a name="overview"></a>Übersicht

Windows verwendet mehrere kontrastreiche auf Systemebene Designs, die den Farbkontrast Text, Hintergründe und Bilder, erhöhen vornehmen Elemente mehr unterschiedliche auf dem Bildschirm angezeigt werden. Aus Gründen der Barrierefreiheit ist es wichtig, dass die Benutzeroberflächenelemente von Visual Studio ordnungsgemäß reagieren, wenn Benutzer zum Design mit hohem Kontrast wechseln.

Nur eine Handvoll von Systemfarben kann für Designs mit hohem Kontrast verwendet werden. Wenn Sie Ihr System Farbnamen auswählen, beachten Sie die folgenden Tipps:

- **Wählen Sie die Systemfarben, die die gleiche semantische Bedeutung haben** als das Element, das Sie Farben sind. Z. B. Wenn Sie eine hohe Kontraste-Farbe für Text in einem Fenster auswählen, verwenden Sie WindowText und nicht ControlText.

- **Wählen Sie die Vordergrund-/Hintergrund-Paare** zusammen oder werden Sie nicht sicher sind, dass Ihre Farbauswahl in allen Designs mit hohem Kontrast funktionieren.

- **Zu bestimmen, welche Teile der Benutzeroberfläche am wichtigsten sind, und stellen sicher, dass Inhaltsbereiche abhebt..** Sie verlieren viele Details, die geringfügige Unterschiede bei den Farbton normalerweise unterscheiden würden, daher ist die Verwendung der starken Rahmenfarben häufig zum Definieren von Bereichen, da keine Farbvarianten für verschiedene Inhaltsbereiche vorhanden sind.

### <a name="system-color-set"></a>System-Farbpalette

Die Tabelle auf [WPF-Teamblog: SystemColors Verweis](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) gibt den vollständigen Satz von Namen der System-Farben und die entsprechenden Farbtöne in jedes Design angezeigt.

Beim Anwenden dieses Satz von Farben auf der Benutzeroberfläche beschränkt *es wird erwartet, dass Sie feinen Details verlieren, die in den "normalen" Designs vorhanden waren*. Hier ist ein Beispiel der Benutzeroberfläche mit feine grauen Farben, die verwendet werden, um Bereiche innerhalb eines Toolfensters zu unterscheiden. In Kombination mit demselben Fenster im Modus mit hohem Kontrast angezeigt sehen Sie sich, dass alle die Hintergründe der gleiche Farbton und die Rahmen von Bereichen von Rahmen, die allein angegeben werden:

![Beispiel für die wie feinen Details sind verlorene Bestätigungen mit hohem Kontrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-A_PropertiesWindow")<br />Beispiel für die wie feinen Details sind verlorene Bestätigungen mit hohem Kontrast

#### <a name="choosing-text-colors-in-an-editor"></a>Textfarben auswählen in einem editor

Farbige Text wird in einem Editor oder auf einer Entwurfsoberfläche an Bedeutung, wie z.B. die Möglichkeit zur leichteren Identifizierung der Gruppen mit ähnlichen Elementen verwendet. Im Design mit hohem Kontrast allerdings müssen Sie nicht die Möglichkeit, mehr als drei Textfarben unterscheiden. WindowText, GrayText und HotTrackText sind die einzigen Farben auf WindowBackground Oberflächen zur Verfügung. Da Sie mehr als drei Farben verwenden können, wählen Sie sorgfältig die wichtigsten Unterschiede, die im Modus mit hohem Kontrast angezeigt werden soll.

Farbtöne für jede von den Tokennamen auf einer Editoroberfläche zulässig sind, wie sie in jeder Design mit hohem Kontrast angezeigt werden:

![Hoher Kontrast Editor Vergleich](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-B_HCEditorComparison")<br />Editor im Design "Hoher Kontrast", Vergleich

Beispiele für die der Editor-Entwurfsoberfläche in das Design "Blau":

![Editor im Design "Blau"](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-C_EditorBlue")<br />Editor im Design "Blau"

![Editor im Design "hoher Kontrast #1"](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor im Design "hoher Kontrast #1"

### <a name="usage-patterns"></a>Verwendungsmuster

Viele allgemeine Elemente der Benutzeroberfläche haben bereits kontrastreiche Farben definiert werden. Sie können diese Verwendungsmuster verweisen, wenn Sie Ihr eigenes System Farbnamen, auswählen, damit Ihre UI-Elemente mit ähnlichen Komponenten konsistent sind.

| Systemfarbe | Verwendung |
| --- | --- |
| ActiveCaption | -Active-IDE und rafted Fenster Schaltfläche Symbole auf, wenn darauf gezeigt wird, und drücken Sie<br />-Befehlsleisten-Hintergrund für die IDE und rafted Windows Titel<br />-Standard Statusleisten-Hintergrund |
| ActiveCaptionText | -Active-IDE und rafted Windows für Title Bar Vordergrund (Text und Symbole)<br />-Hintergrund und Rahmen des aktiven Fensters Schaltflächen auf, wenn darauf gezeigt wird, und drücken Sie |
| Steuerelement | -Kombinationsfeld, Dropdown-Liste, und suchen wird gesteuert, und wenn deaktiviert, einschließlich der Dropdown-Schaltfläche<br />-Schaltflächenhintergrund<br />-Befehlsleisten-Hintergrund<br />-Toolfenster – Hintergrund |
| ControlDark | -IDE Hintergrund<br />-Menü- und Befehlsleiste-Trennzeichen<br />-Befehlsleiste – Rahmen<br />-Zeichnen von Schatten Menü<br />-Tool Registerkarte Standard und zeigen Sie Fensterrahmen und -Trennzeichen<br />-Dokument auch Schaltflächenhintergrunds auf Überlauf<br />-Der andockziel symbolrahmens |
| ControlDarkDark |-Ohne Fokus, ausgewählten Registerkarte Dokumentfenster |
| ControlLight |-Automatisch ausblendbaren registerkartenrahmen<br />-Der Rahmen für die Kontrollkästchen und Dropdown-Liste Kombinationsfeld<br />-Ziel-Hintergrund und Rahmen Andocken |
| ControlLightLight | -Ausgewählten, mit Fokus vorläufigen Rahmen |
| ControlText | -Symbol für Kombinationsfeld Kontrollkästchen und Dropdown-Liste<br />-Toolfenster deaktiviert – Registerkartentext |
| GrayText |-Deaktiviert Kombinationsfeld und Dropdown-Listenfeld, Rahmen, Dropdown-Glyphe, Text und Menüelementtext<br />– Deaktivierter Menütext<br />-Search Steuerelement "Search Options" HeaderText<br />-Suchen Steuerelements Abschnittstrennzeichen |
| Hervorheben | – Alle Hover und gedrückten Hintergrund und Rahmen, mit Ausnahme von Kombinationsfeld Feld Dropdown-Schaltfläche Hintergrund und Dokument gut Überlauf Schaltflächenrahmens<br />– Ausgewähltes Element Hintergründen |
| HighlightText | – Alle Hover- und gedrückten-vordergründen (Text und Symbole)<br />-Fokussiertes Tool Toolfenster- und Registerkarte Fenster Steuerelement Vordergrund<br />-Fokussierte Toolfenster Title-Leiste – Rahmen<br />-Fokussierten, ausgewählten provisorischen Registerkarte Vordergrund<br />-Dokument sowie Überlauf-Schaltflächenrahmens auf, wenn darauf gezeigt wird, und drücken Sie<br />– Ausgewähltes Symbol|
| HotTrack | -Scroll Leiste Thumb-Hintergrund und Rahmen beim Klicken<br />-Pfeilsymbol, das beim Klicken der Bildlaufleiste |
| InactiveCaption | -Inaktiv-IDE und rafted Fenster Schaltfläche Symbole, wenn darauf gezeigt wird<br />-Befehlsleisten-Hintergrund für die IDE und rafted Windows Titel<br />– Deaktivierter durchsuchen-Steuerelement – Hintergrund |
| InactiveCaptionText | -Inaktiv-IDE und rafted Windows Title Bar Vordergrund (Text und Symbole)<br />-Inaktiven Fensters-Schaltflächen-Hintergrund und Rahmen, wenn darauf gezeigt wird<br />-Ohne Fokus Toolfenster Schaltfläche – Hintergrund und Rahmen<br />– Deaktivierter Suche Steuerelement Vordergrund |
| Menü | -Der Menühintergrund Dropdownliste<br />-Aktivierten und deaktivierten häkchenhintergrund |
| MenuText | -Dropdown-Menü "Rahmen"<br />: Häkchen<br />-Menü Symbole<br />-Text der Dropdown-Menüs<br />– Ausgewähltes Symbol |
| Bildlaufleiste | -Scrollen Sie Leiste und bildlaufleistenpfeilhintergrunds, alle Zustände |
| Fenster | Automatisch ausblendbaren Registerkarte-Hintergrund<br />-Menü Leiste und den hintergrundfarbverlaufsanfang Befehl<br />-Ohne Fokus oder nicht ausgewählte Dokument Registerkarte Fensterhintergrund und Dokumentrahmen, für offene und vorläufige Registerkarten<br />-Ohne Fokus Tool-Fensterhintergrund der Titelleiste<br />-Registerkarte toolfensterhintergrunds, sowohl ausgewählt als auch nicht ausgewählt |
| WindowFrame | -IDE Rahmens |
| WindowText | -Automatisch ausblendbaren Registerkarte Vordergrund<br />– Vordergrund Registerkarte ausgewählte tool<br />-Ohne Fokus Dokumentregisterkarte für Fenster und provisorischen Registerkarte ohne Fokus oder "deaktiviert" Vordergrund<br />-Struktur, die standardmäßige Vordergrund-Ansicht und zeigen Sie für nicht ausgewählte Symbol<br />– Toolfenster ausgewählte Registerkarte – Rahmen<br />-Bildlaufleiste Thumb-Hintergrund, Rahmen und Symbol |

## <a name="BKMK_ExposingColorsForEndUsers"></a> Verfügbarmachen von Farben für Endbenutzer

### <a name="overview"></a>Übersicht

In einigen Fällen sollten Sie ermöglicht dem Endbenutzer auf die Benutzeroberfläche wie anpassen, wenn Sie eine Code-Editor oder die Entwurfsoberfläche erstellen. Die gängigste Methode dazu ist die Verwendung der **Tools &gt; Optionen** Dialogfeld. Es sei denn, Sie hoch UI, die spezielle Steuerelemente erforderlich sind spezialisiert haben, ist die einfachste Möglichkeit zum Präsentieren der anpassungs über die **Schriftarten und Farben** Seite innerhalb der **Umgebung** Abschnitt des Dialogfelds. Für jedes Element, das Sie für die Anpassung verfügbar machen, kann der Benutzer auswählen, so ändern Sie die Vordergrundfarbe, Hintergrundfarbe oder beides.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Erstellen eine VSPackage für Ihre anpassbare Farben

Eine VSPackage kann steuern, Schriftarten und Farben durch benutzerdefinierte Kategorien und Einblenden von Elementen auf der Eigenschaftenseite für Schriftarten und Farben. Wenn Sie diesen Mechanismus verwenden zu können, muss die VSPackages implementieren die [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) -Schnittstelle und die zugehörigen Schnittstellen.

Im Prinzip kann dieser Mechanismus verwendet werden, so ändern Sie alle Elemente mit vorhandenen anzeigen und die Kategorien, die sie enthalten. Allerdings sollte es nicht verwendet werden, die Text-Editor-Kategorie oder ihre Anzeigeelemente zu ändern. Weitere Informationen zu der Kategorie "Text-Editor", finden Sie unter [Schriftart und Farbe (Übersicht)](../font-and-color-overview.md).

Implementieren benutzerdefinierte Kategorien oder Elemente anzeigen, müssen eine VSPackage ein:

- **Erstellen Sie oder identifizieren Sie die Kategorien in der Registrierung.** Die IDE Implementierung der **Schriftarten und Farben** Eigenschaftenseite anhand dieser Informationen ordnungsgemäß für den Dienst, der eine angegebene Kategorie unterstützt Abfragen.

- **Erstellen Sie oder identifizieren Sie Gruppen in der Registrierung (optional).** Es kann hilfreich sein, eine Gruppe definieren, die die Gesamtmenge von zwei oder mehr Kategorien darstellt. Wenn eine Gruppe definiert ist, wird die IDE automatisch zusammengeführt Unterkategorien und verteilt die Elemente in der Gruppe anzeigen.

- **Implementieren Sie die IDE-Unterstützung.**

- **Behandeln Sie Schriftart- und farbänderungen an.**

#### <a name="to-create-or-identify-categories"></a>Zum Erstellen oder Identifizieren von Kategorien

Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrag unter `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` , in denen `<Category>` ist der nicht lokalisierte Name der Kategorie.

Füllen Sie die Registrierung mit zwei Werten:

| Name | Typ | Daten | Beschreibung |
| --- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Eine GUID zum Identifizieren der Kategorie erstellt |
| Package | REG_SZ | GUID | Die GUID des VSPackage-Diensts, der die Kategorie unterstützt. |

 Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen [einer IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) für die entsprechende Kategorie.

#### <a name="to-create-or-identify-groups"></a>Zum Erstellen oder Identifizieren von Gruppen

Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrag unter `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` , in denen `<group>` der nicht lokalisierten Namen der Gruppe ist.

Füllen Sie die Registrierung mit zwei Werten:

| Name | Typ | Daten | Beschreibung |
|--- | --- | --- | --- |
| Kategorie | REG_SZ | GUID | Eine GUID zum Identifizieren der Kategorie erstellt |
| Package | REG_SZ | GUID | Die GUID des VSPackage-Diensts, der die Kategorie unterstützt. |

Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> für die entsprechende Gruppe.

![Implementation of IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementierung von `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>Zum Implementieren von IDE-Unterstützung

Implementieren [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), womit entweder ein [einer IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) Schnittstelle oder ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle für die IDE für die einzelnen Kategorien oder eine Gruppe von angegebenen GUID.

Für jede Kategorie unterstützt, eine VSPackage implementiert eine separate Instanz von der [einer IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) Schnittstelle.

Die Methoden implementiert, über [einer IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) müssen die IDE mit bereitstellen:

- Liste der Elemente in der Kategorie anzeigen

- Lokalisierbaren Namen für Anzeigeelemente

- Anzeigen von Informationen für jedes Element der Kategorie

> [!NOTE]
> Jede Kategorie muss mindestens ein Display-Element enthalten.

Die IDE verwendet das <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle, um eine Kombination aus verschiedenen Kategorien zu definieren.

Die Implementierung bietet die IDE mit:

- Eine Liste der Kategorien, die einer bestimmten Gruppe bilden

- Zugriff auf Instanzen der [einer IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) unterstützt jede Kategorie in der Gruppe

- Lokalisierbare Gruppennamen

#### <a name="updating-the-ide"></a>Aktualisieren der IDE

Die IDE speichert Informationen über Schriftart-und Farbeinstellungen. Also nach jeder Änderung der Konfiguration IDE-Schriftart und Farbe, um sicherzustellen, dass der Cache auf dem neuesten Stand ist eine bewährte Methode.

Aktualisieren des Caches erfolgt über die [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) Schnittstelle und kann ausgeführt global oder nur für ausgewählte Elemente.

### <a name="handling-font-and-color-changes"></a>Behandeln von Schriftart- und farbänderungen an

Um die farbliche Kennzeichnung von Text ordnungsgemäß zu unterstützen, die eine VSPackage anzeigt, muss der Farbgebung-Dienst unterstützt das VSPackage auf die vom Benutzer initiierte Änderungen, die über die Eigenschaftenseite für Schriftarten und Farben reagieren.

Zu diesem Zweck müssen eine VSPackage ein:

- **IDE-generierte Ereignisse behandeln** durch die Implementierung der [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) Schnittstelle. Die IDE Ruft die entsprechende Methode, die folgenden Änderungen durch den Benutzer von der Seite "Schriftarten und Farben". Beispielsweise ruft die [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) Methode, wenn eine neue Schriftart ausgewählt ist.

  **ODER**

- **Abrufen die IDE Änderungen**. Dies kann erfolgen über das System implementierter [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) Schnittstelle. Zwar in erster Linie für die Unterstützung von Persistenz der [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) Methode Schriftart und Farbe zu Elementen zu erhalten. Weitere Informationen zu den Schriftart-und farbeinstellungen, finden Sie im MSDN-Artikel [den Zugriff auf gespeicherte Schriftart- und Farbeinstellungen](../accessing-stored-font-and-color-settings.md).

> [!NOTE]
> Verwenden, um sicherzustellen, dass die Abfrageergebnisse richtig sind, die [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) Schnittstelle, um zu bestimmen, ob eine Entleerung des Cache und die Updates erforderlich sind, vor dem Aufrufen der Abrufmethoden, der die [IVsFontAndColorStorage ](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) Schnittstelle.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrieren benutzerdefinierte Schriftart und Farbe Kategorie ohne Schnittstellen zu implementieren

Im folgenden Codebeispiel wird veranschaulicht, registrieren Sie die benutzerdefinierte Schriftart und Farbe, Kategorie ohne Schnittstellen zu implementieren:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Für dieses Codebeispiel:

- `"NameID"` die Ressourcen-ID, der den Namen der lokalisierten Kategorie im Paket =
- `"ToolWindowPackage"` = Paket-GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` ist nur ein Beispiel und der tatsächliche Wert kann eine neue GUID, die durch die Implementierung bereitgestellt.

### <a name="set-the-font-and-color-property-category-guid"></a>Legen Sie die Schriftart und Farbe Eigenschaftskategorie-GUID

Das folgende Codebeispiel veranschaulicht das Festlegen der Category-GUIDs.

```csharp
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
