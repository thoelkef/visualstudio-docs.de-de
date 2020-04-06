---
title: Beheben von DPI-Problemen2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740105"
---
# <a name="address-dpi-issues"></a>Beheben von DPI-Problemen
Immer mehr Geräte werden mit "hochauflösenden" Bildschirmen ausgeliefert. Diese Bildschirme haben in der Regel mehr als 200 Pixel pro Zoll (ppi). Für die Arbeit mit einer Anwendung auf diesen Computern müssen Inhalte skaliert werden, um die Anforderungen der Anzeige des Inhalts in einem normalen Anzeigeabstand für das Gerät zu erfüllen. Ab 2014 sind mobile Computergeräte (Tablets, Clamshell-Laptops und Telefone) das primäre Ziel für Displays mit hoher Dichte.

Windows 8.1 und höher enthält mehrere Funktionen, mit denen diese Computer gleichzeitig mit Displays und Umgebungen arbeiten können, in denen die Maschine gleichzeitig an Displays mit hoher Dichte und Standarddichte angeschlossen ist.

- Windows ermöglicht es Ihnen, Inhalte auf das Gerät zu skalieren, indem Sie die Einstellung "Text und andere Elemente größer oder kleiner machen" (seit Windows XP verfügbar) auf das Gerät skalieren.

- Windows 8.1 und höher skaliert den Inhalt automatisch für die meisten Anwendungen, um konsistent zu sein, wenn sie zwischen Displays unterschiedlicher Pixeldichten verschoben werden. Wenn die primäre Anzeige eine hohe Dichte (200 % Skalierung) und die sekundäre Anzeige eine Standarddichte (100%) aufweist, skaliert Windows den Inhalt des Anwendungsfensters automatisch auf der sekundären Anzeige nach unten (1 Pixel wird für alle 4 Pixel angezeigt, die von der Anwendung gerendert werden).

- Windows wird standardmäßig für die Pixeldichte und den Anzeigeabstand für die Anzeige auf die richtige Skalierung eingestellt (Windows 7 und höher, OEM-konfigurierbar).

- Windows kann Inhalte auf neuen Geräten, die 280 ppi überschreiten (ab Windows 8.1 S14), automatisch um bis zu 250 % skalieren.

  Windows kann mit der Skalierung der Benutzeroberfläche umgehen, um die Vorteile der erhöhten Pixelanzahl zu nutzen. Eine Anwendung entscheidet sich für dieses System, indem sie sich selbst als "System-DPI-bewusst" deklariert. Anwendungen, die dies nicht tun, werden vom System skaliert. Dies kann zu einer "fuzzy" Benutzererfahrung führen, bei der die gesamte Anwendung gleichmäßig pixelgestreckt ist. Beispiel:

  ![DPI-Probleme unscharf](../extensibility/media/dpi-issues-fuzzy.png "DPI-Probleme unscharf")

  Visual Studio entscheidet sich für die DPI-Skalierung und ist daher nicht "virtualisiert".

  Windows (und Visual Studio) nutzen mehrere UI-Technologien, die unterschiedliche Möglichkeiten haben, mit vom System festgelegten Skalierungsfaktoren umzugehen. Beispiel:

- WPF misst Steuerelemente geräteunabhängig (Einheiten, nicht Pixel). Die WPF-Benutzeroberfläche wird automatisch für den aktuellen DPI skaliert.

- Alle Textgrößen unabhängig vom UI-Framework werden in Punkten ausgedrückt und daher vom System als DPI-unabhängig behandelt. Text in Win32, WinForms und WPF wird bereits korrekt skaliert, wenn er auf das Anzeigegerät gezeichnet wird.

- Win32/WinForms-Dialoge und -Fenster verfügen über Mittel zum Aktivieren des Layouts, das die Größe mit Text ändert (z. B. durch Raster-, Fluss- und Tabellenlayoutbereiche). Dadurch werden hartcodierte Pixelpositionen vermieden, die nicht skaliert werden, wenn die Schriftgrößen erhöht werden.

