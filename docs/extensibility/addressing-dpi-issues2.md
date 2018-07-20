---
title: Adressierung DPI wichtigsten Themen2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97012b0d8b4214cdeafcaf12403948997436a212
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154329"
---
# <a name="address-dpi-issues"></a>DPI-Probleme
Eine zunehmende Anzahl von Geräten, die mit "hochauflösende" Bildschirme geliefert werden. Diese Seiten müssen in der Regel mehr als 200 Pixel pro Zoll (Ppi). Inhalt hochskaliert werden, auf die Anforderungen zum Anzeigen des Inhalts in einer normalen Ansicht Entfernung für das Gerät wird das Arbeiten mit einer Anwendung auf diesen Computern erforderlich. Seit 2014 ist die primäre Zielgruppe für anzeigen mit hoher Dichte mobiler Geräte (Tablets, Schalenkoffer Laptops und Smartphones) zu berechnen.  
  
 Windows 8.1 und höher enthält zahlreiche Funktionen, die diese Computer angezeigt und Umgebungen, in dem der Computer verbunden ist, sowohl mit hoher Dichte und Standard-Dichte angezeigt wird, zur gleichen Zeit, zu aktivieren.  
  
-   Windows kann es Ihnen ermöglichen, Inhalte werden skaliert und an das Gerät mithilfe der "Mach Text und andere Elemente vergrößert oder verkleinert" (verfügbar seit Windows XP) festlegen.  
  
-   Windows 8.1 und höher werden automatisch für die meisten Anwendungen konsistent, wenn zwischen der Anzeige von unterschiedlichen Pixel dichten verschoben sein Inhalt skaliert. Wenn die primäre Anzeige hohe Dichte (200 % Skalierung ist), und die sekundären Anzeige ist standard Dichte (100 %), Windows wird automatisch Herunterskalieren der Fensterinhalt der Anwendung auf dem sekundären (1-Pixel angezeigt wird, für jede 4 Pixel gerendert wird, indem Sie die die Anwendung).  
  
-   Windows wird standardmäßig auf der rechten Seite, die Skalierung für die Pixeldichte und Anzeigen von Entfernung für die Anzeige (Windows 7 und höher, OEM-konfigurierbar) verwendet werden.  
  
-   Windows kann automatisch Inhalt nach oben um 250 % auf neuen Geräten skalieren, die 280 Ppi (ab Windows 8.1 S14) überschreiten.  
  
 Windows bietet eine Möglichkeit für den Umgang mit der Benutzeroberfläche Skalierung mehr Pixel Anzahl nutzen. Eine Anwendung verwendet dieses System durch Deklarieren selbst "System-DPI-fähige." Anwendungen, die keine vom System zentral hochskaliert werden. Dies kann zu einer "Fuzzyübereinstimmung" benutzerfreundlichkeit führen, in dem die gesamte Anwendung gleichmäßig auf die Pixels gestreckt wird. Zum Beispiel:  
  
 ![DPI-Probleme für Fuzzysuche](../extensibility/media/dpi-issues-fuzzy.png "DPI-Probleme für Fuzzygruppierung")  
  
 Visual Studio, dass der DPI-Skalierung-fähige verwendet und daher nicht "virtualisiert."  
  
 Windows (und Visual Studio) nutzen mehrere UI-Technologien, die unterschiedliche Methoden zum Umgang mit Skalierungsfaktoren, die vom System festgelegt haben. Zum Beispiel:  
  
-   WPF misst die Steuerelemente so geräteunabhängige (Einheiten, nicht in Pixel). WPF-UI skaliert automatisch für den aktuellen DPI-Wert.  
  
-   Alle Textgrößen unabhängig vom Benutzeroberflächen-Framework werden in Punkt ausgedrückt und daher vom System als DPI-unabhängige behandelt werden. Text in WPF, WinForms und Win32-bereits zentral hochskaliert werden ordnungsgemäß beim Zeichnen auf dem Anzeigegerät.  
  
-   Win32/Windows Forms-Dialogfelder und Fenster haben für die Aktivierung von Layouts, das mit dem Text (z. B. über Raster, Flow und Tabelle LayoutPanel-Elemente) ändert. Vermeiden hart kodierte Pixelpositionen, die nicht skaliert werden, wenn die Schriftgrade Ihren Bedürfnissen entsprechend erhöht werden können.  
  
