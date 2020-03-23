---
title: Farben und Formatierung
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0330ef80fc1127893590ef8d326cb5b8e0cf0160
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301344"
---
# <a name="colors-and-styling-for-visual-studio"></a>Farben und Stile für Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>Verwenden von Farbe in Visual Studio
 In Visual Studio wird Farbe in erster Linie als Kommunikationswerkzeug und nicht nur als Dekoration verwendet. Verwenden Sie Farbe minimal und reservieren Sie sie für Situationen, in denen Sie:

- Kommunizieren Sie Bedeutung oder Zugehörigkeit (z. B. Plattform- oder Sprachmodifizierer)

- Aufmerksamkeit erregen (z. B. Anzeige einer Statusänderung)

- Verbessern Sie die Lesbarkeit und stellen Sie Meilensteine für die Navigation auf der Benutzeroberfläche bereit

- Erhöhen Sie die Erwünschtheit

  Es gibt mehrere Optionen zum Zuweisen von Farben zu UI-Elementen in Visual Studio. Manchmal kann es schwierig sein, herauszufinden, welche Option Sie verwenden sollen, oder wie Sie es richtig verwenden. Dieses Thema hilft Ihnen:

1. Verstehen der verschiedenen Dienste und Systeme, die zum Definieren von Farben in Visual Studio verwendet werden.

2. Wählen Sie die richtige Option für ein bestimmtes Element aus.

3. Verwenden Sie die von Ihnen gewählte Option richtig.

   **WICHTIG:** Nie Hardcode-Hex-, RGB- oder Systemfarben für Ihre UI-Elemente. Die Nutzung der Dienste ermöglicht Flexibilität bei der Abstimmung von Farbtönen. Darüber hinaus können Sie ohne den Dienst die Theme-Switching-Funktionen des [VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)nicht nutzen.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Methoden zum Zuweisen von Farbe zu Visual Studio-Schnittstellenelementen
 Wählen Sie die Methode aus, die für Ihre UI-Elemente am besten geeignet ist.

|Ihre Benutzeroberfläche|Methode|Was sind sie?|
|-------------|------------|--------------------|
|Sie verfügen über eingebettete oder eigenständige Dialogfelder.|**Systemfarben**|Systemnamen, mit denen das Betriebssystem die Farbe und Darstellung der UI-Elemente definieren kann, z. B. für allgemeine Dialogsteuerelemente.|
|Sie verfügen über eine benutzerdefinierte Benutzeroberfläche, die mit der gesamten VS-Umgebung konsistent sein soll, und Sie verfügen über UI-Elemente, die der Kategorie und der semantischen Bedeutung der freigegebenen Token entsprechen.|**Gemeinsame gemeinsame Farben**|Vorhandene vordefinierte Farbtokennamen für bestimmte UI-Elemente|
|Sie haben ein einzelnes Feature oder eine Gruppe von Features, und es gibt keine gemeinsame Farbe für ähnliche Elemente.|**Benutzerdefinierte Farben**|Farbtokennamen, die für einen Bereich spezifisch sind und nicht für andere Benutzeroberflächen freigegeben werden sollen|
|Sie möchten dem Endbenutzer erlauben, die Benutzeroberfläche oder den Inhalt anzupassen (z. B. für Texteditoren oder spezielle Designerfenster).|**Endbenutzeranpassung**<br /><br /> **(Tools > Optionsdialog)**|Einstellungen, die auf der Seite "Schriftarten und Farben" im Dialogfeld **"Tools > Options"** oder auf einer speziellen Seite definiert sind, die für ein UI-Feature spezifisch ist.|