- Symbole, die vom System bereitgestellt werden, oder Ressourcen, die auf Systemmetriken basieren (z. B. SM_CXICON und SM_CXSMICON), sind bereits skaliert.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Ältere Win32 (GDI, GDI+) und WinForms-basierte Benutzeroberfläche
Obwohl WPF bereits hoch DPI-bewusst ist, wurde ein Großteil unseres Win32/GDI-basierten Codes ursprünglich nicht mit DPI-Bewusstsein geschrieben. Windows hat DPI-Skalierungs-APIs bereitgestellt. Korrekturen von Win32-Problemen sollten diese konsistent im gesamten Produkt verwenden. Visual Studio hat eine Hilfsklassenbibliothek bereitgestellt, um Das Duplizieren von Funktionen zu vermeiden und die Konsistenz im gesamten Produkt sicherzustellen.

## <a name="high-resolution-images"></a>Hochauflösende Bilder
Dieser Abschnitt richtet sich in erster Linie an Entwickler, die Visual Studio 2013 erweitern. Verwenden Sie für Visual Studio 2015 den Image-Service, der in Visual Studio integriert ist. Möglicherweise müssen Sie auch viele Versionen von Visual Studio unterstützen/zielen, und daher ist die Verwendung des Image-Service im Jahr 2015 keine Option, da er in früheren Versionen nicht vorhanden ist. Dieser Abschnitt ist auch für Sie dann.

## <a name="scaling-up-images-that-are-too-small"></a>Hochskalieren von Bildern, die zu klein sind
Bilder, die zu klein sind, können auf GDI und WPF mit einigen gängigen Methoden skaliert und gerendert werden. Verwaltete DPI-Hilfsklassen stehen internen und externen Visual Studio-Integratoren zur Verfügung, um Skalierungssymbole, Bitmaps, Bilderstreifen und Bildlisten zu adressieren. Win32-basierte native C/C++-Helfer stehen für die Skalierung von HICON, HBITMAP, HIMAGELIST und VsUI::GdiplusImage zur Verfügung. Die Skalierung einer Bitmap erfordert in der Regel nur eine einzeilige Änderung, nachdem ein Verweis auf die Hilfsbibliothek eingebracht wurde. Beispiel:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Das Skalieren einer Bildliste hängt davon ab, ob die Bildliste zum Zeitpunkt des Ladens vollständig ist oder zur Laufzeit angehängt wird. Wenn sie zum Zeitpunkt `LogicalToDeviceUnits()` des Ladens abgeschlossen ist, rufen Sie die Bildliste wie eine Bitmap auf. Wenn der Code eine einzelne Bitmap laden muss, bevor die Bildliste erstellt wird, stellen Sie sicher, dass die Bildgröße der Bildliste skaliert wird:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Im systemeigenen Code können die Bemaßungen beim Erstellen der Bildliste wie folgt skaliert werden:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Funktionen in der Bibliothek ermöglichen die Angabe des Größenänderungsalgorithmus. Wenn Sie Bilder in Bildlisten skalieren, stellen Sie sicher, dass Sie die Hintergrundfarbe angeben, die für die Transparenz verwendet wird, oder verwenden Sie die NearestNeighbor-Skalierung (was zu Verzerrungen bei 125 % und 150 %) führt.

Lesen <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> Sie die Dokumentation zu MSDN.

Die folgende Tabelle zeigt Beispiele, wie Bilder unter entsprechenden DPI-Skalierungsfaktoren skaliert werden sollten. Die in Orange umrissenen Bilder bezeichnen unsere best practice ab Visual Studio 2013 (100%-200% DPI-Skalierung):

![DPI-Probleme beim Skalieren](../extensibility/media/dpi-issues-scaling.png "DPI-Probleme beim Skalieren")

## <a name="layout-issues"></a>Layoutprobleme
Häufige Layoutprobleme können in erster Linie vermieden werden, indem Punkte in der Benutzeroberfläche skaliert und relativ zueinander gehalten werden, anstatt absolute Positionen (insbesondere in Pixeleinheiten) zu verwenden. Beispiel:

- Layout-/Textpositionen müssen angepasst werden, um skalierte Bilder zu berücksichtigen.

- Spalten in Rastern müssen Breiten für den skalierten Text angepasst haben.

- Hartcodierte Größen oder Leerzeichen zwischen Elementen müssen ebenfalls skaliert werden. Größen, die nur auf Textdimensionen basieren, sind in der Regel in Ordnung, da Schriftarten automatisch skaliert werden.

  Hilfsfunktionen sind in <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> der Klasse verfügbar, um die Skalierung auf der X- und Y-Achse zu ermöglichen:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (Funktionen ermöglichen die Skalierung auf der X/Y-Achse)

- int space = DpiHelper.LogicalToDeviceUnitsX (10);

- int height = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Es gibt Überladungen von LogicalToDeviceUnits, um Skalierungsobjekte wie Rect, Point und Size zu ermöglichen.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Verwenden der DPIHelper-Bibliothek/-Klasse zum Skalieren von Bildern und Layouts
Die Visual Studio-DPI-Hilfsbibliothek ist in systemeigenen und verwalteten Formularen verfügbar und kann außerhalb der Visual Studio-Shell von anderen Anwendungen verwendet werden.

Um die Bibliothek zu verwenden, wechseln Sie zu den [Visual Studio VSSDK-Erweiterbarkeitsbeispielen,](https://github.com/Microsoft/VSSDK-Extensibility-Samples) und klonen Sie das DPI_Images_Icons-Beispiel.

Schließen Sie in Quelldateien *VsUIDpiHelper.h* ein `VsUI::DpiHelper` und rufen Sie die statischen Funktionen der Klasse auf:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Verwenden Sie die Hilfsfunktionen nicht in statischen Variablen auf Modul- oder Klassenebene. Die Bibliothek verwendet auch Statik für die Threadsynchronisierung, und Es kann zu Problemen bei der Reihenfolge-Initialisierung kommen. Konvertieren Sie diese Statik entweder in nicht statische Membervariablen, oder umschließen Sie sie in eine Funktion (damit sie beim ersten Zugriff erstellt werden).

So greifen Sie über verwalteten Code auf die DPI-Hilfsfunktionen zu, der in der Visual Studio-Umgebung ausgeführt wird:

- Das verbrauchende Projekt muss auf die neueste Version von Shell MPF verweisen. Beispiel:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Stellen Sie sicher, dass das Projekt Verweise auf **System.Windows.Forms**, **PresentationCore**und **PresentationUI**enthält.

- Verwenden Sie im Code den **Microsoft.VisualStudio.PlatformUI-Namespace,** und rufen Sie statische Funktionen der DpiHelper-Klasse auf. Für unterstützte Typen (Punkte, Größen, Rechtecke usw.) stehen Erweiterungsfunktionen zur Verfügung, die neue skalierte Objekte zurückgeben. Beispiel:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Umgang mit WPF-Bildunuzziness in zoombarer Benutzeroberfläche
In WPF werden Bitmaps automatisch von WPF für die aktuelle DPI-Zoomstufe mithilfe eines hochwertigen bikubischen Algorithmus (Standard) angepasst, der gut für Bilder oder große Screenshots funktioniert, aber für Menüelementsymbole ungeeignet ist, da es wahrgenommene Unschärfe einführt.

Empfehlungen:

- Für Logo-Bild und Banner-Artworks kann der Standard-Größenänderungsmodus <xref:System.Windows.Media.BitmapScalingMode> verwendet werden.

- Für Menüpunkte und Ikonographiebilder sollte die <xref:System.Windows.Media.BitmapScalingMode> verwendet werden, wenn es nicht dazu führt, dass andere Verzerrungsartefakte Unschärfe beseitigen (bei 200% und 300%).

- Bei großen Zoomstufen, die nicht ein Vielfaches von 100 % betragen (z. B. 250 % oder 350 %), führt die Skalierung von Ikonographiebildern mit bikubischen Ergebnissen zu einer unscharfen, ausgewaschenen Benutzeroberfläche. Ein besseres Ergebnis wird erzielt, indem zuerst das Bild mit NearestNeighbor auf das größte Vielfache von 100% skaliert wird (z. B. 200% oder 300%) und Skalierung mit bikubischen von dort. Weitere Informationen finden Sie unter Sonderfall: Vorskalierung von WPF-Bildern für große DPI-Ebenen.

  Die DpiHelper-Klasse im Microsoft.VisualStudio.PlatformUI-Namespace stellt einen Member <xref:System.Windows.Media.BitmapScalingMode> bereit, der für die Bindung verwendet werden kann. Die Visual Studio-Shell kann den Bitmapskalierungsmodus im gesamten Produkt je nach DPI-Skalierungsfaktor einheitlich steuern.

  Um es in XAML zu verwenden, fügen Sie hinzu:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Die Visual Studio-Shell legt diese Eigenschaft bereits in Fenstern und Dialogfeldern der obersten Ebene fest. Die in Visual Studio ausgeführte WPF-basierte Benutzeroberfläche erbt sie bereits. Wenn die Einstellung nicht an bestimmte Teile der Benutzeroberfläche weitergegeben wird, kann sie für das Stammelement der XAML/WPF-Benutzeroberfläche festgelegt werden. Zu den Orten, an denen dies geschieht, gehören Pop-ups, Elemente mit Win32-Eltern und Designerfenster, die nicht mehr verarbeitet werden, z. B. Blend.

Einige Benutzeroberfläche können unabhängig von der vom System festgelegten DPI-Zoomstufen skaliert werden, z. B. der Visual Studio-Texteditor und WPF-basierte Designer (WPF Desktop und Windows Store). In diesen Fällen sollte DpiHelper.BitmapScalingMode nicht verwendet werden. Um dieses Problem im Editor zu beheben, hat das IDE-Team eine benutzerdefinierte Eigenschaft mit dem Titel RenderOptions.BitmapScalingMode erstellt. Legen Sie diesen Eigenschaftswert abhängig von der kombinierten Zoomstufe des Systems und der Benutzeroberfläche auf HighQuality oder NearestNeighbor fest.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Sonderfall: Vorskalierung von WPF-Bildern für große DPI-Level
Bei sehr großen Zoomstufen, die nicht ein Vielfaches von 100 % betragen (z. B. 250 %, 350 % usw.), führt die Skalierung von Ikonographiebildern mit bikubischen Ergebnissen zu einer unscharfen, ausgewaschenen Benutzeroberfläche. Der Eindruck dieser Bilder neben gestochen scharfem Text ist fast wie der einer optischen Täuschung. Die Bilder scheinen näher am Auge und azentriver in Bezug auf den Text zu sein. Das Skalierungsergebnis bei dieser vergrößerten Größe kann verbessert werden, indem zuerst das Bild mit NearestNeighbor auf das größte Vielfache von 100 % skaliert wird (z. B. 200 % oder 300 %) und Skalierung mit Bikubik auf den Rest (weitere 50%).

Im Folgenden finden Sie ein Beispiel für die Unterschiede in den Ergebnissen, bei denen das erste Bild mit dem verbesserten Doppelskalierungsalgorithmus 100%->200%->250% skaliert wird, und das zweite nur mit bikubischen 100%->250%.

![DPI-Probleme Double Scaling Beispiel](../extensibility/media/dpi-issues-double-scaling-example.png "DPI-Probleme Double Scaling Beispiel")

Damit die Benutzeroberfläche diese Doppelteskalierung verwenden kann, muss das XAML-Markup zum Anzeigen jedes Image-Elements geändert werden. In den folgenden Beispielen wird veranschaulicht, wie Sie die Doppelteskalierung in WPF in Visual Studio mithilfe der DpiHelper-Bibliothek und Shell.12/14 verwenden.

Schritt 1: Skalieren Sie das Bild mit NearestNeighbor auf 200 %, 300 % usw.

Skalieren Sie das Bild entweder mit einem Konverter, der auf eine Bindung angewendet wird, oder mit einer XAML-Markuperweiterung. Beispiel:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Wenn das Bild auch thematisiert werden muss (die meisten, wenn nicht alle sollten), kann das Markup einen anderen Konverter verwenden, der zuerst das Bild thematisiert und dann vorskaliert. Das Markup kann <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>je nach gewünschter Konvertierungsausgabe entweder oder verwenden.

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

Schritt 2: Stellen Sie sicher, dass die endgültige Größe für den aktuellen DPI korrekt ist.

Da WPF die Benutzeroberfläche für den aktuellen DPI mithilfe der BitmapScalingMode-Eigenschaft, die auf dem UIElement festgelegt ist, skaliert, sieht ein Image-Steuerelement, das ein vorskaliertes Bild als Quelle verwendet, zwei- bis dreimal größer aus, als es sollte. Im Folgenden finden Sie mehrere Möglichkeiten, diesem Effekt entgegenzuwirken:

- Wenn Sie die Bemaßung des Originalbildes zu 100 % kennen, können Sie die genaue Größe des Bildsteuerelements angeben. Diese Größen spiegeln die Größe der Benutzeroberfläche wider, bevor die Skalierung angewendet wird.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Wenn die Größe des Originalbildes nicht bekannt ist, kann eine LayoutTransform verwendet werden, um das endgültige Image-Objekt herunterzuskalieren. Beispiel:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>Aktivieren der HDPI-Unterstützung für das WebOC
Standardmäßig aktivieren WebOC-Steuerelemente (z. B. das WebBrowser-Steuerelement in WPF oder die IWebBrowser2-Schnittstelle) die HDPI-Erkennung und -Unterstützung nicht. Das Ergebnis ist ein eingebettetes Steuerelement mit Anzeigeinhalten, das auf einem hochauflösenden Display zu klein ist. Im Folgenden wird beschrieben, wie Sie High-DPI-Unterstützung in einer bestimmten WebOC-Instanz aktivieren.

Implementieren Sie die IDocHostUIHandler-Schnittstelle (siehe MSDN-Artikel auf dem [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

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

Implementieren Sie optional die ICustomDoc-Schnittstelle (siehe MSDN-Artikel auf dem [ICustomDoc:](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

Ordnen Sie die Klasse, die IDocHostUIHandler implementiert, dem WebOC-Dokument zu. Wenn Sie die iCustomDoc-Schnittstelle oben implementiert haben, um die Document-Eigenschaft des WebOC zu validieren, geben Sie sie in ein ICustomDoc um und rufen Sie die SetUIHandler-Methode auf, indem Sie die Klasse übergeben, die IDocHostUIHandler implementiert.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

Wenn Sie die ICustomDoc-Schnittstelle NICHT implementiert haben, müssen Sie, sobald die Document-Eigenschaft des WebOC gültig ist, `SetClientSite` sie in ein IOleObject umlegen und die Methode aufrufen und die Klasse übergeben, die IDocHostUIHandler implementiert. Legen Sie das DOCHOSTUIFLAG_DPI_AWARE-Flag für DIE `GetHostInfo` ABEROSTUIINFO fest, die an den Methodenaufruf übergeben wird:

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

Dies sollte alles sein, was Sie benötigen, um Ihr WebOC-Steuerelement zur Unterstützung von HPDI zu erhalten.

## <a name="tips"></a>Tipps

1. Wenn sich die dokumenteigenschaft im WebOC-Steuerelement ändert, müssen Sie das Dokument möglicherweise erneut der IDocHostUIHandler-Klasse zuordnen.

2. Wenn die oben genannten Nichtfunktioniertwerden, liegt ein bekanntes Problem vor, dass das WebOC die Änderung am DPI-Flag nicht aufnimmt. Die zuverlässigste Möglichkeit, dies zu beheben, besteht darin, den optischen Zoom des WebOC umzuschalten, d. h. zwei Aufrufe mit zwei unterschiedlichen Werten für den Zoomprozentsatz. Wenn diese Problemumgehung erforderlich ist, kann es erforderlich sein, sie bei jedem Navigationsaufruf auszuführen.

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
