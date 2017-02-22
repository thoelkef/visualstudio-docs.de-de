---
title: "Behandlung von Problemen der DPI-Wert | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Behandlung von Problemen der DPI-Wert
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine zunehmende Anzahl von Geräten werden mit "Auflösung" Bildschirmen ausgeliefert. Diese Seiten haben in der Regel mehr als 200 Pixel pro Zoll \(Ppi\). Arbeiten mit einer Anwendung auf diesen Computern benötigen Inhalt skaliert werden, um den Bedürfnissen von Anzeigen des Inhalts in eine geglättete Abstand für das Gerät. Ab 2014 ist die primäre Zielgruppe für eine HD\-mobile Geräte \(Tablets, Schalenkoffer Laptops und Smartphones\) zu berechnen.  
  
 Windows 8.1 und höher enthält zahlreiche Features, aktivieren diese Computer mit zeigt und Umgebungen, in dem der Computer ist sowohl HD\-zugeordnet und Standard\-Dichte zeigt gleichzeitig, arbeiten.  
  
-   Windows kann können Sie Inhalt an das Gerät mithilfe des "Stellen Text und andere Elemente vergrößern oder verkleinern" \(verfügbar seit Windows XP\) festlegen.  
  
-   Windows 8.1 und höher werden automatisch Inhalt für die meisten Anwendungen konsistent, wenn zwischen unterschiedlichen der Dichte von Pixel skaliert. Wenn die primäre Anzeige hohe Dichte \(200 % Skalierung ist\) und die sekundäre Anzeige ist standard Dichte \(100 %\), wird Windows automatisch der Fensterinhalt für die Anwendung auf dem sekundären \(1 Pixel für alle 4 Pixeln gerendert, die von der Anwendung angezeigt wird\) abwärts skalieren.  
  
-   Windows standardmäßig rechts Skalierung für die Pixeldichte und Abstand für die Anzeige \(Windows 7 und höher, OEM\-konfigurierbar\) anzeigen.  
  