-   Symbole, die vom System bereitgestellten oder Ressourcen anhand von Systemmetriken (z. B. SM_CXICON zugeordnet und SM_CXSMICON zugeordnet) bereits zentral hochskaliert werden.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Ältere Win32 (GDI, GDI +) und Windows Forms-basierte Benutzeroberfläche  
 Obwohl WPF bereits hohe DPI-bewusst ist, wurde ein großer Teil unserer Win32/GDI-basierten Codes nicht ursprünglich mit DPI-Unterstützung, denken Sie daran geschrieben. Windows verfügt über APIs DPI-Skalierung bereitgestellt. Korrekturen für Win32-Probleme sollten konstant innerhalb des Produkts verwenden. Visual Studio stellt eine Hilfsprogramm-Klassenbibliothek, um Funktionen dupliziert und Gewährleistung der Konsistenz in das Produkt zu vermeiden.  
  
## <a name="high-resolution-images"></a>Hochauflösende Bilder  
 In diesem Abschnitt ist in erster Linie für Entwickler, die Erweiterung von Visual Studio 2013. Verwenden Sie für Visual Studio 2015 Image-Dienst, der in Visual Studio integriert ist. Finden Sie auch, dass Sie viele Versionen von Visual Studio-Support /-Ziel und mit aus diesem Grund in 2015 der Bilddienst ist nicht möglich, da sie in früheren Versionen nicht vorhanden ist. In diesem Abschnitt wird auch dann für Sie.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Skalieren Images, die zu klein sind.  
 Bilder, die zu klein sind können zentral hochskaliert und auf GDI und über einige allgemeinen Methoden für WPF gerendert werden. Verwaltete DPI-Hilfsklassen stehen für interne und externe Visual Studio-Integratoren, Skalierung, Symbole, Bitmaps, Imagestrips und Imagelists Adresse zur Verfügung. Win32-basierte systemeigenen C / C++-Hilfsprogramme für die Skalierung HICON, HBITMAP, HIMAGELIST und VsUI::GdiplusImage verfügbar sind. Skalieren einer Bitmap in der Regel erfordert nur eine einzeiligen Änderung nach dem einschließen eines Verweises auf die Hilfe-Bibliothek. Zum Beispiel:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Eine Imagelist skalieren, hängt davon ab, ob die Imagelist zur Ladezeit abgeschlossen ist, oder zur Laufzeit angefügt wird. Wenn beim Laden abgeschlossen ist, rufen Sie `LogicalToDeviceUnits()` würden Sie mit der Imagelist, wie Sie eine Bitmap. Wenn der Code eine einzelne Bitmap zu laden, bevor Sie die Imagelist erstellen muss, stellen Sie sicher, dass die Bildgröße des Imagelist zu skalieren:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 In systemeigenem Code können die Dimensionen skaliert werden, wenn Imagelist wie folgt erstellen:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funktionen in der Bibliothek ermöglichen, die die größenanpassung Algorithmus angibt. Wenn Skalierung Bilder in Imagelists, platziert werden sollten Sie die Hintergrundfarbe festlegen, die für die Transparenz verwendet wird oder NearestNeighbor Skalierung (die Anzeigegeräts 125 % und 150 % auslöst) verwenden.  
  
 Wenden Sie sich an den <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> Dokumentation auf MSDN.  
  
 Die folgende Tabelle zeigt Beispiele wie Bilder mit entsprechenden DPI skaliert werden soll Ihre Skalierungsfaktoren. Die Bilder in Grün kennzeichnen, unsere bewährte ab Visual Studio 2013 (100 – 200 % DPI-Skalierung):  
  
 ![DPI-Probleme, die Skalierung](../extensibility/media/dpi-issues-scaling.png "DPI-Probleme, die Skalierung")  
  
## <a name="layout-issues"></a>Probleme mit dem Layout  
 Häufige Probleme mit dem Layout können in erster Linie durch die Punkte in der Benutzeroberfläche, skaliert und relativ zueinander zu bleiben und nicht mithilfe von absolute Positionen (insbesondere in Pixeleinheiten) vermieden werden. Zum Beispiel:  
  
