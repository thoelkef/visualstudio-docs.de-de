---
title: "Farben und Stilen f&#252;r Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Farben und Stilen f&#252;r Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Mithilfe von Farben in Visual Studio  
 In Visual Studio wird die Farbe in erster Linie als Kommunikationstool, nicht nur als Dekoration verwendet. Verwenden Sie Farbe minimal, und reservieren Sie ihn für Situationen, in denen Sie zu:  
  
-   Kommunikation von Bedeutung oder der Zuordnung \(z. B. Plattform oder Sprache Modifizierer\)  
  
-   Wecken Sie \(z. B., wodurch eine statusänderung\)  
  
-   Verbessern Sie Lesbarkeit zu, und geben Sie Informationen zum Navigieren in der Benutzeroberfläche  
  
-   Serverupdate erhöhen  
  
 Mehrere Optionen, die zum Zuweisen von Farben für Elemente der Benutzeroberfläche in Visual Studio vorhanden sein. Manchmal kann es zu Abbildung schwierig sein, welche Option Sie verwenden sollten, oder wie sie ordnungsgemäß verwenden. In diesem Thema helfen Ihnen:  
  
1.  Verstehen Sie die verschiedenen Dienste und Systeme, die zum Definieren von Farben in Visual Studio.  
  
2.  Wählen Sie die richtige Option für ein angegebenes Element.  
  
