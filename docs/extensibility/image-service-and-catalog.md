---
title: Image Service und Katalog | Microsoft Docs
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710390"
---
# <a name="image-service-and-catalog"></a>Image-Service und Katalog
Dieses Rezeptbuch enthält Anleitungen und bewährte Methoden für die Einführung des Visual Studio Image Service und image Catalog, die in Visual Studio 2015 vorgestellt wurden.

 Mit dem in Visual Studio 2015 eingeführten Image-Service können Entwickler die besten Bilder für das Gerät und das vom Benutzer gewählte Design erhalten, um das Bild anzuzeigen, einschließlich der korrekten Themenbildung für den Kontext, in dem sie angezeigt werden. Die Annahme des Image-Service wird dazu beitragen, wichtige Probleme im Zusammenhang mit der Wartung von Ressourcen, der HDPI-Skalierung und der Themenzuspielung zu beseitigen.

|||
|-|-|
|**Probleme heute**|**Lösungen**|
|Hintergrundfarbverschmelzung|Integrierte Alpha-Mischung|
|Theming (einige) Bilder|Themenmetadaten|
|Hochkontrastmodus|Alternative Ressourcen mit hohem Kontrast|
|Benötigen Sie mehrere Ressourcen für verschiedene DPI-Modi|Wählbare Ressourcen mit vektorbasiertem Fallback|
|Duplikatbilder|Ein Bezeichner pro Bildkonzept|

 Warum den Image-Service übernehmen?

- Erhalten Sie immer das neueste "pixel-perfekte" Bild von Visual Studio

- Sie können Ihre eigenen Bilder einreichen und verwenden

- Keine Notwendigkeit, Ihre Bilder zu testen, wenn Windows neue DPI-Skalierung hinzufügt

- Beheben Sie alte architektonische Hürden in Ihren Implementierungen

  Die Visual Studio-Shellsymbolleiste vor und nach der Verwendung des Image-Service:

  ![Bilddienst vorher und nachher](../extensibility/media/image-service-before-and-after.png "Bilddienst vorher und nachher")

## <a name="how-it-works"></a>Funktionsweise
 Der Image-Service kann ein Bitmap-Image bereitstellen, das für jedes unterstützte UI-Framework geeignet ist:

- WPF: BitmapSource

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Bilddienstflussdiagramm

  ![Bilddienst-Flussdiagramm](../extensibility/media/image-service-flow-diagram.png "Bilddienst-Flussdiagramm")

  **Bildmoniker**

  Ein Bildmoniker (oder kurz Moniker) ist ein GUID/ID-Paar, das ein Bild- oder Bildlistenobjekt in der Bildbibliothek eindeutig identifiziert.

  **Bekannte Moniker**

  Der Satz von Bildmonikern, die im Visual Studio-Bildkatalog enthalten sind und von jeder Visual Studio-Komponente oder -Erweiterung öffentlich ausvergoniert werden können.

  **Bildmanifestdateien**

  Bildmanifestdateien (*.imagemanifest*) sind XML-Dateien, die eine Reihe von Bildassets definieren, die Moniker, die diese Assets darstellen, und das reale Bild oder die Bilder, die jedes Asset darstellen. Bildmanifeste können eigenständige Bilder oder Bildlisten für die Unterstützung der älteren Benutzeroberfläche definieren. Darüber hinaus gibt es Attribute, die entweder für die Anlage oder für die einzelnen Bilder hinter jedem Asset festgelegt werden können, um zu ändern, wann und wie diese Assets angezeigt werden.

  **Bildmanifestschema**

  Ein vollständiges Bildmanifest sieht wie folgt aus:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Symbols**

 Als Lesbarkeits- und Wartungshilfe kann das Bildmanifest Symbole für Attributwerte verwenden. Symbole sind wie folgt definiert:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Unterelement**|**Definition**|
|Importieren|Importiert die Symbole der angegebenen Manifestdatei zur Verwendung im aktuellen Manifest|
|Guid|Das Symbol stellt eine GUID dar und muss mit der GUID-Formatierung übereinstimmen.|
|id|Das Symbol stellt eine ID dar und muss eine nicht negative Ganze reine Zahl sein.|
|String|Das Symbol stellt einen beliebigen Zeichenfolgenwert dar.|

 Bei Symbolen wird die Groß-/Kleinschreibung beachtet und mit der Syntax von '(symbolname) verwiesen:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Einige Symbole sind für alle Manifeste vordefiniert. Diese können im Uri-Attribut \<der Source-> oder \<>-Element importieren verwendet werden, um Pfade auf dem lokalen Computer zu referenzieren.