-   Layout/Textpositionen müssen-Konto für den erweiterten Bildern anpassen.  
  
-   Spalten im Raster müssen Breiten für den erweiterten Text angepasst haben.  
  
-   Hartcodierte Größen oder Leerzeichen zwischen Elementen müssen auch hochskaliert werden. Größen, die nur für Text Dimensionen basieren sind in der Regel in Ordnung, da Schriftarten automatisch hochskaliert werden.  
  
 Hilfsfunktionen finden Sie in der <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> -Klasse ermöglicht die Skalierung auf der X- und Y-Achse:  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (Funktionen ermöglichen die Skalierung auf X / Y-Achse)  
  
-   Int Speicherplatz = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   Int-Height = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 Es gibt Überladungen LogicalToDeviceUnits, um Objekte, z. B. Rect, Punkt und Größe Skalierung zu ermöglichen.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Verwenden der DPIHelper Library/Klasse zum Skalieren von Bildern und layout  
 Die Visual Studio-DPI-Hilfsbibliothek steht in systemeigenen und verwalteten Formulare und außerhalb von Visual Studio Shell von anderen Anwendungen verwendet werden kann.  
  
 Um die Bibliothek zu verwenden, wechseln Sie zu der [Beispiele zur Erweiterbarkeit von Visual Studio-VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) und Klonen der Beispiel-High-DPI_Images_Icons.  
  
 In den Quelldateien enthalten *VsUIDpiHelper.h* , und rufen Sie die statischen Funktionen der `VsUI::DpiHelper` Klasse:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Verwenden Sie nicht die Hilfsfunktionen in auf Modulebene Klassen- oder Instanzebene statischen Variablen. Die Bibliothek verwendet auch statische Variablen für die Threadsynchronisierung, und Sie möglicherweise treten Probleme auf Order-Initialisierung. Konvertieren Sie diese statische Variablen in nicht statischen Membervariablen oder umschlossen in eine Funktion (sodass sie beim ersten Zugriff erstellt abrufen).  
  
 Um die DPI-Hilfsfunktionen in verwaltetem Code zugreifen zu können, die in Visual Studio-Umgebung ausgeführt wird:  
  
-   Das verarbeitende Projekt muss auf die neueste Version der Shell MPF verweisen. Zum Beispiel:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Stellen Sie sicher, das Projekt enthält Verweise auf **"System.Windows.Forms"**, **PresentationCore**, und **PresentationUI**.  
  
-   Verwenden Sie im Code die **Microsoft.VisualStudio.PlatformUI** -Namespace, und rufen eine statische Funktionen DpiHelper-Klasse. Unterstützter Typen (Punkte, Größen, Rechtecke und So weiter) stehen bereitgestellte Erweiterungsfunktionen, die neue zurückgeben Objekte skaliert. Zum Beispiel:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Umgang mit WPF Image Unschärfe zoombare Benutzeroberfläche  
 In WPF werden Bitmaps automatisch skaliert, die von WPF für die aktuelle Zoomstufe für DPI-Werte mithilfe eines Algorithmus für qualitativ hochwertigen Bikubisch (Standard), die eignet sich gut für Bilder oder große Screenshots, jedoch ist für die Symbole im Menü ungeeignet, da dies die wahrgenommene Unschärfe führt .  
  
 Empfehlungen:  
  
-   Für Logo, Bild und Banner Grafik, die Standardeinstellung <xref:System.Windows.Media.BitmapScalingMode> Größenänderung Modus verwendet werden.  
  
-   Für Menüelemente und ikonographie-Images die <xref:System.Windows.Media.BitmapScalingMode> sollte verwendet werden, wenn es nicht zu anderen Artefakten Verzerrung zu darzustellen, Unschärfe (auf 200 % und 300 %) zu beseitigen führt.  
  