3.  Verwenden Sie die Option, die von Ihnen gewählte korrekt.  
  
 **Wichtig:** niemals hartcodieren Hex, RGB oder Systemfarben für UI\-Elemente. Verwendung der Dienste ermöglicht Flexibilität bei der Feineinstellung von Farbton. Darüber hinaus ohne den Dienst nicht werden Design\-switching\-Funktionen nutzen die [Der Dienst VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
### Methoden für das Zuweisen von Farben für die Elemente der Visual Studio\-Benutzeroberfläche  
 Wählen Sie die Methode eignet sich am besten für Ihre UI\-Elemente.  
  
|Die Benutzeroberfläche|Methode|Was sind?|  
|----------------------------|-------------|---------------|  
|Sie verfügen über eingebettete oder eigenständige Dialogfelder.|**Systemfarben**|Namen, mit die das Betriebssystem die Farbe und die Darstellung der Benutzeroberflächenelemente, z. B. für allgemeine Dialogfeld\-Steuerelemente definieren können.|  
|Sie verfügen über benutzerdefinierte Benutzeroberfläche, die Konsistenz der gesamten Visual Studio\-Umgebung ausgeführt werden sollen und Sie Elemente der Benutzeroberfläche, die die Kategorie und die semantische Bedeutung der freigegebenen Token übereinstimmen.|**Allgemeine freigegebenen Farben**|Vorhandene vordefinierte Farbe Tokennamen für bestimmte Elemente der Benutzeroberfläche|  
|Sie haben eine einzelne Funktion oder eine Gruppe von Funktionen, und es gibt keine freigegebenen Farbe für ähnliche Elemente.|**Benutzerdefinierte Farben**|Token Farbnamen, die spezifisch für einen Bereich und nicht gemeinsam mit anderen Benutzeroberfläche verwendet werden soll|  
|Sie möchten können die Endbenutzer\-Benutzeroberfläche oder Inhalt \(z. B. für Text\-Editoren oder spezielle Designerfenstern\) anpassen.|**Endbenutzer\-Anpassung**<br /><br /> **\(Extras \> Optionen\-Dialogfeld\)**|Auf der Seite "Schriftarten und Farben" definierten Einstellungen der **Tools \> Optionen** Dialogfeld oder eine spezielle Seite für eine UI\-Funktion.|  
|Sie haben die Benutzeroberfläche, die in HTML erstellt wurden.|**Daytona**|Ermöglicht die Benutzeroberfläche in HTML für den Dienstzugriff Farbe und Schriftart erstellt.|  
  
### Visual Studio\-Themen  
 Visual Studio verfügt über drei verschiedene Farbschemas: hell, dunkel und Blau. Es erkennt außerdem Modus für hohe Kontraste, eine systemweite Farbschema für Eingabehilfen entworfen wird.  
  
 Benutzer werden aufgefordert, ein Design auswählen, während ihrer ersten Verwendung von Visual Studio und können Designs später ändern, indem Sie auf **Extras \> Optionen \> Umgebung \> allgemeine** und ein neues Design aus dem Dropdown\-Menü "Farbschema" auswählen.  
  
 Benutzer können auch Systemsteuerung verwenden, um ihre gesamten Systeme in einer der verschiedenen Designs mit hohem Kontrast zu wechseln. Klickt ein Benutzer ein Design mit hohem Kontrast, wirkt sich dann die Farbauswahl Design Visual Studio nicht mehr Farben in Visual Studio zwar Designänderungen für gespeichert werden, wenn der Benutzer den Modus für hohe Kontraste beendet. Weitere Informationen zu den Modus für hohe Kontraste, finden Sie unter [Kontrastreiche Farben auswählen](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).  
  
### Der Dienst VSColor  
 Visual Studio bietet einen Umgebung Farbe, bekannt als der VSColor\-Dienst, der Sie einem benannten Eintrag Farbwerte für jedes Visual Studio\-Design enthält die Farbwerte der UI\-Elemente binden kann. Dadurch wird sichergestellt, dass Sie Farben automatisch geändert werden, um den aktuellen Benutzer ausgewählten Designs oder System Modus für hohe Kontraste widerzuspiegeln. Verwendung des Dienstes bedeutet, dass die Implementierung aller Farbe Design\-bezogene Änderungen an einer Stelle verarbeitet, und bei Verwendung von freigegebenen Farben, die vom Dienst Ihrer Benutzeroberfläche automatisch neue Designs in zukünftigen Versionen von Visual Studio entsprechend.  
  
### Implementierung  
 Der Quellcode für Visual Studio umfasst mehrere Paketdefinitionsdateien, die Listen von token und der entsprechenden Werte für jedes Design enthalten. Die Farbe der Dienst liest die VSColors in diese Paketdefinitionsdateien definiert. Diese Farben werden in XAML\-Markup oder im Code verwiesen und dann geladen wird, entweder über die **IVsUIShell5.GetThemedColor** Methode oder eine DynamicResource\-Zuordnung.  
  
### Systemfarben  
 Allgemeine Steuerelemente verweisen die Systemfarben standardmäßig. Wenn Sie Ihre Benutzeroberfläche Systemfarben verwenden, z. B. beim Erstellen einer eingebetteten oder eigenständigen Dialogfeld verwenden möchten, müssen Sie nichts zu tun.  
  
### Allgemeine freigegebenen Farben in der VSColor\-Dienst  
 Die Elemente der Benutzeroberfläche sollte die gesamte Visual Studio\-Umgebung entsprechen. Durch das Wiederverwenden von gemeinsamen freigegebenen Farben, die für die UI\-Komponente geeignet sind, die Sie erstellen, stellen Sie sicher, dass die Schnittstelle mit anderen Visual Studio\-Schnittstellen konsistent ist und Sie Farben automatisch aktualisiert werden, wenn Designs hinzugefügt oder aktualisiert werden.  
  
 Stellen Sie vor der Verwendung von Farben, die gemeinsam genutzten sicher, dass Sie wissen, wie sie ordnungsgemäß verwenden. Falscher Verwendung von Farben, die gemeinsam genutzten möglicherweise eine inkonsistente, frustrierend und verwirrend Erfahrung für Ihre Benutzer.  
  
### Benutzer anpassbare Farben  
 Finden Sie unter: [Verfügbarmachen von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 In einigen Fällen möchten Sie dem Benutzer zum Anpassen der Benutzeroberfläche, z. B. Wenn Sie einen Code\-Editor oder die Entwurfsoberfläche erstellen. Anpassbare UI\-Komponenten finden Sie in der **Schriftarten und Farben** Teil der **Tools \> Optionen** Dialogfeld, in dem Benutzer so ändern Sie die Vordergrundfarbe und\/oder Hintergrundfarbe auswählen können.  
  
 ![Tools &#62; Options dialog in Visual Studio](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301\-a\_ToolsOptionsDialog")  
  
 **Extras \> Dialogfeld "Optionen"**  
  
### Web\-UI\-Farben  
 Es wird immer als üblich, Autor UI\-Komponenten, die mit HTML, sodass sie sowohl in Visual Studio Online als auch in Visual Studio verwendet werden können. Benutzeroberfläche, die in HTML geschrieben muss weiterhin den VSColor\-Dienst verwenden, wenn innerhalb der Visual Studio\-Umgebung ausgeführt wird. Informationen zu Daytona und Ihre Verwendung finden Sie unter [Daytona und Web-GUI](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="BKMK_TheVSColorService"></a> Der Dienst VSColor  
 Visual Studio bietet einen Umgebung Farbe, auch den VSColor\-Dienst oder der Shell Farbe\-Dienst bezeichnet. Dieser Dienst ermöglicht eine Name\-Wert\-Farbe, die Farben für jedes Design enthält die Farbwerte der UI\-Elemente binden. Der VSColor\-Dienst muss für alle Elemente der Benutzeroberfläche verwendet werden, sodass Farben automatisch entsprechend der aktuellen Benutzer ausgewählten Designs und, damit Benutzeroberfläche an den Dienst der Umgebung Farbe gebunden mit neuen Designs in zukünftigen Versionen von Visual Studio integrieren werden.  
  
### Funktionsweise des Diensts  
 Die Umgebung Farbe Service liest VSColors in der PKGDEF für die UI\-Komponente definiert. Diese VSColors klicken Sie dann im XAML\-Markup oder Code referenziert werden und werden geladen, entweder über die **IVsUIShell5.GetThemedColor** oder eine DynamicResource\-Zuordnung.  
  
 ![Environment color service architecture](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302\-a\_EnvironmentColorServiceArchitecture")  
  
 **Umgebungsfarbe – Dienstarchitektur**  
  
### Zugriff auf den Dienst  
 Es gibt verschiedene Arten zum Zugriff auf der Dienst VSColor, je nachdem, welche Farbe Sie Token verwenden und welche Art von Code verwendet.  
  
#### Vordefinierte Umgebung Farben  
  
##### Von systemeigenem code  
 Die Shell stellt einen Dienst, der Zugriff auf die COLORREF Farben haben. Die Dienstschnittstelle ist:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 In der Datei VSShell80.idl, die Enumeration **\_\_VSSYSCOLOREX** Farbkonstanten Shell hat. Verwendet werden, übergeben Sie den Indexwert entweder einen der Werte aus der Enumeration \_\_VSSYSCOLOREX in MSDN dokumentiert oder ein regulärer Index Zahl, die das Windows\-System\-API, **GetSysColor**, akzeptiert. Auf diese Weise erhalten den RGB\-Wert, der die Farbe, die im zweiten Parameter verwendet werden soll.  
  
 Wenn einem Stift oder Pinsel mit einer neuen Farbe zu speichern, müssen AdviseBroadcastMessages \(außerhalb der Visual Studio\-Shell\) und Empfangen von WM\_SYSCOLORCHANGE und WM\_THEMECHANGED.  
  
```  
// To access the color service in native code, you'll make a call that resembles this: pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **Hinweis:** von zurückgegebenen Werte für die COLORREF **GetVSSysColorEx\(\)** enthalten nur R, G, B Komponenten ein Farbdesign aus. Wenn ein Eintrag Design Transparenz verwendet wird, wird der Alpha\-Kanal\-Wert vor der Rückgabe verworfen. Aus diesem Grund die gewünschten Farbe Umgebung muss an einem Ort verwendet werden, wo transparenzkanal wichtig ist, sollten Sie IVsUIShell5.GetThemedColor anstelle von IVsUIShell2::GetVSSysColorEx, verwenden, wie weiter unten in diesem Thema beschrieben.  
  
##### Aus verwaltetem code  
 Zugriff auf den VSColor\-Dienst durch systemeigenen Code ist ziemlich einfach. Wenn Sie mithilfe von verwaltetem Code arbeiten, kann jedoch wie Sie den Dienst ermitteln schwierig sein. Denken Sie daran, ist hier ein C\#\-Codeausschnitt veranschaulicht diesen Prozess:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e) { //getIVSUIShell2 IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2; Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2"); if (uiShell2 != null) { //get the COLORREF structure uint win32Color; uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color); //translate it to a managed Color structure Color myColor = ColorTranslator.FromWin32((int)win32Color); //use it e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100); } }  
```  
  
 Wenn Sie in Visual Basic arbeiten, verwenden Sie:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### Aus WPF\-Benutzeroberfläche  
 Sie können in Visual Studio Farben durch die Werte in der Anwendung ResourceDictionary exportiert binden. Es folgt ein Beispiel für die Verwendung von Ressourcen aus der Tabelle als auch die Bindung an die Umgebung Schriftart in XAML.  
  
```  
<Style TargetType="{x:Type Button}"> <Setter Property="TextBlock.FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter Property="TextBlock.FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" /> <Setter Property="Background" Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" /> </Style>  
```  
  
#### Hilfsklassen und\-Methoden für verwalteten code  
 Für verwalteten Code enthält die Shell Managed Package Framework\-Bibliothek \(Microsoft.VisualStudio.Shell.12.0.dll\) ein paar Hilfsklassen und erleichtert die Verwendung von versehene Farben.  
  
 Die Hilfsmethoden in der **Microsoft.VisualStudio.Shell.VsColors** \-Klasse in MPF **GetThemedGDIColor\(\)** und **GetThemedWPFColor\(\)**. Diese Hilfsmethoden der Rückgabewert der Farbe eines Eintrags Design als System.Drawing.Color oder System.Windows.Media.Color, in Windows Forms\- oder WPF UI verwendet werden.  
  
```  
IVsUIShell5 shell5; Button button = new Button(); button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey); button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey); /// <summary> /// Gets a System.Drawing.Color value from the current theme for the given color key. /// </summary> /// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param> /// <param name="themeResourceKey">The key to find the color for.</param> /// <returns>The current theme's value of the named color.</returns> public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey); // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); } private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Guid category = themeResourceKey.Category; __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush) { colorType = __THEMEDCOLORTYPE.TCT_Background; } // This call will throw an exception if the color is not found uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType); return BitConverter.GetBytes(rgbaColor); } public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey); return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); }  
  
```  
  
 Die Klasse kann auch verwendet werden, um VSCOLOR\-IDs für einen bestimmten WPF Farbe Ressource\-Schlüssel zu erhalten oder umgekehrt.  
  
```  
public static string GetColorBaseKey(int vsSysColor); public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 Die Methoden der **VsColors** Abfragen\-Klasse den VSColor Dienst zurückgeben den Farbwert jedes Mal aufgerufen. Um einen Farbwert als erhalten **System.Drawing.Color**, eine Alternative mit besserer Leistung ist, verwenden Sie stattdessen die Methoden der der **Microsoft.VisualStudio.PlatformUI.VSThemeColor** \-Klasse, die vom Dienst VSColor Farbwerte zwischengespeichert. Die Klasse intern Shell Broadcastmeldungen Ereignisse abonniert und verwirft den zwischengespeicherten Wert bei Eintreten des Ereignisses Design ändern. Die Klasse stellt außerdem ein. NET\-geeignete Ereignis Designänderungen abonnieren. Verwenden der **ThemeChanged** Ereignis, um einen neuen Handler hinzuzufügen, und verwenden die **GetThemedColor\(\)** \-Methode Farbe erhalten Werte für die **ThemeResourceKeys** von Interesse sind. Ein Beispiel für Code könnte folgendermaßen aussehen:  
  
```  
public MyWindowPanel() { InitializeComponent(); // Subscribe to theme changes events so we can refresh the colors VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged; RefreshColors(); } private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e) { RefreshColors(); // Also post a message to all the children so they can apply the current theme appropriately foreach (System.Windows.Forms.Control child in this.Controls) { NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero); } } private void RefreshColors() { this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey); this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey); } protected override void Dispose(bool disposing) { if (disposing) { VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged; base.Dispose(disposing);} }  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a> Kontrastreiche Farben auswählen  
  
### Übersicht  
 Windows verwendet mehrere hohe Kontraste auf Systemebene Designs, die Farbe von Text, Hintergründe und Bilder, Kontrast ausführenden Elemente deutlicher auf dem Bildschirm angezeigt. Aus Gründen der Eingabehilfen ist es wichtig, dass Visual Studio\-Benutzeroberflächenelementen ordnungsgemäß reagiert, wenn Benutzer auf ein Design mit hohem Kontrast wechseln.  
  
 Für hohe Kontraste Designs kann nur eine Handvoll Systemfarben verwendet werden. Wenn Sie Ihr System Farbnamen auswählen, beachten Sie die folgenden Tipps:  
  
1.  **System Farben, die die gleiche semantische Bedeutung haben** als das Element, das Sie färben sind. Wenn Sie eine hohe Kontraste Farbe für Text in einem Fenster auswählen, verwenden Sie z. B. WindowText und nicht ControlText.  
  
2.  **Wählen Sie die Vordergrund\-\/Hintergrund\-Paare** zusammen sein, oder Sie nicht sicher, dass die Farbauswahl alle Designs mit hohem Kontrast funktionieren wird.  
  
3.  **Bestimmen, welche Teile der Benutzeroberfläche am wichtigsten sind, und stellen Sie sicher, dass Inhaltsbereiche abhebt..** Viele Details, die normalerweise feine Unterschiede in Farbe Farbton unterscheiden würde, werden daher die Verwendung der starken Rahmenfarben häufig zum Definieren von Bereichen, da es keine Farbe Varianten für verschiedene Inhaltsbereiche gelöscht werden.  
  
### System\-Farbpalette  
 Die Tabelle auf [WPF\-Teamblog: SystemColors Verweis](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) gibt den vollständigen Satz von Systemnamen für die Farbe und die entsprechende Farbtöne in jedes Design angezeigt.  
  
 Beim Anwenden dieses Satz von Farben an Ihrer Benutzeroberfläche beschränkt *Es wird davon ausgegangen, dass feinen Details verloren, die in den "normalen" Designs vorhanden waren*. Hier ist ein Beispiel der Benutzeroberfläche mit kleinen grauen Farben, die verwendet werden, um Bereiche innerhalb eines Toolfensters zu unterscheiden. Bei Verwendung der gleichen Fenster im Modus für hohe Kontraste angezeigt, sehen Sie, dass alle Hintergründe der gleiche Farbton und die Rahmen der Bereiche durch Rahmen allein angegeben werden:  
  
 ![Properties window](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303\-a\_PropertiesWindow")  
  
 **Beispiel für wie feinen Details sind in hohem Kontrast verloren**  
  
#### Auswählen von Textfarben in einem editor  
 Farbdruckoption Text wird in einem Editor oder auf einer Entwurfsoberfläche verwendet, an Bedeutung, z. B. zur leichteren Identifizierung von Gruppen ähnlicher Elemente ermöglicht. In einem Design mit hohem Kontrast allerdings müssen Sie nicht die Möglichkeit, mehr als drei Farben unterscheiden. WindowText, GrayText und HotTrackText sind der einzigen Farben auf WindowBackground Flächen. Da Sie mehr als drei Farben verwenden können, wählen Sie sorgfältig die wichtigsten Unterschiede, die Sie im Modus für hohe Kontraste anzeigen möchten.  
  
 Farbtöne für jede die Tokens Namen auf einer Editoroberfläche in jeder Design mit hohem Kontrast angezeigt werden:  
  
 ![High Contrast editor comparison](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303\-b\_HCEditorComparison")  
  
 **Editor im Design "Hoher Kontrast", Vergleich**  
  
 Beispiele für die Editor\-Entwurfsoberfläche in das Design "Blau":  
  
 ![Editor in Blue theme](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303\-c\_EditorBlue")  
  
 **Editor im Design "Blau"**  
  
 ![Editor in High Contrast theme](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303\-d\_EditorHC1")  
  
 **Editor im Design "hoher Kontrast \#1"**  
  
### Verwendungsmuster  
 Viele allgemeine Benutzeroberflächenelemente haben bereits kontrastreiche Farben definiert. Sie können diese Verwendungsmuster verweisen, wenn Sie Ihr eigenes System Farbnamen auswählen, damit Ihre UI\-Elemente mit ähnlichen Komponenten konsistent sind.  
  
|Systemfarbe|Verwendung|  
|-----------------|----------------|  
|ActiveCaption|-   Aktive IDE und rafted Fenster Schaltfläche Symbole auf den gezeigt wird, und drücken Sie<br />-   Hintergrund der Titelleiste für IDE und rafted windows<br />-   Hintergrund der designerstatusleiste Standard|  
|ActiveCaptionText|-   Aktive IDE und rafted Windows für Titel Leiste Vordergrund \(Text und Symbole\)<br />-   Hintergrund und Rahmen des aktiven Fensters Schaltflächen gezeigt wird, und drücken Sie|  
|Steuerelement|-   Kombinationsfeld Dropdown\-Liste und Search Standard und deaktiviert Hintergrund des Steuerelements, einschließlich der Dropdown\-Schaltfläche<br />-   Andocken des Hintergrunds des Ziel\-Schaltfläche<br />-   Befehl Hintergrund<br />-   Toolfenster – Hintergrund|  
|ControlDark|-   IDE\-Hintergrund<br />-   Befehlsleiste Trennzeichen<br />-   Befehlsleiste – Rahmen<br />-   Menü Schatten<br />-   Tool Registerkarte Standard und zeigen Sie Fensterrahmen und Trennzeichen<br />-   Dokumentieren Sie gut Überlauf Schaltflächenhintergrund<br />-   Dock Ziel Glyphe Rahmen|  
|ControlDarkDark|-   Ohne Fokus, ausgewählte Registerkarte Dokumentfenster|  
|ControlLight|-   Die Registerkarte Rahmen automatisch im Hintergrund<br />-   Das Kombinationsfeld und Dropdown\-Listenrahmen<br />-   Dock\-Ziel\-Hintergrund und Rahmen|  
|ControlLightLight|-   Ausgewählte, fokussierte vorläufigen Rahmen|  
|ControlText|-   Das Kombinationsfeld und Dropdownlisten\-Symbol<br />-   Tool\-Fenster deaktiviert Registerkartentext|  
|GrayText|-   Das Kombinationsfeld und Rahmen der Dropdown\-Liste deaktiviert, Dropdown\-Symbol, Text und Menüelementtext<br />-   Deaktivierte Menütext<br />-   Steuerelement "Suchoptionen" Header Suchtext<br />-   Suchen\-Steuerelements Abschnittstrennzeichen|  
|Markieren|-   Zeigen Sie alle und Hintergründe und Rahmen, mit Ausnahme von Kombinationsfeld klicken Sie im Dropdownmenü gedrückt Schaltflächenhintergrund und Dokument auch überlaufen Schaltfläche Rahmen<br />-   Ausgewähltes Element Hintergründe|  
|HighlightText|-   Alle Hover und gedrückt Vordergrund \(Text und Symbole\)<br />-   Fokussiertes Tool Fenster\- und Registerkarte Steuerelement Vordergrund<br />-   Fokussiertes Tool Fensterrahmens Title\-Leiste<br />-   Vordergrundfarbe von fokussierten, ausgewählten provisorischen Registerkarte<br />-   Dokumentieren Sie gut Überlauf Schaltfläche Rahmen gezeigt wird, und drücken Sie<br />-   Ausgewählte Rahmen|  
|HotTrack|-   Bildlaufleiste Thumb Hintergrund und einen Rahmen auf<br />-   Bildlaufleiste Pfeilsymbol drücken|  
|InactiveCaption|-   Inaktive IDE und rafted Fenster Schaltfläche Glyphen darauf gezeigt wird<br />-   Hintergrund der Titelleiste für IDE und rafted windows<br />-   Hintergrund für deaktivierte suchen\-Steuerelements|  
|InactiveCaptionText|-   Inaktive IDE und rafted Windows Titel Leiste Vordergrund \(Text und Symbole\)<br />-   Inaktiver Schaltflächen Hintergrund und einen Rahmen auf die gezeigt wird<br />-   Schaltfläche ohne Fokus Toolfenster – Hintergrund und Rahmen<br />-   Deaktivierte Suche Steuerelement Vordergrund|  
|Menü|-   Hintergrunds der Dropdown\-Menüs<br />-   Aktivierte und deaktivierte Häkchen Hintergrund|  
|MenuText|-   Dropdown\-Menü Rahmen<br />-   Kontrollkästchen mit Häkchen<br />-   Menü\-Symbole<br />-   Dropdown\-Menütext<br />-   Ausgewählte Rahmen|  
|Bildlaufleiste|-   Bildlaufleiste oder Bildlaufleiste Pfeil im Hintergrund, alle Zustände|  
|Fenster|-   Die Registerkarte Hintergrund automatisch im Hintergrund<br />-   Menü Balken\- und Befehl Regal Hintergrund<br />-   Ohne Fokus oder die nicht ausgewählten Dokument Registerkarte Hintergrund und Dokument\-Rahmen, für offene und vorläufige Registerkarten<br />-   Ohne Fokus Tool Fenster Hintergrund der Titelleiste<br />-   Toolfenster Registerkarte – Hintergrund, sowohl aktiviert als auch deaktiviert|  
|WindowFrame|-   IDE\-Rahmen|  
|WindowText|-   Die Registerkarte Vordergrund automatisch im Hintergrund<br />-   Ausgewählte Tool Registerkarte Vordergrund<br />-   Ohne Fokus oder die nicht ausgewählten provisorischen Registerkarte Vorder\- und ohne Fokus Dokumentregisterkarte für Fenster<br />-   Struktur anzeigen standardmäßige Vordergrund\- und zeigen Sie auf nicht markierte Symbol<br />-   Toolfenster – ausgewählte Registerkarte Rahmen<br />-   Bildlaufleiste Thumb Hintergrund, Rahmen und Symbol|  
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a> Verfügbarmachen von Farben für Endbenutzer  
  
### Übersicht  
 Manchmal möchten Sie dem Benutzer zum Anpassen der Benutzeroberfläche, z. B. Wenn Sie einen Code\-Editor oder die Entwurfsoberfläche erstellen. Die gängigste Methode hierfür ist die Verwendung der **Tools \> Optionen** Dialogfeld. Wenn die Benutzeroberfläche sehr spezialisiert haben, die spezielle Steuerelemente erfordert ist die einfachste Möglichkeit zum Präsentieren der Anpassung über die **Schriftarten und Farben** Seite innerhalb der **Umgebung** Abschnitt des Dialogfelds. Für jedes Element, das Sie für die Anpassung verfügbar machen, kann der Benutzer auswählen, die Vordergrundfarbe und\/oder Hintergrundfarbe ändern.  
  
### Erstellen ein VSPackage für anpassbare Farben  
 Ein VSPackage kann steuern, Schriftarten und Farben durch benutzerdefinierte Kategorien und Elemente auf der Eigenschaftenseite für Schriftarten und Farben angezeigt. Bei der Verwendung dieser Mechanismus VSPackages implementieren muss die [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) und seine zugehörigen Schnittstellen.  
  
 Im Prinzip kann dieser Mechanismus verwendet werden, so ändern Sie alle vorhandenen Elementen und die Kategorien, die sie enthalten. Allerdings sollten sie nicht verwendet werden so ändern Sie die Text\-Editor oder seiner Anzeigeelemente. Weitere Informationen über die Kategorie des Text\-Editor, finden Sie unter [Schriftart und Farbe \(Übersicht\)](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
 Zum Implementieren von benutzerdefinierter Kategorien oder Elemente anzeigen möchten, müssen ein VSPackage:  
  
-   **Erstellen Sie oder identifizieren Sie der Kategorien in der Registrierung.** Die IDE Implementierung der **Schriftarten und Farben** Eigenschaftenseite verwendet diese Informationen korrekt für die Unterstützung einer bestimmten Kategorie Dienst Abfragen.  
  
-   **Erstellen Sie oder identifizieren Sie Gruppen in der Registrierung \(optional\).** Es ist möglicherweise nützlich, um eine Gruppe zu definieren, die die Vereinigung von zwei oder mehreren Kategorien darstellt. Wenn eine Gruppe definiert ist, wird die IDE automatisch Unterkategorien zusammengeführt und verteilt die Elemente in der Gruppe anzeigen.  
  
-   **Implementieren Sie die IDE\-Unterstützung.**  
  
-   **Behandeln Sie Schriftart und Farbe ändern.**  
  
#### Zum Erstellen oder Identifizieren von Kategorien  
 Erstellen Sie eine besondere Art von Kategorie\-Registrierungseintrag unter \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< Visual Studio\-Version \> \\FontAndColors\\ \< Category \>\]. \< Category \> ist der nicht lokalisierten Namen der Kategorie.  
  
 Füllen Sie die Registrierung mit zwei Werten:  
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|Kategorie|REG\_SZ|GUID|Eine GUID erstellt, um die Kategorie zu identifizieren.|  
|Package|REG\_SZ|GUID|Die GUID des VSPackage\-Diensts, der die Kategorie unterstützt|  
  
 In der Registrierung angegebene Dienst muss eine Implementierung bereitstellen [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) für die entsprechende Kategorie.  
  
#### Zum Erstellen oder Identifizieren von Gruppen  
 Erstellen Sie eine besondere Art von Kategorie\-Registrierungseintrag unter \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< Visual Studio\-Version \> \\FontAndColors\\ \< Gruppe \>\]. \< Gruppe \> ist der nicht lokalisierten Namen der Gruppe.  
  
 Füllen Sie die Registrierung mit zwei Werten:  
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|Kategorie|REG\_SZ|GUID|Eine GUID erstellt, um die Kategorie zu identifizieren.|  
|Package|REG\_SZ|GUID|Die GUID des VSPackage\-Diensts, der die Kategorie unterstützt|  
  
 In der Registrierung angegebene Dienst muss eine Implementierung bereitstellen **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** für die entsprechende Gruppe.  
  
 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304\-a\_FontAndColorGroup")  
  
### IDE\-Unterstützung implementieren.  
 Implementieren [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), die gibt entweder eine [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) Schnittstelle oder ein **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** Schnittstelle für die IDE für jede Kategorie oder eine Gruppe von angegebenen GUID.  
  
 Für jede Kategorie unterstützt, ein VSPackage implementiert eine separate Instanz von der [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) Schnittstelle.  
  
 Durch die Methoden implementiert [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) müssen die IDE mit bereitstellen:  
  
-   Liste der Elemente in der Kategorie anzeigen  
  
-   Lokalisierbaren Namen für Anzeigeelemente  
  
-   Anzeigen von Informationen für jedes Element der Kategorie  
  
 **Hinweis:** jeder Kategorie muss mindestens ein Anzeigeelement enthalten.  
  
 Die IDE verwendet das **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** Schnittstelle, um eine Union von mehrere Kategorien definieren.  
  
 Seine Implementierung bietet die IDE mit:  
  
-   Eine Liste der Kategorien, die einer bestimmten Gruppe bilden  
  
-   Zugriff auf Instanzen von [einer IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) unterstützen jede Kategorie innerhalb der Gruppe  
  
-   Lokalisierbare Gruppennamen  
  
#### Aktualisieren der IDE  
 Die IDE speichert Informationen zu Schriftart und Farbe. Also nach jeder Änderung der Konfiguration IDE Schriftart und Farbe, um sicherzustellen, dass der Cache auf dem aktuellen Stand ist eine bewährte Methode.  
  
 Aktualisieren des Caches erfolgen über den [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) Schnittstelle und kann ausgeführte global oder nur auf ausgewählte Elemente.  
  
### Behandlung von Schriftart und Farbe ändern  
 Um ein VSPackage zeigt die farbliche Kennzeichnung von Text ordnungsgemäß unterstützen, muss die farbliche Kennzeichnung\-Dienst unterstützt das VSPackage auf benutzerinitiierte Änderungen über die Eigenschaftenseite für Schriftarten und Farben reagieren.  
  
 Zu diesem Zweck müssen ein VSPackage:  
  
-   **IDE ausgelöste Ereignisse behandeln** durch Implementieren der [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) Schnittstelle. Die IDE Ruft die entsprechende Methode, die folgenden benutzeränderungen an der Seite Schriftarten und Farben. Beispielsweise ruft die [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) Methode, wenn eine neue Schriftart ausgewählt ist.  
  
 **ODER**  
  
-   **abrufen, die IDE Änderungen**. Dies erfolgt über das System implementierter [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) Schnittstelle. Obwohl in erster Linie für die Unterstützung von Persistenz, die [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) Methode erhalten Informationen zu Schriftart und Farbe für Elemente anzeigen. Weitere Informationen zu Schriftart und Farbe Einstellungen finden Sie im MSDN\-Artikel [Zugriff auf gespeicherte Schriftart und Farbe Einstellungen](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
 **Hinweis:** verwenden, um sicherzustellen, dass die der Abfrageergebnisse richtig sind, die [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) Schnittstelle, um zu bestimmen, ob eine Entleerung des Cache und Aktualisierung benötigt werden, vor dem Aufrufen der Abrufmethoden, der die [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) Schnittstelle.  
  
#### Registrieren benutzerdefinierte Schriftart und Farbe Kategorie ohne Schnittstellen zu implementieren  
 Im folgenden Codebeispiel wird veranschaulicht, wie die benutzerdefinierte Schriftart und Farbe Kategorie ohne Schnittstellen zu implementieren:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window] "Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}" "Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" "ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}" "NameID"=dword:00000064  
```  
  
 **HINWEIS:**  
  
-   "NameID" die Ressourcen\-ID, der Namen der lokalisierten Kategorie im Paket \=  
  
-   "ToolWindowPackage" Paket\-GUID \=  
  
-   "Category" \= "{9FF46859\-A47E\-47bf\-8AC5\-EC3DBE69D1FE}" ist nur ein Beispiel und der tatsächliche Wert kann eine neue GUID durch die Implementierung bereitgestellt werden.  
  
### Legen Sie die Schriftart und Farbe Eigenschaftskategorie\-GUID  
 Das folgende Codebeispiel veranschaulicht das Festlegen der Category\-GUIDs.  
  
```  
// m_pView is your IVsTextView IVsTextEditorPropertyCategoryContainer spPropCatContainer = (IVsTextEditorPropertyCategoryContainer)m_pView; if (spPropCatContainer != null) { IVsTextEditorPropertyContainer spPropContainer; Guid GUID_EditPropCategory_View_MasterSettings = new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}"); hr = spPropCatContainer.GetPropertyCategory( ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer); if(hr == 0) { hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID); hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID); } }  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a> Daytona und Web\-GUI  
  
### Übersicht  
 "Daytona" ist ein Satz von APIs, Tools und Dienste, mit denen Benutzer zum Erstellen von Plug\-Ins mit HTML, CSS und JavaScript, die in einer Vielzahl von Hosts, z. B. Visual Studio oder F12 verwendet werden kann. Plug\-Ins bestehen eine portable Komponente, die in HTML, CSS und JavaScript geschrieben ist, und optional hostspezifische\-Komponenten. Jeder Host Daytona haben einen eigenen Satz von UI\-Konventionen, entweder implizit oder explizit, dass ein Plug\-in entsprechen muss, um systemeigene für seine Umgebung angezeigt. Einige Hosts, z. B. Visual Studio ermöglichen Endbenutzern, auf das "Standarddesign" ändern, sodass visuellen Aspekte der Host können nicht statisch verwendet werden, wenn Sie ein Stylesheet zu erstellen. Dies ist eine Herausforderung für Entwickler von portablen\-Plug\-Ins. In diesem Thema wird erläutert, wie zum Erstellen von Web\-Benutzeroberfläche in Visual Studio mit dem Daytona Host in einer Weise, die Designs und hohe Kontraste ordnungsgemäß unterstützt wird.  
  
### Daytona Designs Mechanismus  
 Die Daytona\-Runtime bietet eine Reihe von Diensten, die die UI\-Konventionen abstrahiert und Designs Funktionen des Hosts. Diese Dienste sicherzustellen, dass Plug\-Ins automatisch entsprechen, an den visual Erwartungen des Benutzers auf der Grundlage der Umgebung, in dem sie gehostet werden. Dieses Verhalten wird durch drei primäre Funktionen bereitgestellt:  
  
1.  Ein Common Language Runtime eingefügten Stylesheet \(plugin.css\), die transparent wendet einen Satz von CSS\-Regeln für ein Plug\-in\-Benutzeroberfläche und den Standardsatz von HTML\-Steuerelemente \(z. B. HTMLInputElement und HTMLButtonElement\-Stile  
  
2.  Einen Satz von Host bereitgestellte Token, die mit Werten, die anstelle von hartcodierten designbasierte Style\-Benutzeroberflächenelementen verwendet werden können  
  
    1.  eine deklarative Syntax für den Zugriff auf diese Token mit CSS  
  
    2.  eine API für den programmgesteuerten Zugriff auf Design\-Token aus JavaScript  
  
3.  Benachrichtigung über Designänderungen  
  
#### Common Language Runtime eingefügten Stylesheet  
 Die Koordinaten Daytona Common Language Runtime mit dem Host einen Stil einfügen Blatt zur automatischen Designs standardmäßiger Benutzeroberflächenelemente eines Plug\-Ins. Dies umfasst Stil für den folgenden Konzepten:  
  
-   Umgebungsschriftart  
  
-   Hintergrundfarben  
  
-   Hyperlinks  
  
-   Formularsteuerelemente \(z. B.: \< auswählen \>, \< input \>, \< Schaltfläche \>  
  
-   Tabellen  
  
-   Überschriften  
  
-   Bildlaufleisten  
  
 Dies bedeutet, dass ausschließlich aus standardmäßigen HTML\-UI\-Steuerelemente die Benutzeroberfläche umfasst, dann keine zusätzliche Arbeit und Designänderungen richtig beantworten und zur Unterstützung hoher Kontrast benötigt werden sollte.  
  
#### Benutzerspezifische UI  
 In fast allen nicht trivialen Fall werden die Standard\-HTML\-UI\-Steuerelemente für die Bereitstellung einer vollständigen für ein Plug\-in, und benutzerdefinierte Benutzeroberfläche muss eingeführt werden. Um die richtige Schriftart Auswahl und Farbe verwenden, unterstützen **Design Token** sollte in CSS deklarativ oder imperativ über die JavaScript\-API, die unten beschriebenen verwendet werden. Die Laufzeit Daytona übernimmt die Stylesheets, die diese Token auf der Auslastungstest\-Plug\-Ins und Designänderungen aktualisieren.  
  
##### Design\-Token  
 Beide Standard\- und hostspezifische Design Token sind verfügbar. Standardmäßige Token sind Host eingefügt und immer verfügbar. Es ist vorzuziehen, möglichst immer die standard\-Token verwenden. Standardtokens garantiert von allen Daytona Hosts bereitgestellt werden, und deren Verwendung Ihr Plug\-in ist grundsätzlich besser portierbar. Der Satz von standard\-Token ist unterliegen, obwohl nur neue Token hinzugefügt werden soll und keine entfernt werden soll. Die Visual Studio 2013\-Version wird unten beschrieben:  
  
|Wenn Sie den Namen|Beschreibung|  
|------------------------|------------------|  
|Plug\-in\-Hintergrundfarbe|Die Standardhintergrundfarbe für das Plug\-in|  
|Plug\-in\-Farben|Die Standardvordergrundfarbe für das Plug\-in|  
|Plug\-in\-Contextmenu\-aktiv\-Farben|Die Auswahl Standardvordergrundfarbe für Kontextmenüs, wenn sie aktiv sind \(den Fokus haben\)|  
|Plug\-in\-Contextmenu\-Hintergrundfarbe|Die Standardhintergrundfarbe für Kontextmenüs|  
|Plug\-in\-Contextmenu\-Rahmenfarbe|Die Standard\-Rahmenfarbe für Kontextmenüs|  
|Plug\-in\-Contextmenu\-Farben|Die Standardvordergrundfarbe für Kontextmenüs|  
|Plug\-in\-Contextmenu\-Hover\-Farben|Die Standardhintergrundfarbe für Hover für Kontextmenüs|  
|Plug\-in\-Contextmenu\-Hover\-Text\-Farben|Die Standardvordergrundfarbe für Hover für Kontextmenüs|  
|Plug\-in\-Contextmenu\-Symbol\-Kontrollkästchen|Das Kontrollkästchen Symbol Standardfarbe für die Kontextmenüs|  
|Plug\-in\-Contextmenu\-inaktiv\-Text\-Farben|Die Auswahl Standardvordergrundfarbe für Kontextmenüs, wenn sie inaktiv sind|  
|Plug\-in\-Contextmenu\-trennzeichenfarbe|Die Standardfarbe für Trennzeichen für Kontextmenüs|  
|Plug\-in\-Font\-family|Die standardmäßige Schriftfamilie für das Plug\-in verwenden|  
  
 In Visual Studio die folgenden Plug\-in\-Schriftart\-Token auf die Umgebung Schriftart basieren:  
  
-   Plug\-in\-Font\-size  
  
-   Plug\-in\-Font\-weight  
  
-   Plug\-in\-Hintergrund Hervorhebungsfarbe  
  
-   Hervorhebungsfarbe\-Plug\-in  
  
-   Plug\-in\-inaktive\-Farben  
  
 Formatieren von HTMLElements \(links\) werden die folgenden Plug\-in\-Link\-Token verwendet:  
  
-   Linkfarbe\-Plug\-in  
  
-   Plug\-in\-aktive Linkfarbe  
  
-   Plug\-in\-Hover Linkfarbe  
  
 Plugin.CSS Stile Bildlaufleisten, die standardmäßig mithilfe der folgenden Tokens, um eine bessere Unterstützung der Designs in den verschiedenen Hosts \(insbesondere Visual Studio\):  
  
-   Plug\-in\-Scrollbar\-Pfeil\-Farben  
  
-   Plug\-in\-Scrollbar\-Hintergrundfarbe  
  
-   Plug\-in\-Scrollbar\-Face\-color  
  
 Die folgenden Plug\-in\-Select\-Token werden verwendet, um die HTMLSelectElement \(Combobox Dropdown\) formatieren:  
  
-   Plug\-in\-Select\-Option\-Hintergrundfarbe  
  
-   Plug\-in\-Select\-Option\-color  
  
-   Plugin\-Select\-Option\-Checked\-Background\-Color  
  
-   Plugin\-Select\-Option\-Checked\-Border\-Color  
  
-   Plugin\-Select\-Option\-Checked\-Foreground\-Color  
  
-   Plugin\-Select\-Option\-Hover\-Background\-Color  
  
-   Plugin\-Select\-Option\-Hover\-Border\-Color  
  
-   Plugin\-Select\-Option\-Hover\-Foreground\-Color  
  
-   Plug\-in\-wählen\-Rahmenfarbe  
  
-   Plug\-in\-wählen\-Hintergrundfarbe  
  
-   Plug\-in\-wählen\-Vordergrundfarbe  
  
-   Plug\-in\-wählen\-Hover\-Hintergrundfarbe  
  
-   Plug\-in\-wählen\-Hover\-Border\-color  
  
-   Plug\-in\-wählen\-Hover\-\-Vordergrundfarbe  
  
-   Plug\-in\-Tabelle\-Rahmenfarbe  
  
-   Plug\-in\-Tabelle\-Header\-Hintergrundfarbe  
  
-   Plug\-in\-Header\-Hintergrundfarbe  
  
-   Plug\-in\-Textbox\-Rahmenfarbe  
  
-   Plug\-in\-Textbox\-Hintergrundfarbe  
  
-   Plug\-in\-Textbox\-Farben  
  
-   Plug\-in\-Textbox\-deaktiviert\-Hintergrundfarbe  
  
-   Plug\-in\-Textbox\-Disabled\-Border\-color  
  
-   Plug\-in\-Textbox\-deaktiviert\-Farben  
  
 Diese Token sollte verwendet werden, für die *alle* Sichten und Tabellen, Struktur, weil sie die richtigen Standardeinstellungen in den verschiedenen Hosts auf die Unterstützung von Designs und hohen Kontrast festgelegt haben:  
  
-   Plug\-in\-Treeview\-Inhalt\-Hintergrundfarbe  
  
-   Plug\-in\-Treeview\-Inhalt\-Farben  
  
-   Plugin\-TreeView\-Content\-inactive\-Selected\-Color  
  
-   Plugin\-TreeView\-Content\-Mouseover\-Background\-Color  
  
-   Plug\-in\-Treeview\-Inhalt\-Mouseover\-Farbe  
  
-   Plugin\-TreeView\-Content\-inactive\-Selected\-Color  
  
-   Plugin\-TreeView\-Content\-Selected\-Background\-Color  
  
-   Plugin\-TreeView\-Content\-Selected\-Border\-Color  
  
-   Plug\-in\-Treeview\-Inhalt\-\-Farbe  
  
##### Hostspezifische Token  
 Zusätzlich zur Unterstützung des Standardsatz von Token, können Hosts auch nicht dem Standard entsprechende Token enthalten. Der Visual Studio\-Host geschieht, indem das Plug\-in Design token Aliase in einem Visual Studio\-spezifischen Abschnitt des Manifests angeben. Zum Beispiel:  
  
```  
"vs": { "theme_token_aliases": { "diagnostics-host-border": { "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22", "key_type": "BackgroundColor", "name": "Border" }, ... } }  
  
```  
  
 In diesem Beispiel führt ein Design Token, mit dem Namen "Diagnose\-Host\-Rahmen," das identisch zu den oben genannten Standardtokens verwiesen werden kann. Die Kategorie, Key\_type und Namen werden verwendet, die Farbe durch Auflösen der **IVsFontAndColorStorage** Schnittstelle. In vielen Fällen ist es möglich ist, finden entsprechende Farben \(zusammen mit der Kategorie, Key\_type und Informationen über den Namen\) in der XML\-Dateien im Vscommon\\themes. Durch denselben Mechanismus wird verwendet, wenn das Paket neue konfigurierbare Farben eingeführt: entsprechen der Kategorie, Key\_type und Namen, um die Farbe, die Sie verwenden möchten. \-Plug\-in\-Autoren sollten möglichst Standardtokens verwenden und nur verwenden hostspezifische\-Token, wenn es absolut notwendig.  
  
##### Verwenden von Designs Token in CSS  
 Design\-Token werden über eine speziell formatierte Kommentarsyntax bezeichnet. Die Regeln für das token analysieren:  
  
1.  Der Kommentarausdruck muss in eckige Klammern eingeschlossen werden \(**\[\]**\).  
  
2.  Alle Leerstellen innerhalb des Kommentars, jedoch außerhalb der Ausdruck wird ignoriert.  
  
3.  Der Kommentarausdruck muss direkt die Eigenschaft, die sie ersetzt.  
  
4.  Alle führenden oder nachgestellten Leerzeichen innerhalb des Ausdrucks werden entfernt.  
  
5.  Jedes token Namen innerhalb des Ausdrucks in geschweiften Klammern eingeschlossen werden muss \(z. B. **{Font\-Family}** und **{Schaltfläche\-Hover\-Color}**\). Andernfalls wird es als literaler Wert behandelt.  
  
 Im folgenden sind Beispiele für wie der token\-Parser CSS vorausgesetzt, dass ersetzen, wird der **\-Plug\-in\-Background\-Color** Token hat den Wert \#000 und **\-Plug\-in\-Font\-Family** Token hat den Wert "Verdana".  
  
|Erstellte CSS|Analysierte CSS|Notizen|  
|-------------------|---------------------|-------------|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #000;`|Der Standardwert wird mit dem dynamischen hostspezifische Wert ersetzt.|  
|`background-color: #fff; /*   [{plugin-background-color}]   */`|`background-color: #000;`|Der Leerraum außerhalb des Ausdrucks wird ignoriert.|  
|`background-color: #fff; /*[   {plugin-background-color}   ]*/`|`background-color: #000;`|Die nachfolgende und führende Leerzeichen innerhalb des Ausdrucks wird entfernt.|  
|`background-color: #fff; /*{plugin-background-color}*/`|`background-color: #fff;`|Der Ausdruck ist nicht in eckige Klammern eingeschlossen, und daher wird der Kommentar ignoriert.|  
|`background-color: #fff; /*[plugin-background-color]*/`|`background-color: plugin-background-color;`|Das Token ist nicht in geschweifte Klammern eingeschlossen und wird daher als literaler Wert behandelt.|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|Der Kommentar folgt nicht den Wert der Eigenschaft und wird daher ignoriert.|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #fff;`|*Wie oben*|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|*Wie oben*|  
|`font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/`|`font-family: Verdana, sans-serif;`|Das Token ersetzt wird, und der Literale Inhalt wird beibehalten.|  
|`background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/`|`background-image: linear-gradient(0% #000, 100% #000);`|*Wie oben*|  
  
 Eine CSS\-Datei enthält das Design Token darf es durch das Attribut Data\-Plug\-in\-Design auf die Link\-Elements in der HTML\-Datei gekennzeichnet werden. Zum Beispiel:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```  
  
##### Design\-Token aus JavaScript  
 Benutzerdefinierte Benutzeroberfläche versehene CSS, soweit möglich sein soll, gibt es Szenarien, wenn der Wert eines Designs token muss programmgesteuert zugegriffen werden. Z. B. wenn die benutzerdefinierte Benutzeroberfläche auf einem CanvasElement gezeichnet wird, die Formatierung von CSS erben nicht oder ein Element der Benutzeroberfläche dynamisch wird anstatt Stylesheets erstellt werden. Die Szenarien werden mithilfe der API Daytona aktiviert **Plugin.Theme.getValue**. Diese Funktion gibt einen Host bereitgestellte Designwert, wenn ein token erhält.  
  
|Nicht mit Design|Design|  
|----------------------|------------|  
|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = "#ccc"; surface.fillRect(0, 0, 200, 200);`|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = ("plugin-background-color"); surface.fillRect(0, 0, 200, 200);`|  
|`var el = document.createElement("div"); el.style.backgroundColor = "#ccc";`|`var el = document.createElement("div"); el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");`|  
  
 Wenn Token aus JavaScript verwendet werden**, das Änderungsereignis Design muss behandelt werden, um auf Updates reagieren**. Dies ist nicht für Design\-Token, die deklarativ in CSS verwendet werden, wie die Runtime Daytona es für das Plug\-in übernimmt. Die Design\-Ereignis kann auf folgende Weise behandelt werden:  
  
|Member \(einzelner Handler\)|DOM\-Ereignis \(mehrere Handler\)|  
|----------------------------------|---------------------------------------|  
|`Plugin.Theme.onchange = function () { // re-draw dynamic UI here }`|`Plugin.Theme.addEventListener("change", function () { // re-draw dynamic UI here });`|  
  
 In diesem Fall ist es wäre sehr häufig erneut aufrufen, **Plugin.Theme.getValue** in diesen Handler als Wert für die Design\-Token, die wahrscheinlich geändert, wenn das Design geändert.  
  
##### Standard\-token\-Zuordnung  
 Die standard\-Token werden Umgebung und Shell Farben zugeordnet. Die unten aufgeführte Liste bietet eine Sorte, was diese Zuordnungen sind.  
  
|Wenn Sie den Namen|VS\-Zuordnung \(EnvironmentColors\)|  
|------------------------|-----------------------------------------|  
|Plug\-in\-Farben|ToolWindowTextColorKey|  
|Plug\-in\-Hintergrundfarbe|ToolWindowBackgroundColorKey|  
|Linkfarbe\-Plug\-in|ControlLinkTextColorKey|  
|Plug\-in\-Hover Linkfarbe|ControlLinkTextHoverColorKey|  
|Plug\-in\-aktive Linkfarbe|ControlLinkTextPressedColorKey|  
|Hervorhebungsfarbe\-Plug\-in|HighlightTextColorKey|  
|Plug\-in\-Hintergrund Hervorhebungsfarbe|HighlightColorKey|  
|Plug\-in\-Tabelle\-Header\-Hintergrundfarbe|GridHeadingBackgroundColorKey|  
|Plug\-in\-Header\-Hintergrundfarbe|GridHeadingTextColorKey|  
|Plug\-in\-Tabelle\-Rahmenfarbe|GridLineColorKey|  
|Plug\-in\-Schaltfläche\-Hintergrundfarbe|ButtonFaceColorKey|  
|Plug\-in\-Schaltfläche\-Hover\-Hintergrundfarbe|ButtonHighlightColorKey|  
|Schaltflächenfarbe\-Plug\-in|ButtonTextColorKey|  
|Plug\-in\-Schaltfläche\-Rahmenfarbe|ButtonBorderColorKey|  
  
##### Designänderungen  
 Der Visual Studio\-Host Trigger\-Plug\-Ins Design ändert sich, wenn ein Endbenutzer werden Änderungen an den folgenden Einstellungen:  
  
 **Farbschema:**  
  
 ![Color theme changes](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305\-a\_ColorTheme")  
  
 **Design der Umgebung:**  
  
 ![Environment theme changes](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305\-b\_EnvironmentTheme")  
  
 **Betriebssystem Design** \(nur bei zu und von hohem Kontrast zu ändern\):  
  
 ![OS theme changes](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305\-c\_OSTheme")