### <a name="visual-studio-themes"></a>Visual Studio-Themen
 Visual Studio verfügt über drei verschiedene Farbthemen: hell, dunkel und blau. Es erkennt auch den Modus mit hohem Kontrast, bei dem es sich um ein systemweites Farbdesign handelt, das für die Barrierefreiheit entwickelt wurde.

 Benutzer werden aufgefordert, ein Design während der ersten Verwendung von Visual Studio auszuwählen und können Designs später wechseln, indem sie zu **Tools > Optionen > Umgebung > Allgemein** wechseln und ein neues Design aus dem Dropdown-Menü "Farbthema" auswählen.

 Benutzer können auch die Systemsteuerung verwenden, um ihre gesamten Systeme in eines von mehreren Themen mit hohem Kontrast umzuschalten. Wenn ein Benutzer ein Design mit hohem Kontrast auswählt, wirkt sich die Visual Studio-Farbdesignauswahl nicht mehr auf Farben in Visual Studio aus, obwohl alle Designänderungen gespeichert werden, wenn der Benutzer den Modus "Hoher Kontrast" beendet. Weitere Informationen zum Modus mit hohem Kontrast finden Sie unter Auswählen von [Farben mit hohem Kontrast](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Der VSColor-Service
 Visual Studio stellt einen Umgebungsfarbdienst bereit, der als VSColor-Dienst bezeichnet wird und mit dem Sie die Farbwerte Ihrer UI-Elemente an einen benannten Eintrag binden können, der Farbwerte für jedes Visual Studio-Design enthält. Dadurch wird sichergestellt, dass sich Ihre Farben automatisch ändern, um das aktuelle vom Benutzer ausgewählte Design oder den Modus "Hoher Kontrast" des Systems widerzuspiegeln. Die Verwendung des Dienstes bedeutet, dass die Implementierung aller themebezogenen Farbänderungen an einem Ort behandelt wird, und wenn Sie gemeinsame freigegebene Farben aus dem Dienst verwenden, spiegelt die Benutzeroberfläche automatisch neue Designs in zukünftigen Versionen von Visual Studio wider.

### <a name="implementation"></a>Implementierung
 Der Visual Studio-Quellcode enthält mehrere Paketdefinitionsdateien, die Listen mit Tokennamen und die entsprechenden Farbwerte für jedes Design enthalten. Der Farbdienst liest die in diesen Paketdefinitionsdateien definierten VSColors. Auf diese Farben wird in XAML-Markup oder Code verwiesen und dann entweder über die **IVsUIShell5.GetThemedColor-Methode** oder eine DynamicResource-Zuordnung geladen.

### <a name="system-colors"></a>Systemfarben
 Allgemeine Steuerelemente verweisen standardmäßig auf die Systemfarben. Wenn die Benutzeroberfläche Systemfarben verwenden soll, z. B. wenn Sie ein eingebettetes oder eigenständiges Dialogfeld erstellen, müssen Sie nichts tun.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Gemeinsame freigegebene Farben im VSColor-Dienst
 Die Schnittstellenelemente sollten die gesamte Visual Studio-Umgebung widerspiegeln. Durch die Wiederverwendung der gemeinsamen Farben, die für die ui-Komponente geeignet sind, die Sie entwerfen, stellen Sie sicher, dass die Benutzeroberfläche mit anderen Visual Studio-Schnittstellen konsistent ist und dass Ihre Farben automatisch aktualisiert werden, wenn Designs hinzugefügt oder aktualisiert werden.

 Bevor Sie gemeinsame freigegebene Farben verwenden, sollten Sie sicherstellen, dass Sie wissen, wie sie richtig verwendet werden. Die falsche Verwendung gemeinsamer freigegebener Farben kann zu einer inkonsistenten, frustrierenden oder verwirrenden Erfahrung für Ihre Benutzer führen.

### <a name="user-customizable-colors"></a>Benutzeranpassbare Farben
 Siehe: [Anzeigen von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 Manchmal möchten Sie dem Endbenutzer erlauben, die Benutzeroberfläche anzupassen, z. B. wenn Sie einen Code-Editor oder eine Entwurfsoberfläche erstellen. Anpassbare UI-Komponenten finden Sie im Abschnitt **Schriftarten und Farben** im Dialogfeld **Tools > Optionen,** in dem Benutzer die Vordergrundfarbe, die Hintergrundfarbe oder beides ändern können.

 ![Tools &#62; Optionsdialog felden in Visual Studio](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")

 **Dialog mit Tools>Optionen**

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>Der VSColor-Service
 Visual Studio bietet einen Umgebungsfarbdienst, der auch als VSColor-Dienst oder Als Shellfarbdienst bezeichnet wird. Mit diesem Service können Sie die Farbwerte der UI-Elemente an einen Farbsatz mit Namenwert binden, der Farben für jedes Design enthält. Der VSColor-Dienst muss für alle UI-Elemente verwendet werden, damit sich die Farben automatisch ändern, um das aktuelle vom Benutzer ausgewählte Design widerzuspiegeln, und damit die an den Umgebungsfarbdienst gebundene Benutzeroberfläche in zukünftige Versionen von Visual Studio integriert wird.

### <a name="how-the-service-works"></a>Funktionsweise des Diensts
 Der Umgebungsfarbdienst liest VSColors, die in der .pkgdef für die UI-Komponente definiert sind. Diese VSColors werden dann in XAML-Markup oder Code referenziert und entweder über die **IVsUIShell5.GetThemedColor** oder eine DynamicResource-Zuordnung geladen.

 ![Umgebungsfarbe – Dienstarchitektur](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")

 **Umgebungsfarbe – Dienstarchitektur**

### <a name="accessing-the-service"></a>Zugriff auf den Dienst
 Es gibt verschiedene Möglichkeiten, auf den VSColor-Dienst zuzugreifen, je nachdem, welche Art von Farbtoken Sie verwenden und welche Art von Code Sie haben.

#### <a name="predefined-environment-colors"></a>Vordefinierte Umgebungsfarben

##### <a name="from-native-code"></a>Aus systemeigenem Code
 Die Shell stellt einen Dienst bereit, der Zugriff auf die COLORREF der Farben ermöglicht. Der Dienst/die Schnittstelle ist:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 In der Datei VSShell80.idl weist die Enumeration **__VSSYSCOLOREX** Schalenfarbkonstanten auf. Um sie zu verwenden, übergeben Sie als Indexwert entweder einen der Werte aus der Enumerat __VSSYSCOLOREX in MSDN dokumentiert oder eine reguläre Indexnummer, die die Windows-System-API, **GetSysColor**, akzeptiert. Dadurch wird der RGB-Wert der Farbe zurückerhalten, die im zweiten Parameter verwendet werden soll.

 Wenn Sie einen Stift oder Pinsel mit einer neuen Farbe speichern, müssen Sie AdviseBroadcastMessages (außerhalb der Visual Studio-Shell) und WM_SYSCOLORCHANGE und WM_THEMECHANGED Nachrichten abhören.

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **HINWEIS:** Die von **GetVSSysColorEx()** zurückgegebenen COLORREF-Werte enthalten nur R,G,B-Komponenten einer Designfarbe. Wenn ein Designeintrag Transparenz verwendet, wird der Alphakanalwert vor der Rückgabe verworfen. Wenn daher die Umgebungsfarbe von Interesse an einem Ort verwendet werden muss, an dem Transparenzkanal wichtig ist, sollten Sie IVsUIShell5.GetThemedColor anstelle von IVsUIShell2::GetVSSysColorEx verwenden, wie weiter unten in diesem Thema beschrieben.

##### <a name="from-managed-code"></a>Aus verwaltetem Code
 Der Zugriff auf den VSColor-Dienst über systemeigenen Code ist ziemlich einfach. Wenn Sie jedoch über verwalteten Code arbeiten, kann es schwierig sein, die Verwendung des Dienstes zu bestimmen. In diesem Sinne ist hier ein Codeausschnitt von C-Code, der diesen Prozess demonstriert:

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

##### <a name="from-wpf-ui"></a>Von der WPF-Benutzeroberfläche
 Sie können Visual Studio-Farben über Werte binden, die in das ResourceDictionary der Anwendung exportiert werden. Im Folgenden finden Sie ein Beispiel für die Verwendung von Ressourcen aus der Farbtabelle sowie die Bindung an die Umgebungsschriftartdaten in XAML.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Hilfsklassen und -methoden für verwalteten Code
 Für verwalteten Code enthält die Managed Package Framework-Bibliothek der Shell (Microsoft.VisualStudio.Shell.12.0.dll) einige Hilfsklassen, die die Verwendung von Thematischen Farben erleichtern.

 Die Hilfsmethoden in der **Microsoft.VisualStudio.Shell.VsColors-Klasse** in MPF umfassen **GetThemedGDIColor()** und **GetThemedWPFColor()**. Diese Hilfsmethoden geben den Farbwert eines Designeintrags als System.Drawing.Color oder System.Windows.Media.Color zurück, der in WinForms oder WPF UI verwendet werden soll.

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

 Die Klasse kann auch verwendet werden, um VSCOLOR-Bezeichner für einen bestimmten WPF-Farbressourcenschlüssel zu erhalten, oder umgekehrt.

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 Die Methoden der **VsColors-Klasse** abfragen den VSColor-Dienst, um den Farbwert jedes Mal zurückzugeben, wenn sie aufgerufen werden. Um einen Farbwert als **System.Drawing.Color**zu erhalten, besteht eine Alternative mit besserer Leistung darin, stattdessen die Methoden der **Microsoft.VisualStudio.PlatformUI.VSThemeColor-Klasse** zu verwenden, die die vom VSColor-Dienst abgerufenen Farbwerte zwischenspeichert. Die Klasse abonniert intern Shell-Broadcast-Nachrichtenereignisse und verwirft den zwischengespeicherten Wert, wenn ein Designänderungsereignis auftritt. Außerdem stellt die Klasse eine zur Verfügung. NET-freundliches Ereignis zum Abonnieren von Designänderungen. Verwenden Sie das **ThemeChanged-Ereignis,** um einen neuen Handler hinzuzufügen, und verwenden Sie die **GetThemedColor()-Methode,** um Farbwerte für die von Interesse sindden **ThemeResourceKeys** abzusondern. Ein Beispielcode könnte wie folgt aussehen:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Auswählen von Farben mit hohem Kontrast

### <a name="overview"></a>Übersicht
 Windows verwendet mehrere Designs auf Systemebene mit hohem Kontrast, die den Farbkontrast von Text, Hintergründen und Bildern erhöhen, sodass Elemente auf dem Bildschirm deutlicher erscheinen. Aus Gründen der Barrierefreiheit ist es wichtig, dass Visual Studio-Schnittstellenelemente korrekt reagieren, wenn Benutzer zu einem Design mit hohem Kontrast wechseln.

 Nur eine Handvoll Systemfarben können für Hochkontrast-Themen verwendet werden. Beachten Sie bei der Auswahl der Systemfarbnamen die folgenden Tipps:

1. Wählen Sie Systemfarben aus, **die dieselbe semantische Bedeutung haben** wie das Element, das Sie färben. Wenn Sie z. B. eine kontrastreiche Farbe für Text in einem Fenster auswählen, verwenden Sie WindowText und nicht ControlText.

2. **Wählen Sie Vordergrund-/Hintergrundpaare zusammen,** oder Sie sind nicht sicher, ob Ihre Farbauswahl in allen Themen mit hohem Kontrast funktioniert.

3. **Bestimmen Sie, welche Teile der Benutzeroberfläche die wichtigsten sind, und stellen Sie sicher, dass Inhaltsbereiche hervorgehoben werden.** Sie verlieren viele Details, die subtile Unterschiede im Farbton normalerweise unterscheiden würden, sodass die Verwendung starker Rahmenfarben üblich ist, um Inhaltsbereiche zu definieren, da es keine Farbvarianten für verschiedene Inhaltsbereiche gibt.

### <a name="system-color-set"></a>Systemfarbsatz
 Die Tabelle unter [WPF Team Blog: SystemColors Reference](https://devblogs.microsoft.com/wpf/systemcolors-reference/) gibt den vollständigen Satz von Systemfarbnamen und die entsprechenden Farbtöne an, die in jedem Design angezeigt werden.

 Wenn Sie diesen begrenzten Satz von Farben auf Ihre Benutzeroberfläche anwenden, *wird erwartet, dass Sie subtile Details verlieren, die in den "normalen" Themen vorhanden waren.* Hier ist ein Beispiel für die Benutzeroberfläche mit subtilen grauen Farben, die verwendet werden, um Bereiche innerhalb eines Werkzeugfensters zu unterscheiden. Wenn Sie mit demselben Fenster gekoppelt sind, das im Modus "Hoher Kontrast" angezeigt wird, können Sie sehen, dass alle Hintergründe den gleichen Farbton haben und die Ränder dieser Bereiche nur durch Rahmen angezeigt werden:

 ![Eigenschaftenfenster](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303-a_PropertiesWindow")

 **Beispiel dafür, wie subtile Details verloren gehen, wenn sie in hohem Kontrast sind**

#### <a name="choosing-text-colors-in-an-editor"></a>Auswählen von Textfarben in einem Editor
 Farbiger Text wird in einem Editor oder auf einer Entwurfsoberfläche verwendet, um Bedeutung anzugeben, z. B. die einfache Identifizierung von Gruppen ähnlicher Elemente. In einem Design mit hohem Kontrast können Sie jedoch nicht zwischen mehr als drei Textfarben unterscheiden. WindowText, GrayText und HotTrackText sind die einzigen Farben, die auf WindowBackground-Oberflächen verfügbar sind. Da Sie nicht mehr als drei Farben verwenden können, wählen Sie sorgfältig die wichtigsten Unterschiede aus, die Sie im Modus "Hoher Kontrast" anzeigen möchten.

 Hues für jeden token namen erlaubt auf einer Editor-Oberfläche, wie sie in jedem High Contrast-Design angezeigt werden:

 ![Editor im Design "Hoher Kontrast", Vergleich](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303-b_HCEditorComparison")

 **Editor im Design "Hoher Kontrast", Vergleich**

 Beispiele für die Editor-Oberfläche im Blue-Thema:

 ![Editor im Design "Blau"](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303-c_EditorBlue")

 **Editor im Design "Blau"**

 ![Editor im Design "Hoher Kontrast"](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303-d_EditorHC1")

 **Editor in High Contrast #1 Thema**

### <a name="usage-patterns"></a>Verwendungsmuster
 Bei vielen häufigen UI-Elementen sind bereits kontrastreiche Farben definiert. Sie können auf diese Verwendungsmuster verweisen, wenn Sie Ihre eigenen Systemfarbnamen auswählen, sodass die UI-Elemente mit ähnlichen Komponenten konsistent sind.

|Systemfarbe|Verwendung|
|------------------|-----------|
|ActiveCaption|- Aktive IDE und geflößte Fensterknopf-Glyphen auf schweben und drücken<br />- Titelleiste Hintergrund für IDE und Floßfenster<br />- Standard-Statusleiste Hintergrund|
|ActiveCaptionText|- Aktive IDE und Geflößte Fenster für Titelleiste Vordergrund (Text und Glyphen)<br />- Hintergrund und Rahmen der aktiven Fenstertasten auf Schweben und Drücken|
|Control|- Kombinationsfeld, Dropdown-Liste und Suchsteuerung Standard und deaktivierter Hintergrund, einschließlich Dropdown-Taste<br />- Dock-Ziel-Taste Hintergrund<br />- Befehlsleiste Hintergrund<br />- Tool-Fenster-Hintergrund|
|ControlDark|- IDE-Hintergrund<br />- Menü- und Befehlsleistentrennzeichen<br />- Befehlsleistengrenze<br />- Menü-Schatten<br />- Werkzeugfenster Registerkarte Standard und Hover-Rahmen und Trennzeichen<br />- Dokument gut Überlauf-Taste Hintergrund<br />- Dock-Ziel-Glyphenrahmen|
|ControlDarkDark|- Unfokussiertes, ausgewähltes Dokument-Registerkartenfenster|
|ControlLight|- Auto-Hide Tab-Rahmen<br />- Combo-Box und Dropdown-Liste Rahmen<br />- Dock Ziel Hintergrund und Grenze|
|SteuerungLightLight|- Ausgewählte, fokussierte provisorische Grenze|
|ControlText|- Combo-Box und Dropdown-Liste Glyphe<br />- Tool-Fenster nicht ausgewählter Tab-Text|
|GrayText|- Kombinationsfeld und Dropdown-Liste deaktivierter Rahmen, Dropdown-Glyphe, Text und Menüelementtext<br />- Deaktivierter Menütext<br />- Suchsteuerung 'Suchoptionen' Headertext<br />- Suchsteuerungsabschnittstrennzeichen|
|Hervorheben|- Alle schwebenund und gedrückten Hintergründe und Rahmen, außer Combo-Box Dropdown-Taste Hintergrund und Dokument gut Überlauf-Taste Rand<br />- Ausgewählte Elementhintergründe|
|HighlightText|- Alle schwebenden und gedrückten Vordergrunde (Text und Glyphen)<br />- Fokussiertes Werkzeugfenster und Dokument-Registerkarten-Steuerung Vordergrund<br />- Fokussierter Werkzeugfenster-Titelleistenrahmen<br />- Fokussierter, ausgewählter provisorischer Tab-Vordergrund<br />- Dokumentieren Sie gut Überlauf-Taste Rand auf Hover und drücken<br />- Ausgewählter Symbolrahmen|
|HotTrack|- Scrollbar Daumen Hintergrund und Rand auf drücken<br />- Scrollbar Pfeil-Glyphe auf Drücken|
|InactiveCaption|- Inaktive IDE und geflößte Fenster-Button-Glyphen auf hover<br />- Titelleiste Hintergrund für IDE und Floßfenster<br />- Deaktivierter Suchsteuerungshintergrund|
|InactiveCaptionText|- Inaktive IDE und Geflößte Fenster Titelleiste Vordergrund (Text und Glyphen)<br />- Inaktive Fenstertasten Hintergrund und Rahmen auf Hover<br />- Unfokussierte Werkzeugfenster-Taste Hintergrund und Rahmen<br />- Deaktivierte Suchsteuerung im Vordergrund|
|Menü|- Dropdown-Menü Hintergrund<br />- Geprüfter und deaktivierter Hintergrund des Häkchens|
|MenuText|- Dropdown-Menürand<br />- Häkchen-Check<br />- Menü-Glyphen<br />- Dropdown-Menütext<br />- Ausgewählter Symbolrahmen|
|Bildlaufleiste|- Scrollbar und Scrollbar Pfeil Hintergrund, alle Zustände|
|Fenster|- Auto-Hide-Tab-Hintergrund<br />- Menüleiste und Befehlsregalhintergrund<br />- Unfokussierte oder nicht ausgewählte Dokumentfenster-Registerkarte Hintergrund und Dokumentrahmen, sowohl für offene als auch für vorläufige Registerkarten<br />- Unfokussierter Werkzeugfenster Titelleiste Hintergrund<br />- Werkzeugfenster-Registerkarte Hintergrund, sowohl ausgewählt als auch nicht ausgewählt|
|WindowFrame|- IDE-Grenze|
|WindowText|- Auto-Hide Tab Vordergrund<br />- Ausgewählte Werkzeugfenster Tab Vordergrund<br />- Unfokussierte Dokumentfenster-Registerkarte und unfokussierte oder nicht ausgewählte vorläufige Registerkarte Vordergrund<br />- Baumansicht Standard-Vordergrund und zeigen sie mit der Maus auf nicht ausgewählte Glyphe<br />- Werkzeugfenster ausgewählt Tab-Rahmen<br />- Scrollbar Daumen Hintergrund, Rahmen und Glyphe|

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Anzeigen von Farben für Endbenutzer

### <a name="overview"></a>Übersicht
 Manchmal möchten Sie dem Endbenutzer erlauben, die Benutzeroberfläche anzupassen, z. B. wenn Sie einen Code-Editor oder eine Entwurfsoberfläche erstellen. Die häufigste Möglichkeit hierzu ist die Verwendung des Dialogfelds **Tools > Optionen.** Sofern Sie nicht über eine hochspezialisierte Benutzeroberfläche verfügen, die spezielle Steuerelemente erfordert, ist die einfachste Möglichkeit, die Anpassung zu präsentieren, über die Seite **Schriftarten und Farben** im Abschnitt **Umgebung** des Dialogfelds. Für jedes Element, das Sie zur Anpassung verfügbar machen, kann der Benutzer die Vordergrundfarbe, die Hintergrundfarbe oder beides ändern.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Erstellen eines VSPackage für Ihre anpassbaren Farben
 Ein VSPackage kann die Schriftarten und Farben über benutzerdefinierte Kategorien steuern und Elemente auf der Eigenschaftenseite Schriftarten und Farben anzeigen. Bei Verwendung dieses Mechanismus muss VSPackages die [IVsFontAndColorDefaultsProvider-Schnittstelle](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) und die zugehörigen Schnittstellen implementieren.

 Im Prinzip kann dieser Mechanismus verwendet werden, um alle vorhandenen Anzeigeelemente und die Kategorien, die sie enthalten, zu ändern. Es sollte jedoch nicht verwendet werden, um die Text-Editor-Kategorie oder ihre Anzeigeelemente zu ändern. Weitere Informationen zur Kategorie Texteditor finden Sie unter [Schriftart- und Farbübersicht](https://msdn.microsoft.com/library/bb165065.aspx).

 Um benutzerdefinierte Kategorien zu implementieren oder Elemente anzuzeigen, muss ein VSPackage:

- **Erstellen oder identifizieren Sie Kategorien in der Registrierung.** Die IDE-Implementierung der Eigenschaftenseite **"Schriftarten und Farben"** verwendet diese Informationen, um den Dienst, der eine bestimmte Kategorie unterstützt, korrekt abzufragen.

- **Erstellen oder Identifizieren von Gruppen in der Registrierung (optional).** Es kann nützlich sein, eine Gruppe zu definieren, die die Vereinigung von zwei oder mehr Kategorien darstellt. Wenn eine Gruppe definiert ist, führt die IDE automatisch Unterkategorien zusammen und verteilt Anzeigeelemente innerhalb der Gruppe.

- **Implementieren Sie die IDE-Unterstützung.**

- **Behandeln Sie Schriftart- und Farbänderungen.**

#### <a name="to-create-or-identify-categories"></a>So erstellen oder identifizieren Sie Kategorien
 Erstellen Sie einen speziellen Kategorieregistrierungseintrag unter\\ [HKLM-SOFTWARE-Microsoft-<Visual Studio-Version\>"FontAndColors\\<Kategorie\>]. \<Kategorie> ist der nicht lokalisierte Name der Kategorie.

 Füllen Sie die Registrierung mit zwei Werten aus:

|Name|type|Daten|Beschreibung|
|----------|----------|----------|-----------------|
|Category|REG_SZ|GUID|Eine GUID, die erstellt wurde, um die Kategorie zu identifizieren|
|Paket|REG_SZ|GUID|Die GUID des VSPackage-Dienstes, der die Kategorie|

 Der in der Registrierung angegebene Dienst muss eine Implementierung von [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) für die entsprechende Kategorie bereitstellen.

#### <a name="to-create-or-identify-groups"></a>So erstellen oder identifizieren Sie Gruppen
 Erstellen Sie einen speziellen Kategorieregistrierungseintrag unter\\ [HKLM-SOFTWARE-Microsoft-<Visual Studio-Version\>"FontAndColors\\<Gruppe\>]. \<Gruppe> ist der nicht lokalisierte Name der Gruppe.

 Füllen Sie die Registrierung mit zwei Werten aus:

|Name|type|Daten|Beschreibung|
|----------|----------|----------|-----------------|
|Category|REG_SZ|GUID|Eine GUID, die erstellt wurde, um die Kategorie zu identifizieren|
|Paket|REG_SZ|GUID|Die GUID des VSPackage-Dienstes, der die Kategorie|

 Der in der Registrierung angegebene Dienst muss eine Implementierung von **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** für die entsprechende Gruppe bereitstellen.

 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>So implementieren Sie DIE IDE-Unterstützung
 Implementieren Sie [GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), das entweder eine [IVsFontAndColorDefaults-Schnittstelle](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) oder eine **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup-Schnittstelle** an die IDE für jede angegebene Kategorie oder Gruppen-GUID zurückgibt.

 Für jede kategorie, die es unterstützt, implementiert ein VSPackage eine separate Instanz der [IVsFontAndColorDefaults-Schnittstelle.](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)

 Die über [IVsFontAndColorDefaults implementierten](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) Methoden müssen der IDE Folgendes zur Verfügung stellen:

- Listen der Anzeigeelemente in der Kategorie

- Lokalisierbare Namen für Anzeigeelemente

- Anzeigen von Informationen für jedes Mitglied der Kategorie

  **HINWEIS:** Jede Kategorie muss mindestens ein Anzeigeelement enthalten.

  Die IDE verwendet die **Schnittstelle T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup,** um eine Vereinigung mehrerer Kategorien zu definieren.

  Seine Implementierung bietet der IDE:

- Eine Liste der Kategorien, aus denen eine bestimmte Gruppe besteht

- Zugriff auf Instanzen von [IVsFontAndColorDefaults,](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) die jede Kategorie innerhalb der Gruppe unterstützen

- Lokalisierbare Gruppennamen

#### <a name="updating-the-ide"></a>Aktualisieren der IDE
 Die IDE speichert Informationen zu Schriftart- und Farbeinstellungen zwischen. Daher ist es nach jeder Änderung der IDE-Schriftart- und Farbkonfiguration eine bewährte Methode, sicherzustellen, dass der Cache auf dem neuesten Stand ist.

 Das Aktualisieren des Cacheerfolgtes erfolgt über die [IvsFontAndColorCacheManager-Schnittstelle](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) und kann global oder nur für ausgewählte Elemente durchgeführt werden.

### <a name="handling-font-and-color-changes"></a>Umgang mit Schrift- und Farbänderungen
 Um die Farbgebung von Text, den ein VSPackage anzeigt, ordnungsgemäß zu unterstützen, muss der Farbisierungsdienst, der das VSPackage unterstützt, auf die vom Benutzer initiierten Änderungen reagieren, die über die Eigenschaftenschriftarten und Farben vorgenommen wurden.

 Dazu muss ein VSPackage:

- **IDE-generierte Ereignisse** durch Implementieren der [IVsFontAndColorEvents-Schnittstelle](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) behandeln. Die IDE ruft die entsprechende Methode auf, die auf Benutzeränderungen der Seite Schriftarten und Farben folgt. Beispielsweise wird die [OnFontChanged-Methode](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) aufgesucht, wenn eine neue Schriftart ausgewählt ist.

  **Oder**

- **die IDE nach Änderungen absuchen**. Dies kann über die vom System implementierte [IVsFontAndColorStorage-Schnittstelle](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) erfolgen. Obwohl die [GetItem-Methode](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) in erster Linie die Persistenz unterstützt, kann sie Schriftart- und Farbinformationen für Anzeigeelemente abrufen. Weitere Informationen zu Schriftart- und Farbeinstellungen finden Sie im MSDN-Artikel [Zum Zugriff auf gespeicherte Schriftart- und Farbeinstellungen](https://msdn.microsoft.com/library/bb166382.aspx).

  **HINWEIS:** Um sicherzustellen, dass die Abrufergebnisse korrekt sind, verwenden Sie die [IVsFontAndColorCacheManager-Schnittstelle,](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) um zu ermitteln, ob eine Cache-Flush- und -Aktualisierung erforderlich ist, bevor sie die Abrufmethoden der [IVsFontAndColorStorage-Schnittstelle](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) aufrufen.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrieren benutzerdefinierter Schriftart und Farbkategorie ohne Implementierung von Schnittstellen
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie die benutzerdefinierte Schriftart und Farbkategorie registrieren, ohne Schnittstellen zu implementieren:

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **Hinweis:**

- "NameID" = die Ressourcen-ID des lokalisierten Kategorienamens in Ihrem Paket

- "ToolWindowPackage" = Paket-GUID

- "Category"="""9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE" ist nur ein Beispiel und der tatsächliche Wert kann eine neue GUID sein, die vom Implementierer bereitgestellt wird.

### <a name="set-the-font-and-color-property-category-guid"></a>Festlegen der Schriftart- und Farbeigenschaftskategorie GUID
 Im folgenden Codebeispiel wird das Festlegen von Kategorie-GUIDs veranschaulicht.

```cs
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
  IVsTextEditorPropertyContainer spPropContainer;
  Guid GUID_EditPropCategory_View_MasterSettings =
  new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
  hr = spPropCatContainer.GetPropertyCategory(
  ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer);
  if(hr == 0)
  {
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID);
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID);
  }
}
```