|||
|-|-|
|**Symbol**|**Beschreibung**|
|CommonProgramFiles|Der Wert der Umgebungsvariablen %CommonProgramFiles%|
|LocalAppData|Der Wert der Umgebungsvariablen %LocalAppData%|
|ManifestFolder|Der Ordner, der die Manifestdatei enthält|
|Mydocuments|Der vollständige Pfad des Ordners Eigene Dateien des aktuellen Benutzers|
|ProgramFiles|Der Wert der Umgebungsvariablen %ProgramFiles%|
|System|Der Ordner *Windows-System32*|
|WinDir|Der Wert der Umgebungsvariablen %WinDir%|

 **Image**

 Das \<Bild->-Element definiert ein Bild, auf das ein Moniker verweisen kann. Die GUID und die ID, die zusammen genommen werden, bilden den Bildmoniker. Der Moniker für das Bild muss in der gesamten Bildbibliothek eindeutig sein. Wenn mehr als ein Bild einen bestimmten Moniker hat, wird das erste Bild beim Erstellen der Bibliothek beibehalten.

 Sie muss mindestens eine Quelle enthalten. Größenneutrale Quellen liefern die besten Ergebnisse in einer breiten Palette von Größen, aber sie sind nicht erforderlich. Wenn der Dienst nach einem Abbild einer \<Größe gefragt wird, die nicht im Image->-Element definiert ist, und es keine größenneutrale Quelle gibt, wählt der Dienst die beste größenspezifische Quelle aus und skaliert sie auf die angeforderte Größe.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**attribute**|**Definition**|
|Guid|[Erforderlich] Der GUID-Teil des Bildmonikers|
|id|[Erforderlich] Der ID-Teil des Bildmonikers|
|AllowColorInversion|[Optional, Standard true] Gibt an, ob das Bild seine Farben programmgesteuert invertiert haben kann, wenn es auf einem dunklen Hintergrund verwendet wird.|

 **Quelle**

 Das \<Source>-Element definiert ein einzelnes Bildquellen-Asset (XAML und PNG).

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**attribute**|**Definition**|
|Uri|[Erforderlich] Ein URI, der definiert, aus wo das Bild geladen werden kann. Folgende Werte sind möglich:<br /><br /> - Ein [Pack-URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) mit der application:///-Berechtigung<br />- Eine absolute Komponentenressourcenreferenz<br />- Ein Pfad zu einer Datei, die eine systemeigene Ressource enthält|
|Hintergrund|[Optional] Gibt an, welche Quelle auf der Art des Hintergrunds verwendet werden soll.<br /><br /> Folgende Werte sind möglich:<br /><br /> *Licht:* Die Quelle kann auf einem hellen Hintergrund verwendet werden.<br /><br /> *Dunkel:* Die Quelle kann auf einem dunklen Hintergrund verwendet werden.<br /><br /> *HighContrast:* Die Quelle kann auf jedem Hintergrund im Modus "Hoher Kontrast" verwendet werden.<br /><br /> *HighContrastLight:* Die Quelle kann auf einem hellen Hintergrund im Modus "Hoher Kontrast" verwendet werden.<br /><br /> *HighContrastDark:* Die Quelle kann auf einem dunklen Hintergrund im Modus "Hoher Kontrast" verwendet werden.<br /><br /> Wenn das Background-Attribut weggelassen wird, kann die Quelle auf jedem Hintergrund verwendet werden.<br /><br /> Wenn Hintergrund *Light*, *Dark*, *HighContrastLight*oder *HighContrastDark*ist, werden die Farben der Quelle nie invertiert. Wenn Background weggelassen oder auf *HighContrast*festgelegt ist, wird die Umkehrung der Farben der Quelle durch das **AllowColorInversion-Attribut** des Bildes gesteuert.|

Ein \<Source>-Element kann genau eines der folgenden optionalen Unterelemente enthalten:

||||
|-|-|-|
|**Element**|**Attribute (alle erforderlich)**|**Definition**|
|\<Größe>|Wert|Die Quelle wird für Bilder der angegebenen Größe (in Geräteeinheiten) verwendet. Das Bild wird quadratisch sein.|
|\<SizeRange>|MinSize, MaxSize|Die Quelle wird für Bilder von MinSize bis MaxSize (in Geräteeinheiten) einschließlich verwendet. Das Bild wird quadratisch sein.|
|\<Abmessungen>|Width, Height|Die Quelle wird für Bilder der angegebenen Breite und Höhe (in Geräteeinheiten) verwendet.|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Die Quelle wird für Bilder von der minimalen Breite/Höhe bis zur maximalen Breite/Höhe (in Geräteeinheiten) einschließlich verwendet.|

 Ein \<Source>-Element kann \<auch über ein optionales \<>-Unterelement nativeResource verfügen, das eine> definiert, die aus einer systemeigenen Assembly und nicht aus einer verwalteten Assembly geladen wird.

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**attribute**|**Definition**|
|type|[Erforderlich] Der Typ der systemeigenen Ressource, entweder XAML oder PNG|
|id|[Erforderlich] Der Ganzzahl-ID-Teil der systemeigenen Ressource|

 **Imagelist**

 Das \<ImageList>-Element definiert eine Sammlung von Bildern, die in einem einzelnen Streifen zurückgegeben werden können. Der Streifen wird nach Bedarf nach Bedarf gebaut.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**attribute**|**Definition**|