-   Windows kann automatisch Inhalt oben auf 250 % auf neuen Geräten skalieren, die 280 Ppi \(ab Windows 8.1 S14\) überschreiten.  
  
 Windows verfügt über eine Möglichkeit für den Umgang mit skalieren UI erhöhte Pixel Anzahlen nutzen. Eine Anwendung verwendet dieses System durch Deklarieren selbst "System DPI\-bewusst." Programme, die dies nicht tun werden vom System skaliert. Dies kann zu einer "für die Fuzzysuche" der Benutzeroberfläche führen, in dem die gesamte Anwendung gleichmäßig auf die Pixel gestreckt wird. Zum Beispiel:  
  
 ![DPI&#45;Probleme unscharf](../extensibility/media/dpi-issues-fuzzy.png "DPI Issues Fuzzy")  
  
 Visual Studio verwendet DPI\-Skalierung unterstützt wird und daher nicht "virtualisiert."  
  
 Windows nutzen \(Visual Studio\), mehrere UI\-Technologien, die unterschiedliche Methoden für den Umgang mit Skalierungsfaktoren vom System festgelegt haben. Zum Beispiel:  
  
-   WPF misst die Steuerelemente in einer Weise geräteunabhängige \(Einheiten, nicht in Pixel\). WPF UI skaliert automatisch für den aktuellen DPI\-Wert.  
  
-   Alle Textgrößen unabhängig von Benutzeroberflächen\-Framework werden in Punkt ausgedrückt und daher vom System als DPI\-unabhängige behandelt. Text in Win32, WinForms und WPF bereits Skalierung ordnungsgemäß, wenn auf dem Bildschirm gezeichnet.  
  
-   Win32\/WinForms\-Dialogfeldern und Fenstern haben die Möglichkeit für die Aktivierung von Layouts, das mit Text – z. B. durch Raster, Datenfluss und Tabelle LayoutPanel\-Elemente ändert. Diese ermöglichen das Vermeiden von hartcodierten Pixelpositionen, die nicht skaliert werden, wenn die Schriftgrade erhöht werden.  
  
-   Symbole, die vom System bereitgestellten oder Ressourcen basierend auf der Systemmetriken \(z. B. SM\_CXICON zugeordnet und SM\_CXSMICON zugeordnet\) sind bereits skaliert.  
  
## Ältere Win32 \(GDI, GDI \+\) und WinForms\-basierte Benutzeroberfläche  
 Während WPF bereits hohe DPI\-bewusst ist, wurde unser Code Win32\/GDI\-basierte nicht ursprünglich mit DPI\-Unterstützung Bedenken geschrieben. Windows stellt APIs DPI\-Skalierung zur Verfügung. Updates für Win32\-Probleme sollten konsistent innerhalb des Produkts verwenden. Visual Studio verfügt über ein Hilfsprogramm bereitgestellt Klassenbibliothek um Funktionen dupliziert und Konsistenz des Produkts zu vermeiden.  
  
## Hochauflösende Bilder  
 Dieser Abschnitt ist in erster Linie für Entwickler Erweitern von Visual Studio 2013. Verwenden Sie für Visual Studio 2015 Abbilder, die in Visual Studio integriert ist. Möglicherweise finden Sie auch, dass Sie Support\-Ziel viele Versionen von Visual Studio und daher in 2015 mit dem Image\-Dienst ist nicht möglich, da sie in früheren Versionen nicht vorhanden ist. In diesem Abschnitt wird auch dann für Sie.  
  
## Skalieren von Bildern, die zu klein sind.  
 Bilder, die zu klein sind, können "skaliert" und auf GDI und einige allgemeine Methoden WPF gerendert werden. Verwaltete DPI\-Hilfsklassen sind für interne und externe Visual Studio Integratoren Adresse Skalierung, Symbole, Bitmaps, Imagestrips und Imagelists verfügbar. Win32\-basierte systemeigene C \/ C \+\+ Hilfsprogramme für die Skalierung HICON, HBITMAP, HIMAGELIST und VsUI::GdiplusImage verfügbar sind. Skalieren einer Bitmap in der Regel erfordert nur eine einzeilige Änderung nach dem einschließen eines Verweises auf die Bibliothek. Zum Beispiel:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```c#  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Skalieren einer Imagelist, hängt davon ab, ob die Imagelist zur Ladezeit abgeschlossen ist, oder zur Laufzeit angefügt wird. Wenn beim Laden der abgeschlossen ist, rufen Sie LogicalToDeviceUnits\(\) mit der Imagelist wie eine Bitmap. Wenn der Code eine einzelne Bitmap zu laden, bevor Sie die Imagelist verfassen muss, stellen Sie sicher, die Bildgröße der Imagelist skalieren:  
  
```c#  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 In systemeigenem Code können die Dimensionen skaliert wird, wenn die Imagelist wie folgt erstellen:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funktionen in der Bibliothek ermöglichen, die beim Ändern der Größe Algorithmus angibt. Beim Skalieren Bilder in Imagelists, platziert werden sollten Sie die Hintergrundfarbe festlegen, die für die Transparenz verwendet wird oder NearestNeighbor Skalierung \(wodurch Verzerrung 125 % und 150 %\) verwenden.  
  
 Wenden Sie sich an den <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> \-Dokumentation auf MSDN.  
  
 Die folgende Tabelle zeigt Beispiele für wie Bilder mit entsprechenden DPI skaliert werden soll, Skalierungsfaktoren. Die Bilder in Grün bezeichnen unsere best Practice ab Visual Studio 2013 \(100 – 200 % DPI\-Skalierung\):  
  
 ![DPI&#45;Probleme beim Skalieren](../extensibility/media/dpi-issues-scaling.png "DPI Issues Scaling")  
  
## Probleme mit dem Layout  
 Layoutprobleme können vermieden werden, in erster Linie durch die Punkte in der Benutzeroberfläche skaliert und relativ zueinander positioniert halten statt mit absoluten Speicherorte \(insbesondere in Pixeleinheiten\). Zum Beispiel:  
  
-   Layout\/Textpositionen müssen Konto für die Skalierung von Bildern anpassen.  
  
-   Spalten im Raster müssen Breiten für den erweiterten Text angepasst haben.  
  
-   Fest programmierte Größen oder der Abstand zwischen Elementen müssen auch skaliert werden. Größen, die nur für Text Dimensionen basieren sind in der Regel in Ordnung, da Schriftarten automatisch skaliert werden.  
  
 Hilfsfunktionen stehen in der <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> Klasse, um die Skalierung auf der X\- und Y\-Achse zu ermöglichen:  
  
-   LogicalToDeviceUnitsX\/LogicalToDeviceUnitsY \(Funktionen ermöglichen die Skalierung für die X \/ Y\-Axis\)  
  
-   Int Speicherplatz \= DpiHelper.LogicalToDeviceUnitsX \(10\);  
  
-   Int\-Height \= VsUI::DpiHelper::LogicalToDeviceUnitsY\(5\);  
  
 Es gibt Überladungen der LogicalToDeviceUnits zu skalieren von Objekten wie z. B. Rect, Punkt und Größe.  
  
## Mithilfe der DPIHelper Library\/Klasse zum Skalieren von Bildern und layout  
 Die Visual Studio\-DPI\-Hilfsbibliothek steht in systemeigenen und verwalteten bereit und kann von einer anderen Anwendung außerhalb der Visual Studio\-Shell verwendet werden.  
  
 Um die Bibliothek zu verwenden, rufen Sie die [Visual Studio VSSDK Erweiterbarkeitsbeispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples) und Klonen das hohe DPI\_Images\_Icons\-Beispiel  
  
 Enthalten Sie in Quelldateien VsUIDpiHelper.h, und rufen Sie die statischen Funktionen der VsUI::DpiHelper\-Klasse:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Verwenden Sie nicht die Hilfsfunktionen in auf Modulebene oder Klassenebene statischen Variablen. Die Bibliothek verwendet auch statische Variablen für die Threadsynchronisierung und Sie möglicherweise treten Probleme auf Order\-Initialisierung. Konvertieren Sie diese Mehrdeutigkeit in nicht statischen Membervariablen, oder in einer Funktion umschlossen Sie \(damit sie beim ersten Zugriff konstruiert werden\).  
  
 Um die DPI\-Hilfsfunktionen in verwaltetem Code zugreifen zu können, die in Visual Studio\-Umgebung ausgeführt wird:  
  
-   Das betreffende Projekt muss es sich um die neueste Version der Shell MPF verweisen. Zum Beispiel:  
  
    ```c#  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Stellen Sie sicher, das Projekt enthält Verweise auf **System.Windows.Forms**, **PresentationCore**, und **PresentationUI**.  
  
-   Verwenden Sie im Code die **Microsoft.VisualStudio.PlatformUI** \-Namespace, und rufen eine statische Funktionen DpiHelper\-Klasse. Unterstützte Typen \(Punkte, Größen, Rechtecke, usw.\) sind bereitgestellt Erweiterungsfunktionen, die neue zurückgeben Objekte skaliert. Zum Beispiel:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## Umgang mit WPF Bild Unschärfe in zoombarem\-Benutzeroberfläche  
 In WPF werden Bitmaps automatisch angepasst, von WPF für den aktuellen DPI Zoomfaktor mithilfe eines Algorithmus für hochwertige Bikubisch \(Standard\), eignet sich gut für Bilder oder große Screenshots, aber ist für die Elementsymbole Menü ungeeignet, da dies die wahrgenommene Unschärfe führt.  
  
 Empfehlung:  
  
-   Für die Logo\-Bild und Banner\-Grafik, die Standardeinstellung <xref:System.Windows.Media.BitmapScalingMode> Größe Modus verwendet werden.  
  
-   Für Menüelemente und ikonographie Bilder die <xref:System.Windows.Media.BitmapScalingMode> sollte verwendet werden, wenn dies nicht andere Artefakte Verzerrung um Unschärfe \(auf 200 % und 300 %\) zu entfernen.  
  
-   •	Für große Zoom Ebenen nicht ein Vielfaches von 100 % \(z. B. 250 % oder 350 %\) führt skalieren ikonographie mit Bikubisch fuzzy, Ausgeblichene Benutzeroberfläche. Ein besseres Ergebnis wird abgerufen, indem zuerst das Bild mit NearestNeighbor das größte Vielfache von 100 % \(z. B. 200 % oder 300 %\) skalieren und mit Bikubisch von dort aus. Finden Sie unter Sonderfall: prescaling WPF\-Images für große DPI\-Level für Weitere Informationen.  
  
 Die DpiHelper\-Klasse im Namespace Microsoft.VisualStudio.PlatformUI bietet Mitglied <xref:System.Windows.Media.BitmapScalingMode> die für die Bindung verwendet werden kann. Die Visual Studio\-Shell Skalierungsmodus über das Produkt gleichmäßig, abhängig von der DPI\-Skalierungsfaktor Bitmap steuern können.  
  
 Fügen Sie in XAML zu verwenden Folgendes hinzu:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Die Visual Studio\-Shell wird diese Eigenschaft bereits für Fenster der obersten Ebene und Dialogfelder. WPF\-basierte Benutzeroberfläche in Visual Studio ausführen erbt es bereits. Wenn die Einstellung nicht an Ihre bestimmte Teile der Benutzeroberfläche weitergegeben wird, kann es für das Stammelement der XAML\/WPF\-Benutzeroberfläche festgelegt werden. Orte, wo dies geschieht, umfassen Popups für Elemente mit Win32\-Eltern, und Designerfenstern, die ausgeführt werden, der zu verarbeiten, z. B. Blend.  
  
 Einige Elemente der Benutzeroberfläche kann unabhängig von der System\-Set DPI Zoomstufe, z. B. die Visual Studio\-Texteditor und WPF\-basierte Designer \(WPF\-Desktop und Windows Store\) skaliert werden. In diesen Fällen sollte DpiHelper.BitmapScalingMode nicht verwendet werden. Zur Behebung dieses Problems im Editor die IDE\-Team erstellt eine benutzerdefinierte Eigenschaft mit dem Titel RenderOptions.BitmapScalingMode. Dieser Eigenschaftswert auf HighQuality oder NearestNeighbor festgelegt, abhängig von der kombinierten Zoomstufe des Systems und Ihre Benutzeroberfläche.  
  
## Sonderfall: prescaling WPF\-Images für große DPI\-Ebenen  
 Für sehr große Zoomfaktoren, die ein Vielfaches von 100 % \(z. B. 250 %, 350 % usw.\) sind, skalieren ikonographie mit Bikubisch fuzzy, Ausgeblichene Benutzeroberfläche führt. Der Eindruck dieser Bilder neben schärfer Text ist fast wie eine optische Illusion. Die Bilder angezeigt werden, die näher zu und unscharf in Bezug auf den Text sein. Skalierung Ergebnis in dieser vergrößerten Größe kann verbessert werden, indem zuerst das Bild mit NearestNeighbor das größte Vielfache von 100 % \(z. B. 200 % oder 300 %\) skalieren und mit Bikubisch auf den verbleibenden \(zusätzliche 50 %\).  
  
 Im folgenden ist ein Beispiel für die Unterschiede in den Ergebnissen, in dem das erste Bild skaliert wird\-Algorithmus mit den verbesserten Double Skalierung 100 % \-\> 200 % \> 250 %, und das zweite Argument nur mit Bikubisch 100 %\-250 % \>.  
  
 ![DPI Issues Double Scaling Example](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Issues Double Scaling Example")  
  
 Damit können die Benutzeroberfläche zum Anzeigen jedes Bildelement diese Double Skalierung, die XAML\-Markup müssen geändert werden. Die folgenden Beispiele veranschaulichen die Verwendung von Double\-Skalierung in WPF in Visual Studio mit der DpiHelper\-Bibliothek und Shell.12\/14.  
  
 Schritt 1: Das Bild auf 200 %, 300 % Prescale usw. NearestNeighbor verwenden.  
  
 Prescale das Bild mit entweder einen Konverter für eine Bindung oder mit einer XAML\-Markuperweiterung angewendet. Zum Beispiel:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Wenn das Bild auch versehene werden muss \(die meisten, wenn nicht alle sollte\), das Markup können Sie einen anderen Konverter, der zuerst Designs auf das Bild und dann vorab Skalierung ist. Das Markup können entweder <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> oder <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, je nachdem, auf die gewünschte Konvertierung\-Ausgabe.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Schritt 2: Stellen Sie sicher, dass die endgültige Größe für den aktuellen DPI\-Wert korrekt ist.  
  
 Da WPF die Benutzeroberfläche für den aktuellen DPI\-Wert mithilfe der BitmapScalingMode\-Eigenschaft, legen Sie für das "UIElement" skaliert wird, sollten ein Image\-Steuerelement mit einem prescaled\-Image, als Quelle zwei oder drei Mal größer ist als es aussieht. Im folgenden sind einige Möglichkeiten, diesen Effekt zu begegnen:  
  
-   Wenn Sie die Dimension des ursprünglichen Bilds bei 100 % kennen, können Sie die genaue Größe des Bild\-Steuerelements angeben. Diese Größe wider, dass die Größe der Benutzeroberfläche vor der Skalierung angewendet wird.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Wenn die Größe des ursprünglichen Bilds nicht bekannt ist, kann ein LayoutTransform skalieren Sie das endgültige Image\-Objekt verwendet werden. Zum Beispiel:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## Aktivieren der Unterstützung für anzeigen auf das WebOC  
 In der Standardeinstellung aktivieren nicht WebOC\-Steuerelemente \(z. B. das WebBrowser\-Steuerelement in WPF oder IWebBrowser2\-Schnittstelle\) HDPI\-Erkennung und Support. Das Ergebnis wird ein eingebettetes Steuerelement mit Inhalt angezeigt werden, die auf einem Bildschirm mit hoher Auflösung zu klein ist. Im folgenden wird beschrieben, wie hohe DPI\-Unterstützung in einem bestimmten Web\-WebOC\-Instanz aktivieren.  
  
 Die IDocHostUIHandler\-Schnittstelle implementieren \(finden Sie im MSDN\-Artikel auf der [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) Schnittstelle\):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 Implementieren Sie optional die ICustomDoc\-Schnittstelle \(finden Sie im MSDN\-Artikel auf der [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) Schnittstelle\):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Ordnen Sie die Klasse, die das WebOC Dokument IDocHostUIHandler implementiert. Wenn Sie die oben genannten ICustomDoc\-Schnittstelle implementiert, hat als das WebOC Document\-Eigenschaft gültig ist, wird in ein ICustomDoc umwandeln und Aufrufen der SetUIHandler\-Methode und übergeben die Klasse, die IDocHostUIHandler implementiert.  
  
```c#  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Wenn Sie die ICustomDoc\-Schnittstelle nicht implementiert wurde, klicken Sie dann müssen, sobald das WebOC Document\-Eigenschaft gültig ist, wird Sie es IOleObject umgewandelt, und rufen die SetClientSite\-Methode und übergeben die Klasse, die IDocHostUIHandler implementiert. Legen Sie das DOCHOSTUIFLAG\_DPI\_AWARE\-Flag für die DOCHOSTUIINFO an die GetHostInfo\-Methode übergeben:  
  
```c#  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Dies sollte alles sein, die Sie benötigen, damit Ihre WebOC Steuerelement HPDI unterstützen.  
  
## Tipps  
  
1.  Wenn die Eigenschaft für das WebOC\-Steuerelement geändert wird, müssen Sie das Dokument mit der Klasse IDocHostUIHandler neu zuordnen.  
  
2.  Wenn die oben genannten nicht funktioniert, ist ein bekanntes Problem mit der WebOC nicht auswählen, die Änderung der DPI\-Flag. Die verlässlichste Möglichkeit zur Lösung dieses Problems ist die optischen Zoom die WebOC Bedeutung zwei Aufrufe mit zwei verschiedene Werte für den Zoomfaktor aktivieren bzw. deaktivieren. Darüber hinaus ist diese Lösung erforderlich, es für die Durchführung bei jedem Aufruf navigieren möglicherweise erforderlich.  
  
    ```c#  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```