-   Für große Zoom nicht ein Vielfaches von 100 % (z. B. 250 % oder % von 350) Zugriffsebenen, führt Skalieren von Bildern von ikonographie mit Bikubisch für Fuzzysuche, verwaschener Benutzeroberfläche. Ein besseres Ergebnis erhalten Sie durch die erste Skalieren des Bilds mit NearestNeighbor zum größten Vielfachen von 100 % (z. B. 200 % oder 300 %) aus, und Skalieren von Daten in eine bikubische von dort aus. Finden Sie unter Sonderfall: WPF-Images für große DPI prescaling Protokollebenen für Weitere Informationen.  
  
 Die DpiHelper-Klasse im Namespace Microsoft.VisualStudio.PlatformUI bietet Mitglied <xref:System.Windows.Media.BitmapScalingMode> , die für die Bindung verwendet werden kann. Sie können die Visual Studio-Shell, die die Skalierung von Bitmaps im Modus für das Produkt gleichmäßig, abhängig von der DPI-Skalierungsfaktor steuern.  
  
 Um es in XAML verwenden, fügen Sie Folgendes hinzu:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Die Visual Studio-Shell wird diese Eigenschaft bereits für Fenster auf oberster Ebene und Dialogfelder. WPF-basierte Benutzeroberfläche ausführen in Visual Studio übernimmt es bereits. Wenn die Einstellung nicht an Ihre bestimmte Teile der Benutzeroberfläche weitergegeben wird, kann es für das Stammelement der XAML/WPF-Benutzeroberfläche festgelegt werden. In dem in diesem Fall, stellen umfassen, Popups für Elemente mit Win32-Eltern, und Designerfenstern, die ausgeführt werden, der zu verarbeiten, z. B. Blend.  
  
 Einige Elemente der Benutzeroberfläche kann unabhängig von der System-Set-DPI Zoomfaktor, z. B. die Visual Studio-Text-Editor und WPF-basierten Designer (WPF-Desktop und Windows Store) skaliert werden. In diesen Fällen sollte DpiHelper.BitmapScalingMode nicht verwendet werden. Zum Beheben dieses Problems im Editor, mit dem Titel der IDE-Teams erstellt eine benutzerdefinierte Eigenschaft RenderOptions.BitmapScalingMode. Dieser Eigenschaftswert HighQuality oder NearestNeighbor die kombinierten Zoomstufe des Systems und die Benutzeroberfläche festgelegt.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Sonderfall: prescaling WPF-Images für große DPI-Ebenen  
 Skalieren von für sehr große Zoomfaktoren, die nicht auf ein Vielfaches von 100 % (z. B. 250 %, 350 % usw.) sind, die ikonographie Bildern mit Bikubisch für Fuzzysuche, verwaschener Benutzeroberfläche führt. Der Eindruck von dieser Images neben schärfer Text ist fast wie eine optische Illusion. Die Bilder, die sich näher über das Auge und unscharf in Bezug auf den Text angezeigt werden. Das Skalieren Ergebnis in dieser vergrößerten Größe kann verbessert werden, vom ersten Skalieren des Bilds mit NearestNeighbor zum größten Vielfachen von 100 % (z. B. 200 % oder 300 %) aus, und Skalieren von Daten in eine bikubische auf den Rest (50 % zusätzlichen).  
  
 Folgendes ist ein Beispiel für die Unterschiede in den Ergebnissen, in dem das erste Bild skaliert wird mit dem verbesserten Skalierung Double-Wert-Algorithmus 100 % ->-200 % > 250 %, und das zweite Argument nur mit Bikubisch 100 %-250 % >.  
  
 ![DPI-Wert gibt doppelte Skalierung Beispiel](../extensibility/media/dpi-issues-double-scaling-example.png "DPI-Wert gibt doppelte Skalierung-Beispiel")  
  
 Damit können die Benutzeroberfläche zum Anzeigen jedes Bildelement diese doppelten Skalierung, die XAML-Markup müssen geändert werden. Die folgenden Beispiele veranschaulichen die Verwendung von Double-Wert-Skalierung in WPF in Visual Studio mithilfe der DpiHelper-Bibliothek und Shell.12/14.  
  
 Schritt 1: Prescale das Bild auf 200 %, 300 % usw. NearestNeighbor verwenden.  
  
 Prescale das Image mithilfe von entweder einen Konverter für eine Bindung oder mit einer XAML-Markuperweiterung angewendet. Zum Beispiel:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Wenn das Bild auch mit Design versehen werden muss (die meisten, wenn nicht sogar alle sollte), das Markup kann einen anderen Konverter, die zuerst Design des Images, und klicken Sie dann vorab Skalierung verwenden. Das Markup verwenden entweder <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> oder <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, je nachdem, auf die gewünschte Konvertierung-Ausgabe.  
  
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
  
 Schritt 2: Stellen Sie sicher, dass die endgültige Größe für den aktuellen DPI-Wert korrekt ist.  
  
 Da WPF die Benutzeroberfläche für den aktuellen DPI-Wert mithilfe der BitmapScalingMode-Eigenschaft, legen Sie für das "UIElement" skaliert wird, sollten ein Image-Steuerelement, das mit einem prescaled Image aus, wie die Quelle zwei- oder dreifache größer als sie aussieht. Im folgenden finden mehrere Möglichkeiten, diesen Effekt Leistungsindikator:  
  