|Guid|[Erforderlich] Der GUID-Teil des Bildmonikers|
|id|[Erforderlich] Der ID-Teil des Bildmonikers|
|Extern|[Optional, Standard false] Gibt an, ob der Bildmoniker auf ein Bild im aktuellen Manifest verweist.|

 Der Moniker für das enthaltene Bild muss nicht auf ein Bild verweisen, das im aktuellen Manifest definiert ist. Wenn das enthaltene Bild nicht in der Bildbibliothek gefunden werden kann, wird an seiner Stelle ein leeres Platzhalterbild verwendet.

## <a name="using-the-image-service"></a>Verwenden des Image-Service

### <a name="first-steps-managed"></a>Erste Schritte (verwaltet)
 Um den Image-Service zu verwenden, müssen Sie dem Projekt Verweise auf einige oder alle der folgenden Assemblys hinzufügen:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Erforderlich, wenn Sie den integrierten Imagekatalog **KnownMonikers**verwenden.

- *Microsoft.VisualStudio.Imaging.dll*

  - Erforderlich, wenn Sie **CrispImage** und **ImageThemingUtilities** in Ihrer WPF-Benutzeroberfläche verwenden.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - Erforderlich, wenn Sie die Typen **ImageMoniker** und **ImageAttributes** verwenden.

  - **EmbedInteropTypes** sollte auf true gesetzt werden.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - Erforderlich, wenn Sie den Typ **IVsImageService2** verwenden.

  - **EmbedInteropTypes** sollte auf true gesetzt werden.

- *Microsoft.VisualStudio.Utilities.dll*

  - Erforderlich, wenn Sie den **BrushToColorConverter** für **ImageThemingUtilities.ImageBackgroundColor** in Ihrer WPF-Benutzeroberfläche verwenden.

- *Microsoft.VisualStudio.Shell. \<VSVersion>.0*

  - Erforderlich, wenn Sie den **IVsUIObject-Typ** verwenden.

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - Erforderlich, wenn Sie die WinForms-bezogenen UI-Hilfsprogramme verwenden.

  - **EmbedInteropTypes** sollte auf true gesetzt werden

### <a name="first-steps-native"></a>Erste Schritte (nativ)
 Um den Image-Service verwenden zu können, müssen Sie einige oder alle der folgenden Header in Ihr Projekt einschließen:

- **KnownImageIds.h**

  - Erforderlich, wenn Sie den integrierten Imagekatalog **KnownMonikers**verwenden, aber nicht den **ImageMoniker-Typ** verwenden können, z. B. beim Zurückgeben von Werten aus **IVsHierarchy GetGuidProperty-** oder **GetProperty-Aufrufen.**

- **KnownMonikers.h**

  - Erforderlich, wenn Sie den integrierten Imagekatalog **KnownMonikers**verwenden.

- **ImageParameters140.h**

  - Erforderlich, wenn Sie die Typen **ImageMoniker** und **ImageAttributes** verwenden.

- **VSShell140.h**

  - Erforderlich, wenn Sie den Typ **IVsImageService2** verwenden.

- **ImageThemingUtilities.h**

  - Erforderlich, wenn Sie nicht zulassen können, dass der Image-Service die Bearbeitung für Sie verarbeitet.

  - Verwenden Sie diese Kopfzeile nicht, wenn der Image-Service Ihre Bild-Themen verarbeiten kann.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Erforderlich, wenn Sie die DPI-Hilfsprogramme verwenden, um den aktuellen DPI abzubekommen.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Erforderlich, wenn Sie die DPI-Awareness-Hilfsprogramme verwenden, um den aktuellen DPI abzubekommen.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Wie schreibe ich eine neue WPF-Benutzeroberfläche?

1. Fügen Sie zunächst die Assemblyverweise hinzu, die im obigen Abschnitt der ersten Schritte erforderlich sind, zu Ihrem Projekt. Sie müssen nicht alle hinzufügen, also fügen Sie nur die Referenzen hinzu, die Sie benötigen. (Hinweis: Wenn Sie **Farben** anstelle von **Pinsel**verwenden oder darauf zugreifen, können Sie den Verweis auf **Dienstprogramme**überspringen, da Sie den Konverter nicht benötigen.)

2. Wählen Sie das gewünschte Bild aus und erhalten Sie dessen Moniker. Verwenden Sie einen **KnownMoniker**, oder verwenden Sie Eigene, wenn Sie Ihre eigenen benutzerdefinierten Bilder und Moniker haben.

3. Fügen Sie **CrispImages** zu Ihrem XAML hinzu. (Siehe unten Beispiel.)

4. Legen Sie die **ImageThemingUtilities.ImageBackgroundColor-Eigenschaft** in der UI-Hierarchie fest. (Dies sollte an der Stelle festgelegt werden, an der die Hintergrundfarbe bekannt ist, nicht unbedingt auf dem **CrispImage**.) (Siehe unten Beispiel.)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **Wie aktualisiere ich die vorhandene WPF-Benutzeroberfläche?**

 Das Aktualisieren vorhandener WPF-Benutzeroberfläche ist ein relativ einfacher Prozess, der aus drei grundlegenden Schritten besteht:

1. Ersetzen \<Sie alle Image> \<Elemente in Ihrer Benutzeroberfläche durch CrispImage> Elemente.

2. Ändern Sie alle Quellattribute in Moniker-Attribute.

    - Wenn sich das Bild nie ändert und Sie **KnownMonikers**verwenden, binden Sie diese Eigenschaft statisch an den **KnownMoniker**. (Siehe das obige Beispiel.)

    - Wenn sich das Bild nie ändert und Sie Ihr eigenes benutzerdefiniertes Bild verwenden, binden Sie es statisch an Ihren eigenen Moniker.

    - Wenn sich das Bild ändern kann, binden Sie das Moniker-Attribut an eine Codeeigenschaft, die über Eigenschaftenänderungen benachrichtigt.

3. Legen Sie irgendwo in der UI-Hierarchie **ImageThemingUtilities.ImageBackgroundColor** fest, um sicherzustellen, dass die Farbinversion ordnungsgemäß funktioniert.

    - Dies kann die Verwendung der **BrushToColorConverter-Klasse** erfordern. (Siehe das obige Beispiel.)

## <a name="how-do-i-update-win32-ui"></a>Wie aktualisiere ich die Win32-Benutzeroberfläche?
 Fügen Sie dem Code ggf. Folgendes hinzu, um das unformatierte Laden von Bildern zu ersetzen. Wechseln Sie die Werte für die Rückgabe von HBITMAPs im Vergleich zu HICONs und HIMAGELIST bei Bedarf.

 **Abrufen des Image-Service**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Anfordern des Bildes**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Wie aktualisiere ich die WinForms-Benutzeroberfläche?
 Fügen Sie dem Code ggf. Folgendes hinzu, um das unformatierte Laden von Bildern zu ersetzen. Wechseln Sie die Werte für die Rückgabe von Bitmaps und Symbolen nach Bedarf.

 **Hilfreich mit Anweisung**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Abrufen des Image-Service**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Anfordern des Bildes**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Wie verwende ich Bildmoniker in einem neuen Toolfenster?
 Die VSIX-Paketprojektvorlage wurde für Visual Studio 2015 aktualisiert. Um ein neues Toolfenster zu erstellen, klicken Sie mit der rechten Maustaste auf das VSIX-Projekt und wählen **Neue** > **Position** hinzufügen (**Strg**+**umschaltung**+**A**). Wählen Sie unter dem Erweiterbarkeitsknoten für die Projektsprache **benutzerdefiniertes Toolfenster**aus, geben Sie dem Toolfenster einen Namen, und drücken Sie die Schaltfläche **Hinzufügen.**

 Dies sind die wichtigsten Orte, um Moniker in einem Toolfenster zu verwenden. Folgen Sie den Anweisungen für jeden:

1. Die Registerkarte "Werkzeugfenster", wenn die Registerkarten klein genug werden (auch im **Fensterschalter Strg-Registerkarte**+**Tab** na.

    Fügen Sie diese Zeile dem Konstruktor für die Klasse hinzu, die vom **ToolWindowPane-Typ** abstammt:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Der Befehl zum Öffnen des Werkzeugfensters.

    Bearbeiten Sie in der *.vsct-Datei* für das Paket die Befehlsschaltfläche des Toolfensters:

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **Wie verwende ich Bildmoniker in einem vorhandenen Toolfenster?**

   Das Aktualisieren eines vorhandenen Toolfensters zur Verwendung von Bildmonikern ähnelt den Schritten zum Erstellen eines neuen Toolfensters.

   Dies sind die wichtigsten Orte, um Moniker in einem Toolfenster zu verwenden. Folgen Sie den Anweisungen für jeden:

3. Die Registerkarte "Werkzeugfenster", wenn die Registerkarten klein genug werden (auch im **Fensterschalter Strg-Registerkarte**+**Tab** na.

   1. Entfernen Sie diese Zeilen (sofern vorhanden) im Konstruktor für die Klasse, die vom **ToolWindowPane-Typ** abstammt:

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. Siehe Schritt #1 des "Wie verwende ich Bildmoniker in einem neuen Toolfenster?" Abschnitt oben.

4. Der Befehl zum Öffnen des Werkzeugfensters.

   - Siehe Schritt #2 des "Wie verwende ich Bildmoniker in einem neuen Toolfenster?" Abschnitt oben.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Wie verwende ich Bildmoniker in einer .vsct-Datei?
 Aktualisieren Sie Ihre *.vsct-Datei,* wie in den folgenden Kommentarzeilen angegeben:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **Was passiert, wenn meine .vsct-Datei auch von älteren Versionen von Visual Studio gelesen werden muss?**

 Ältere Versionen von Visual Studio erkennen das **IconIsMoniker-Befehlsflag** nicht. Sie können Bilder aus dem Image-Service für Versionen von Visual Studio verwenden, die dies unterstützen, aber weiterhin Bilder im alten Stil für ältere Versionen von Visual Studio verwenden. Dazu lassen Sie die *.vsct-Datei* unverändert (und damit mit älteren Versionen von Visual Studio kompatibel) und erstellen eine CSV-Datei (durch Kommas getrennte Werte), die aus GUID/ID-Paaren, die in den \<Bitmaps einer *.vsct-Datei* definiert sind,> Element zu Bildmoniker-GUID/ID-Paaren zuordnet.

 Das Format der Zuordnungs-CSV-Datei ist:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 Die CSV-Datei wird mit dem Paket bereitgestellt, und ihr Speicherort wird von der **IconMappingFilename-Eigenschaft** des **ProvideMenuResource-Paketattributs** angegeben:

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 Der **IconMappingFilename** ist entweder ein relativer Pfad, der implizit bei $PackageFolder - wie im obigen Beispiel) verwurzelt ist, oder ein absoluter Pfad, der explizit in einem Verzeichnis verwurzelt ist, das von einer Umgebungsvariablen definiert ist, wie z. *B. ""%UserProfile%" .dir1,dir2,MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Wie porte ich ein Projektsystem?
 **So liefern Sie ImageMonikers für ein Projekt**

1. Implementieren Sie **VSHPROPID_SupportsIconMonikers** in der **IVs-Hierarchie**des Projekts, und geben Sie true zurück.

2. Implementieren Sie entweder **VSHPROPID_IconMonikerImageList** (wenn das ursprüngliche Projekt **VSHPROPID_IconImgList**verwendet wird) oder **VSHPROPID_IconMonikerGuid** **, VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (wenn das ursprüngliche Projekt **VSHPROPID_IconHandle** und **VSHPROPID_OpenFolderIconHandle**verwendet).

3. Ändern Sie die Implementierung der ursprünglichen VSHPROPIDs für Symbole, um "Legacy"-Versionen der Symbole zu erstellen, wenn Erweiterungspunkte sie anfordern. **IVsImageService2** bietet Funktionen, die zum Abrufen dieser Symbole erforderlich sind.

   **Zusätzliche Anforderungen an VB/C-Projektaromen**

   Implementieren Sie **VSHPROPID_SupportsIconMonikers** nur, wenn Sie feststellen, dass Ihr Projekt der **äußerste Geschmack**ist. Andernfalls kann der tatsächliche äußerste Geschmack Bildmoniker in der Realität nicht unterstützen, und Ihr Basisgeschmack könnte angepasste Bilder effektiv "verstecken".

   **Wie verwende ich Bildmoniker in CPS?**

   Das Festlegen benutzerdefinierter Bilder in CPS (Common Project System) kann manuell oder über eine Elementvorlage erfolgen, die dem Project System Extensibility SDK beiliegt.

   **Verwenden des Project System Extensibility SDK**

   Befolgen Sie die Anweisungen unter [Bereitstellen benutzerdefinierter Symbole für den Projekttyp/Elementtyp,](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) um Ihre CPS-Images anzupassen. Weitere Informationen zu CPS finden Sie in der [Visual Studio Project System-Erweiterbarkeitsdokumentation](https://github.com/Microsoft/VSProjectSystem)

   **Verwenden Sie ImageMonikers manuell**

4. Implementieren und exportieren Sie die **IProjectTreeModifier-Schnittstelle** in Ihrem Projektsystem.

5. Bestimmen Sie, welcher **KnownMoniker-** oder benutzerdefinierte Bildmoniker Verwendet werden soll.

6. Führen Sie in der **ApplyModifications-Methode** die folgenden Punkte an einer Stelle in der Methode aus, bevor Sie die neue Struktur zurückgeben, ähnlich dem folgenden Beispiel:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Wenn Sie eine neue Struktur erstellen, können Sie die benutzerdefinierten Bilder festlegen, indem Sie die gewünschten Moniker an die NewTree-Methode übergeben, ähnlich dem folgenden Beispiel:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Wie kontifziere ich von einem echten Bildstreifen in einen monikerbasierten Bildstreifen?
 **Ich muss HIMAGELISTs unterstützen**

 Wenn für Ihren Code bereits ein Image-Strip vorhanden ist, den Sie aktualisieren möchten, um den Image-Service zu verwenden, Sie jedoch durch APIs eingeschränkt sind, die das Übergeben von Bildlisten erfordern, können Sie dennoch die Vorteile des Image-Service nutzen. Um einen monikerbasierten Bildstreifen zu erstellen, führen Sie die folgenden Schritte aus, um ein Manifest aus vorhandenen Monikern zu erstellen.

1. Führen Sie das **ManifestFromResources-Tool** aus und übergeben Sie es an den Image-Strip. Dadurch wird ein Manifest für den Streifen generiert.

   - Empfohlen: Geben Sie einen nicht standardmäßigen Namen für das Manifest an, der seiner Verwendung entspricht.

2. Wenn Sie nur **KnownMonikers**verwenden, gehen Sie wie folgt vor:

   - Ersetzen \<Sie den Abschnitt Bilder \<> des Manifests durch Bilder/>.

   - Entfernen Sie alle Unterbild-IDs (alles mit \<dem Imagestrip-Namen>_.

   - Empfohlen: Benennen Sie das AssetsGuid-Symbol und das Bildstreifensymbol entsprechend seiner Verwendung um.

   - Ersetzen Sie die GUID von **containedImage**durch die GUID von '(ImageCatalogGuid), ersetzen Sie die ID von **containedImage**durch '(\<moniker>), und fügen Sie jedem **ContainedImage** das External="true"-Attribut hinzu.

       - \<moniker> sollte durch den **KnownMoniker** ersetzt werden, der dem Bild, aber mit den "KnownMonikers" entspricht. aus dem Namen entfernt.

   - Fügen Sie <Import Manifest="\\ (ManifestFolder)<\>Relativen Installations-Dir-Pfad zu *\* ,,Microsoft.VisualStudio.ImageCatalog.imagemanifest" /> oben im Abschnitt \<Symbole> hinzu.

       - Der relative Pfad wird durch den Bereitstellungsort bestimmt, der in der Setuperstellung für das Manifest definiert ist.

3. Führen Sie das **ManifestToCode-Tool** aus, um Wrapper zu generieren, sodass der vorhandene Code über einen Moniker verfügt, mit dem der Image-Service für den Image-Strip abgefragt werden kann.

   - Empfohlen: Geben Sie nicht standardmäßige Namen für die Wrapper und Namespaces an, die ihrer Verwendung entsprechen.

4. Führen Sie alle Hinzufügen, Setup-Authoring/-Bereitstellung und andere Codeänderungen aus, um mit dem Image-Service und den neuen Dateien zu arbeiten.

   Beispielmanifest, das sowohl interne als auch externe Bilder einschließen soll, um zu sehen, wie es aussehen sollte:

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **Ich brauche HIMAGELISTs nicht zu unterstützen**

1. Bestimmen Sie den Satz von **KnownMonikers,** die den Bildern in Ihrem Bildstreifen entsprechen, oder erstellen Sie eigene Moniker für die Bilder in Ihrem Bildstreifen.

2. Aktualisieren Sie die Zuordnung, die Sie verwendet haben, um das Bild am erforderlichen Index im Bildstreifen abzubekommen, um stattdessen die Moniker zu verwenden.

3. Aktualisieren Sie Ihren Code, um den Image-Service zu verwenden, um Moniker über die aktualisierte Zuordnung anzufordern. (Dies kann bedeuten, dass Sie **auf CrispImages** für verwalteten Code aktualisieren oder HBITMAPs oder HICONs vom Image-Service anfordern und für systemeigenen Code übergeben.)

## <a name="testing-your-images"></a>Testen Ihrer Bilder
 Sie können das Tool Image Library Viewer verwenden, um Ihre Bildmanifeste zu testen, um sicherzustellen, dass alles korrekt erstellt wurde. Sie finden das Tool im [Visual Studio 2015 SDK](visual-studio-sdk.md). Dokumentation für dieses und andere Dokumente finden Sie [hier](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015).

## <a name="additional-resources"></a>Zusätzliche Ressourcen

### <a name="samples"></a>Beispiele
 Einige Visual Studio-Beispiele auf GitHub wurden aktualisiert, um zu zeigen, wie der Image-Service als Teil verschiedener Visual Studio-Erweiterbarkeitspunkte verwendet wird.

 Überprüfen [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Sie, ob die neuesten Beispiele enthalten sind.

### <a name="tooling"></a>Tools
 Eine Reihe von Support-Tools für den Image-Service wurde erstellt, um die Erstellung/Aktualisierung der Benutzeroberfläche zu unterstützen, die mit dem Image Service funktioniert. Weitere Informationen zu den einzelnen Tools finden Sie in der Dokumentation zu den Tools. Die Tools sind Teil des [Visual Studio 2015 SDK](visual-studio-sdk.md).

 **ManifestFromResources**

 Das Werkzeug "Manifest aus Ressourcen" erstellt eine Liste der Bildressourcen (PNG oder XAML) und generiert eine Bildmanifestdatei für die Verwendung dieser Bilder mit dem Image-Service.

 **ManifestToCode**

 Das Werkzeug Manifest zu Code nimmt eine Bildmanifestdatei und generiert eine Wrapperdatei zum Verweisen auf die Manifestwerte in Codedateien (C++, C oder VB) oder *.vsct-Dateien.*

 **ImageLibraryViewer**

 Das Bildbibliotheks-Viewer-Tool kann Bildmanifeste laden und ermöglicht es dem Benutzer, sie auf die gleiche Weise zu bearbeiten, wie Visual Studio sicherstellen würde, dass das Manifest ordnungsgemäß erstellt wird. Der Benutzer kann Hintergrund, Größen, DPI-Einstellung, hohen Kontrast und andere Einstellungen ändern. Außerdem werden Ladeinformationen angezeigt, um Fehler in den Manifesten zu finden, und Quellinformationen für jedes Bild im Manifest angezeigt.

## <a name="faq"></a>Häufig gestellte Fragen

- Gibt es Abhängigkeiten, die Sie \<beim Laden von Reference Include="Microsoft.VisualStudio.* einschließen müssen? Interop.14.0.DesignTime" />?

  - Legen Sie EmbedInteropTypes="true" für alle Interop-DLLs fest.

- Wie setze ich ein Imagemanifest mit meiner Erweiterung bereit?

  - Fügen Sie ihrem Projekt die *.imagemanifest-Datei* hinzu.

  - Legen Sie "In VSIX einschließen" auf True fest.

- Ich aktisiere mein CPS-Projektsystem. Was ist mit **ImageName** und **StockIconService**passiert?

  - Diese wurden entfernt, als CPS aktualisiert wurde, um Moniker zu verwenden. Sie müssen nicht mehr den **StockIconService**aufrufen, sondern einfach den gewünschten **KnownMoniker** mithilfe der **ToProjectSystemType()-Erweiterungsmethode** in den CPS-Dienstprogrammen an die Methode oder Eigenschaft übergeben. Eine Zuordnung von **ImageName** zu **KnownMonikers** finden Sie unten:

    |||
    |-|-|
    |**ImageName**|**KnownMoniker**|
    |ImageName.OfflineWebApp|KnownImageIds.Web|
    |ImageName.WebReferencesFolder|KnownImageIds.Web|
    |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName.ReferenceFolder|KnownImageIds.Referenz|
    |ImageName.Referenz|KnownImageIds.Referenz|
    |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |ImageName.Folder|KnownImageIds.FolderClosed|
    |ImageName.OpenFolder|KnownImageIds.FolderOpened|
    |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|
    |ImageName.ExcludedFile|KnownImageIds.HiddenFile|
    |ImageName.DependentFile|KnownImageIds.GenerateFile|
    |ImageName.MissingFile|KnownImageIds.DocumentWarning|
    |ImageName.WindowsForm|KnownImageIds.WindowsForm|
    |ImageName.WindowsUserControl|KnownImageIds.UserControl|
    |ImageName.WindowsComponent|KnownImageIds.ComponentFile|
    |ImageName.XmlSchema|KnownImageIds.XMLSchema|
    |ImageName.XmlFile|KnownImageIds.XMLFile|
    |ImageName.WebForm|KnownImageIds.Web|
    |ImageName.WebService|KnownImageIds.WebService|
    |ImageName.WebUserControl|KnownImageIds.WebUserControl|
    |ImageName.WebCustomUserControl|BekannteImageIds.WebCustomControl|
    |ImageName.AspPage|KnownImageIds.ASPFile|
    |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|
    |ImageName.WebConfig|KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |ImageName.StyleSheet|KnownImageIds.StyleSheet|
    |ImageName.ScriptFile|KnownImageIds.JSScript|
    |ImageName.TextFile|KnownImageIds.Document|
    |ImageName.SettingsFile|KnownImageIds.Einstellungen|
    |ImageName.Resources|KnownImageIds.DocumentGroup|
    |ImageName.Bitmap|KnownImageIds.Image|
    |ImageName.Icon|KnownImageIds.IconFile|
    |ImageName.Bild|KnownImageIds.Image|
    |ImageName.ImageMap|KnownImageIds.ImageMapFile|
    |ImageName.XWorld|KnownImageIds.XWorldFile|
    |ImageName.Audio|KnownImageIds.Sound|
    |ImageName.Video|KnownImageIds.Media|
    |ImageName.Cab|KnownImageIds.CABProject|
    |ImageName.Jar|KnownImageIds.JARFile|
    |ImageName.DataEnvironment|KnownImageIds.DataTable|
    |ImageName.PreviewFile|KnownImageIds.Report|
    |ImageName.DanglingReferenz|KnownImageIds.ReferenceWarning|
    |ImageName.XsltFile|KnownImageIds.XSLTransform|
    |ImageName.Cursor|KnownImageIds.CursorFile|
    |ImageName.AppDesignerFolder|KnownImageIds.Property|
    |ImageName.Daten|KnownImageIds.Database|
    |ImageName.Anwendung|KnownImageIds.Application|
    |ImageName.DataSet|KnownImageIds.DatabaseGroup|
    |ImageName.Pfx|KnownImageIds.Certificate|
    |ImageName.Snk|KnownImageIds.Rule|
    |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName.CSharpProject|KnownImageIds.CSProjectNode|
    |ImageName.Empty|KnownImageIds.Blank|
    |ImageName.MissingFolder|KnownImageIds.FolderOffline|
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Ich aktisiere meinen Vervollständigungslistenanbieter. Welche **KnownMonikers** entsprechen den alten **StandardGlyphGroup-** und **StandardGlyph-Werten?**

    ||||
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemIntern|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemIntern|ConstantInternal|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemIntern|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemIntern|EnumerationIntern|
    |GlyphGroupEnum|GlyphItemFriend|EnumerationIntern|
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivat|
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemIntern|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemIntern|EventIntern|
    |GlyphGroupEvent|GlyphItemFriend|EventIntern|
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|
    |GlyphGroupException|GlyphItemIntern|ExceptionIntern|
    |GlyphGroupException|GlyphItemFriend|ExceptionIntern|
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemIntern|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupInterface|GlyphItemIntern|InterfaceIntern|
    |GlyphGroupInterface|GlyphItemFriend|InterfaceIntern|
    |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupMacro|GlyphItemPublic|MacroPublic|
    |GlyphGroupMacro|GlyphItemIntern|MacroInternal|
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal|
    |GlyphGroupMacro|GlyphItemProtected|MacroProtected|
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|
    |GlyphGroupMap|GlyphItemPublic|MapPublic|
    |GlyphGroupMap|GlyphItemIntern|MapInternal|
    |GlyphGroupMap|GlyphItemFriend|MapInternal|
    |GlyphGroupMap|GlyphItemProtected|MapProtected|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemIntern|MapItemIntern|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemIntern|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|
    |GlyphGroupMethode|GlyphItemPublic|MethodePublic|
    |GlyphGroupMethode|GlyphItemIntern|MethodeIntern|
    |GlyphGroupMethode|GlyphItemFriend|MethodeIntern|
    |GlyphGroupMethode|GlyphItemProtected|MethodProtected|
    |GlyphGroupMethode|GlyphItemPrivate|MethodePrivate|
    |GlyphGroupMethode|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupOverload|GlyphItemPublic|MethodePublic|
    |GlyphGroupOverload|GlyphItemIntern|MethodeIntern|
    |GlyphGroupOverload|GlyphItemFriend|MethodeIntern|
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|
    |GlyphGroupOverload|GlyphItemPrivate|MethodePrivate|
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|
    |GlyphGroupModule|GlyphItemIntern|ModulIntern|
    |GlyphGroupModule|GlyphItemFriend|ModulIntern|
    |GlyphGroupModule|GlyphItemProtected|ModuleProtected|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivat|
    |GlyphGroupModule|GlyphItemShortcut|ModulShortcut|
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemIntern|NamespaceIntern|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceIntern|
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|
    |GlyphGroupOperator|GlyphItemIntern|OperatorIntern|
    |GlyphGroupOperator|GlyphItemFriend|OperatorIntern|
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|
    |GlyphGroupProperty|GlyphItemIntern|PropertyInternal|
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|
    |GlyphGroupStruct|GlyphItemIntern|StructureIntern|
    |GlyphGroupStruct|GlyphItemFriend|StructureIntern|
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|
    |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|
    |GlyphGroupTemplate|GlyphItemIntern|TemplateIntern|
    |GlyphGroupTemplate|GlyphItemFriend|TemplateIntern|
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemIntern|TypeDefinitionIntern|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionIntern|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemIntern|TypIntern|
    |GlyphGroupType|GlyphItemFriend|TypIntern|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemIntern|UnionIntern|
    |GlyphGroupUnion|GlyphItemFriend|UnionIntern|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|
    |GlyphGroupVariable|GlyphItemIntern|FieldInternal|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemIntern|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemIntern|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodePublic|
    |GlyphGroupJSharpMethod|GlyphItemIntern|MethodeIntern|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodeIntern|
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodePrivate|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemIntern|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupJSharpClass|GlyphItemIntern|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemIntern|NamespaceIntern|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceIntern|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemIntern|InterfaceIntern|
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceIntern|
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile|
    |GlyphAssembly||Referenz|
    |GlyphLibrary||Bibliothek|
    |GlyphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||Dialog|
    |GlyphOpenFolder||FolderOpened|
    |GlyphClosedFolder||FolderClosed|
    |GlyphArrow||GoToNext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphcSharpExpansion||Codeausschnitt|
    |GlyphKeyword||IntellisenseKeyword|
    |GlyphEninformationen||Statusinformationen|
    |GlyphReference||ClassMethodReference|
    |GlyphRecursion||Rekursion|
    |GlyphXmlItem||Tag|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpDokument||Dokument|
    |GlyphForwardType||GoToNext|
    |GlyphCallersGraph||CallTo|
    |GlyphCallGraph||CallFrom|
    |Glyphenwarnung||StatusWarning|
    |GlyphMaybeReferenz||Questionmark|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallFrom|
    |GlyphExtensionMethode||ExtensionMethod|
    |GlyphExtensionMethodIntern||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProtected||ExtensionMethod|
    |GlyphExtensionMethodPrivat||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||XmlAttribute|
    |GlyphXmlChild||XmlElement|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||XmlNamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphxmlChildQuestion||XmlElementLowConfidence|
    |GlyphxmlChildCheck||XmlElementHighConfidence|
    |GlyphxmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarnung|