-   Wenn Sie die Dimension des ursprünglichen Bilds bei 100 % kennen, können Sie die genaue Größe des Steuerelements Image angeben. Diese Größen spiegeln, dass die Größe der Benutzeroberfläche vor der Skalierung angewendet wird.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Wenn die Größe des ursprünglichen Bilds nicht bekannt ist, kann ein LayoutTransform zentral herunterskaliert das endgültige Image-Objekt verwendet werden. Zum Beispiel:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>HDPI-Unterstützung für das WebOC aktivieren  
 In der Standardeinstellung aktivieren nicht WebOC-Steuerelemente (z. B. das WebBrowser-Steuerelement in WPF oder das IWebBrowser2-Schnittstelle) HDPI-Erkennung und Unterstützung. Das Ergebnis wird ein eingebettetes Steuerelement mit Anzeigeinhalt sein, die auf eine hochauflösende anzeigen zu klein ist. Im folgenden wird beschrieben, wie hohe DPI-Unterstützung in einer bestimmten Web WebOC-Instanz zu aktivieren.  
  
 Implementieren der Schnittstelle IDocHostUIHandler (finden Sie im MSDN-Artikel der [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) Schnittstelle):  
  
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
  
 Implementieren Sie optional die ICustomDoc-Schnittstelle (finden Sie im MSDN-Artikel der [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) Schnittstelle):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Ordnen Sie IDocHostUIHandler mit das WebOCs Dokuments implementiert die Klasse, ein. Wenn Sie die oben genannten ICustomDoc-Schnittstelle implementiert, klicken Sie dann, sobald das WebOCs Document-Eigenschaft gültig ist, wird Umwandeln Sie es in ein ICustomDoc und rufen Sie der SetUIHandler-Methode und übergeben die Klasse, die IDocHostUIHandler implementiert.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Wenn Sie hat nicht die ICustomDoc-Schnittstelle implementiert, sobald das WebOCs Document-Eigenschaft gültig ist, müssen Sie die Umwandlung in einem IOleObject, und rufen Sie die `SetClientSite` -Methode, Klasse, die implementiert IDocHostUIHandler übergeben. Legen Sie das DOCHOSTUIFLAG_DPI_AWARE-Flag auf die DOCHOSTUIINFO, die an die `GetHostInfo` Methodenaufruf:  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Dies sollten alle sein, die Sie zum Abrufen Ihrer WebOC HPDI unterstützen müssen.  
  
## <a name="tips"></a>Tipps  
  
1.  Wenn die Document-Eigenschaft für das WebOC Steuerelement geändert wird, müssen Sie das Dokument mit der Klasse IDocHostUIHandler neu zuordnen.  
  
2.  Wenn die oben genannten nicht funktioniert, besteht ein bekanntes Problem mit der WebOC nicht auswählen, um die Änderung an der DPI-Flag. Die verlässlichste Möglichkeit zur Lösung dieses Problems wird zum Umschalten der optischen Zooms von das WebOC, Bedeutung zwei Aufrufe mit zwei unterschiedlichen Werten für den Zoomprozentwert. Darüber hinaus ist diese problemumgehung erforderlich, kann es erforderlich, um es auszuführen, bei jedem Aufruf Navigieren zu sein.  
  
    ```csharp  
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