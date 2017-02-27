---
title: "Image-Dienst und Katalog | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 37
---
# Image-Dienst und Katalog
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Cookbook enthält Leitfäden und bewährte Methoden für die Übernahme der Visual Studio-Abbilder und der Image-Katalog eingeführt in Visual Studio 2015.  
  
 Der Image-Dienst eingeführt in Visual Studio 2015 kann Entwickler die besten Bilder für das Gerät und ausgewählten Designs des Benutzers auf das Bild, einschließlich der richtigen Designs für den Kontext, in dem sie angezeigt werden. Übernahme des Image-Diensts können Hauptprobleme, die im Zusammenhang mit Asset-Verwaltung, Skalierung anzeigen und Designs zu beseitigen.  
  
|||  
|-|-|  
|**Heute Probleme**|**Projektmappen**|  
|Hintergrund Farbe mischen|Integrierte Alphablending|  
|Designs (einige) Bilder|Design-Metadaten|  
|Modus für hohe Kontraste|Ressourcen von alternativen hoher Kontrast|  
|Benötigen Sie mehrere Ressourcen für unterschiedliche DPI-Modi|Auswählbare Ressourcen mit vektorbasierte fallback|  
|Duplizieren von Bildern|Einen Bezeichner pro Bild-Konzept|  
  
 Warum übernehmen den Bilddienst?  
  
-   Immer das neueste "Pixel perfekte" Abbild in Visual Studio zu erhalten  
  
-   Sie können zu übermitteln und eigene Bilder  
  
-   Nicht erforderlich, testen die Bilder, wenn Windows neue DPI-Skalierung fügt  
  
-   Alte Architektur Hürden in den Implementierungen Adresse  
  
 Der Visual Studio-Shell-Symbolleiste, bevor und nachdem der Image-Dienst:  
  
 ![Bilddienst vorher und nachher](../extensibility/media/image-service-before-and-after.png "Image Service Before and After")  
  
## <a name="how-it-works"></a>Funktionsweise  
 Der Image-Dienst kann ein Bitmapbild für alle unterstützten Benutzeroberflächenframework angeben:  
  
-   WPF: "BitmapSource"  
  
-   WinForms: System.Drawing.Bitmap  
  
-   Win32: HBITMAP  
  
 Image-Service-Flussdiagramm  
  
 ![Bilddienst-Flussdiagramm](../extensibility/media/image-service-flow-diagram.png "Image Service Flow Diagram")  
  
 **Image-Moniker**  
  
 Ein Bild-Moniker (oder kurz Moniker) ist ein GUID-ID-Paar, das ein Bildelement oder Liste Bildelement in der Bildbibliothek eindeutig identifiziert.  
  
 **Bekannte Moniker**  
  
 Der Satz von Image-Moniker enthalten alle Visual Studio-Komponente oder die Erweiterung in der Visual Studio-Image-Katalog und öffentlich umgewandelt.  
  
 **Manifest Bilddateien**  
  
 Image-Manifest (.imagemanifest)-Dateien sind XML-Dateien, die einen Satz von Bildanlagen, die Moniker, die darstellen definieren, die Ressourcen und echten Bild oder Bilder, die jede Anlage darstellen. Image-Manifeste können eigenständige Bilder oder Bild für Legacyunterstützung Benutzeroberfläche aufgelistet. Darüber hinaus können Attribute, die auf die Anlage oder die einzelnen Bilder hinter jedem Medienobjekt festgelegt werden können, zu ändern, wann und wie diese Elemente angezeigt werden.  
  
 **Image-Manifestschema**  
  
 Ein vollständiges Abbild Manifest sieht folgendermaßen aus:  
  
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
  
 **Symbole**  
  
 Eine Lesbarkeit und Wartung erleichtern, kann das Image-Manifest Symbole für Attributwerte verwenden. Symbole sind wie folgt definiert:  
  
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
|Importieren|Importiert die Symbole der angegebenen Manifestdatei für die Verwendung im aktuellen manifest|  
|Guid|Das Symbol stellt eine GUID dar und GUID Formatierung übereinstimmen|  
|ID|Das Symbol stellt eine ID und muss eine nicht negative ganze Zahl sein|  
|Zeichenfolge|Das Symbol für einer beliebige Zeichenfolge|  
  
 Symbole sind Groß-und Kleinschreibung sowie mit $(symbol-name) Syntax verwiesen wird:  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Einige Symbole werden für alle Manifeste vordefiniert. Diese können verwendet werden, im Uri-Attribut der \< Quelle> oder \< Import> Element Verweispfade auf dem lokalen Computer.  
  
|||  
|-|-|  
|**Symbol**|**Beschreibung**|  
|CommonProgramFiles|Der Wert der Variable %CommonProgramFiles% Umgebung|  
|LocalAppData|Der Wert der Umgebungsvariablen für % LocalAppData% %|  
|ManifestFolder|Den Ordner mit der manifest-Datei|  
|Eigene Dateien|Der vollständige Pfad des Ordners "Eigene Dateien" des aktuellen Benutzers|  
|ProgramFiles|Der Wert der Umgebungsvariablen für % ProgramFiles %|  
|System|Ordner "Windows\System32"|  
|WinDir|Der Wert der Umgebungsvariablen für % WinDir %|  
  
 **Bild**  
  
 Die \< Image> -Element definiert ein Bild, das über einen Moniker verwiesen werden kann. Die GUID und ID, die zusammen genommen bilden den Image-Moniker. Der Moniker für das Image muss für die gesamte Bildbibliothek eindeutig sein. Wenn mehr als ein Abbild einen angegebenen Moniker verfügt, wird der ersten aufgetreten, die Bibliothek erstellt, die beibehalten werden.  
  
 Es muss mindestens eine Quelle enthalten. Größe neutrale Quellen über eine Vielzahl von Größen die besten Ergebnisse erhalten, aber sie sind nicht erforderlich. Wenn ein Image mit einer Größe, die nicht definiert, der Dienst angefordert wird das \< Image> Element und es ist keine Quelle Größe Neutral ist, wird der Dienst, und wählen Sie die optimale Größe-spezifische Quelle auf die angeforderte Größe zu skalieren.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|Guid|[Erforderlich] Der GUID-Teil der Image-moniker|  
|ID|[Erforderlich] Der ID-Teil der Image-moniker|  
|AllowColorInversion|[Optional, Standardwert True] Gibt an, ob das Bild die Farben umgedreht programmgesteuert auf einen dunklen Hintergrund verwendet werden kann.|  
  
 **Datenquelle**  
  
 Das \< Source> -Element definiert eine einzelne Quelle imagemedienobjekt (XAML und PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|URI|[Erforderlich] Ein URI, der definiert, in dem das Bild aus geladen werden können. Es kann eine der folgenden sein:<br /><br /> – Ein [Paket-URI](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) mithilfe der Anwendung: / / / Autorität<br />-Ein Ressourcenverweis absolute Komponente<br />– Ein Pfad zu einer Datei mit einer systemeigenen Ressource|  
|Hintergrund|[Optional] Gibt an, welche Art von Hintergrund, die die Quelle verwendet werden soll.<br /><br /> Es kann eine der folgenden sein:<br /><br /> *Light:* die Quelle kann auf einen hellen Hintergrund verwendet werden.<br /><br /> *Dunkel:*die Quelle kann auf einem dunklen Hintergrund verwendet werden.<br /><br /> *Hoher Kontrast:* die Quelle kann auf eine im Hintergrund laufende im Modus für hohe Kontraste verwendet werden.<br /><br /> *HighContrastLight:* die Quelle kann auf einen hellen Hintergrund im Modus für hohe Kontraste verwendet werden.<br /><br /> *HighContrastDark:* kann die Quelle eines dunklen Hintergrunds im Modus für hohe Kontraste verwendet werden.<br /><br /> Das Background-Attribut fehlt, kann die Quelle für im Hintergrund verwendet werden.<br /><br /> Wenn der Hintergrund ist *Licht*, *dunkel*, *HighContrastLight*, oder *HighContrastDark*, die Quelle Farben sind niemals umgekehrt. Wenn im Hintergrund weggelassen oder auf festgelegt *hoher Kontrast*, der die Umkehrung der Farben der Quelle wird gesteuert, von des Abbild **AllowColorInversion** Attribut.|  
|||  
  
 Ein \< Quelle> Element kann nur eines der folgenden optionalen untergeordneten Elemente aufweisen:  
  
||||  
|-|-|-|  
|**Element**|**Attribute (alle erforderlich)**|**Definition**|  
|\< Größe>|Wert|Die Quelle wird für Bilder der vorgegebenen Größe (in Geräteeinheiten) verwendet werden. Das Bild quadratisch sein müssen.|  
|\< SizeRange>|MinSize, MaxSize|Die Quelle wird (einschließlich) liegen für Bilder aus MinSize, MaxSize (in Geräteeinheiten) verwendet werden. Das Bild quadratisch sein müssen.|  
|\< Dimensionen>|Breite, Höhe|Die Quelle wird für Bilder von der angegebenen Breite und Höhe (in Geräteeinheiten) verwendet werden.|  
|\< DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth MaxHeight|Die Quelle wird (einschließlich) liegen für Abbilder aus die minimale Breite und Höhe für die maximale Breite/Höhe (in Geräteeinheiten) verwendet werden.|  
  
 Ein \< Quelle> -Element kann auch eine optionale umfassen \< NativeResource> Unterelement, das definiert ein \< Quelle> das aus einer verwalteten Assembly, anstatt eine systemeigene Assembly geladen wird.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|Typ|[Erforderlich] Der Typ der systemeigene Ressource, XAML oder PNG|  
|ID|[Erforderlich] Der ganzzahlige ID-Teil von systemeigenen Ressource|  
  
 **ImageList**  
  
 Die \< ImageList> -Element definiert eine Sammlung von Bildern, die in einem einzelnen Streifen zurückgegeben werden können. Balken wird bei Bedarf erstellt, je nach Bedarf.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Attribut**|**Definition**|  
|Guid|[Erforderlich] Der GUID-Teil der Image-moniker|  
|ID|[Erforderlich] Der ID-Teil der Image-moniker|  
|Extern|[Optional, Standardwert ist False.] Gibt an, ob der Image-Moniker ein Bild in das aktuelle Manifest verweist.|  
  
 Der Moniker für die enthaltene Bild hat keinen Verweis auf ein Bild in das aktuelle Manifest definiert. Wenn das enthaltene Bild in der Bildbibliothek gefunden werden kann, wird ein leeres Platzhalterbild an deren Stelle verwendet werden.  
  
## <a name="using-the-image-service"></a>Mithilfe des Image-Diensts  
  
### <a name="first-steps-managed"></a>Erste Schritte (verwaltet)  
 Um den Bilddienst verwenden, müssen Sie Ihrem Projekt Verweise auf einige oder alle der folgenden Assemblys hinzu:  
  
-   **Microsoft.VisualStudio.ImageCatalog.dll**  
  
    -   Erforderlich, wenn Sie den integrierten Image-Katalog KnownMonikers  
  
-   **Microsoft.VisualStudio.Imaging.dll**  
  
    -   Erforderlich, wenn Sie verwenden **CrispImage** und **ImageThemingUtilities** in Ihrer WPF-UI  
  
-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  
  
    -   Erforderlich, wenn Sie mithilfe der **ImageMoniker** und **ImageAttributes** Typen  
  
    -   **EmbedInteropTypes** sollte festgelegt werden, auf "true"  
  
-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  
  
    -   Erforderlich, wenn Sie mithilfe der **IVsImageService2** Typ  
  
    -   **EmbedInteropTypes** sollte festgelegt werden, auf "true"  
  
-   **Microsoft.VisualStudio.Utilities.dll**  
  
    -   Erforderlich, wenn Sie mithilfe der **BrushToColorConverter** für die ImageThemingUtilities.**ImageBackgroundColor** in Ihrer WPF-Benutzeroberfläche  
  
-   **Microsoft.VisualStudio.Shell. \< VSVersion>.0**  
  
    -   Erforderlich, wenn Sie mithilfe der **IVsUIObject** Typ  
  
-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  
  
    -   Erforderlich, wenn Sie die Benutzeroberfläche WinForms-bezogene verwenden  
  
    -   **EmbedInteropTypes** sollte festgelegt werden, auf "true"  
  
### <a name="first-steps-native"></a>Erste Schritte (systemeigen)  
 Um die Abbilder zu verwenden, müssen Sie einige oder alle der folgenden Header zu Ihrem Projekt enthalten:  
  
-   **KnownImageIds.h**  
  
    -   Erforderlich, wenn Sie das Verwenden des Katalogs integrierte Bild **KnownMonikers**, allerdings nicht mit der **ImageMoniker** Typ, z. B. wenn die Rückgabe von Werten **IVsHierarchy GetGuidProperty** oder **GetProperty** aufrufen.  
  
-   **KnownMonikers.h**  
  
    -   Erforderlich, wenn Sie das Verwenden des Katalogs integrierte Bild **KnownMonikers**.  
  
-   **ImageParameters140.h**  
  
    -   Erforderlich, wenn Sie mithilfe der **ImageMoniker** und **ImageAttributes** Typen.  
  
-   **VSShell140.h**  
  
    -   Erforderlich, wenn Sie mithilfe der **IVsImageService2** Typ.  
  
-   **ImageThemingUtilities.h**  
  
    -   Erforderlich, wenn Sie nicht den Image-Dienst Designs für Sie handhaben lassen können.  
  
    -   Verwenden Sie diesen Header nicht, wenn die Abbilder der Image-Designs behandeln kann.  
  
-   **VSUIDPIHelper.h**  
  
    -   Erforderlich, wenn Sie die DPI-Hilfsprogramme verwenden, um den aktuellen DPI-Wert zu erhalten.  
  
## <a name="how-do-i-write-new-wpf-ui"></a>Wie schreibe ich neue WPF UI?  
  
1.  Beginnen Sie mit dem Hinzufügen von Assemblyverweisen, die in der oben genannten erforderlich zunächst die Schritte im Abschnitt zu Ihrem Projekt. Sie müssen nicht alle hinzufügen, also fügen Sie nur die Verweise, die Sie benötigen. (Hinweis: Wenn Sie verwenden oder aber auf **Farben** anstelle von **Pinsel**, dann können Sie den Verweis auf überspringen **Hilfsprogramme**, da Sie nicht den Konverter benötigen.)  
  
2.  Wählen Sie das gewünschte Abbild aus, und rufen Sie seinen Moniker. Verwenden Sie eine **KnownMoniker**, oder verwenden Sie eine eigene, wenn Sie eigene benutzerdefinierte Bilder und der Moniker haben.  
  
3.  Hinzufügen **CrispImages** auf XAML-CODE. (Siehe folgende Beispiel).  
  
4.  Legen Sie die **ImageThemingUtilities.ImageBackgroundColor** Eigenschaft in der Hierarchie der Benutzeroberfläche. (Dies sollte festgelegt werden, an dem Speicherort, in dem die Farbe des Hintergrunds bekannt ist, nicht unbedingt auf, den **CrispImage**.) (Siehe folgende Beispiel).  
  
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
  
 **Wie aktualisiere ich die vorhandenen WPF UI?**  
  
 Aktualisieren vorhandener WPF-UI ist ein relativ einfacher Prozess, der aus drei grundlegenden Schritten besteht:  
  
1.  Ersetzen Sie alle \< Image> Elemente auf der Benutzeroberfläche mit \< CrispImage> Elemente  
  
2.  Alle Attribute für Datenquellen auf Moniker Attribute ändern  
  
    -   Wenn das Bild nicht geändert, und Sie verwenden **KnownMonikers**, dann statisch binden, ist diese Eigenschaft die **KnownMoniker**. (Siehe Beispiel oben).  
  
    -   Wenn das Bild ändert sich nie, und eines benutzerdefinierten Abbilds verwenden, statisch binden Sie an Ihre eigenen Moniker.  
  
    -   Wenn das Bild ändern kann, binden Sie die Moniker-Attribut an eine Code-Eigenschaft, die auf Änderungen an den Eigenschaften benachrichtigt.  
  
3.  Legen Sie an einer beliebigen Stelle in der Hierarchie der Benutzeroberfläche **ImageThemingUtilities.ImageBackgroundColor** stellen Sie sicher, dass farbumkehrung ordnungsgemäß funktioniert.  
  
    -   Möglicherweise ist die Verwendung von erforderlich die **BrushToColorConverter** Klasse. (Siehe Beispiel oben).  
  
## <a name="how-do-i-update-win32-ui"></a>Wie wird die aktualisiert Win32-UI?  
 Fügen Sie folgenden Code, sofern angebracht, das unformatierte Laden von Bildern zu ersetzen. Wechseln Sie Werte für die Rückgabe von HBITMAPs nicht im Vergleich zu HICONs im Vergleich zu HIMAGELIST nach Bedarf.  
  
 **Den Image-Dienst abrufen**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **Das Bild anfordern**  
  
```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  
  
CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  
  
```  
  
## <a name="how-do-i-update-winforms-ui"></a>Wie aktualisiere ich WinForms UI?  
 Fügen Sie folgenden Code, sofern angebracht, das unformatierte Laden von Bildern zu ersetzen. Wechseln Sie Werte für die Rückgabe von Bitmaps und Symbole nach Bedarf.  
  
 **Nützliche mit-Anweisung**  
  
```c#  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **Den Image-Dienst abrufen**  
  
```c#  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **Fordern Sie das Bild**  
  
```c#  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  
  
// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  
  
Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  
  
```  
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Wie verwende ich die Image-Moniker in ein neues Toolfenster?  
 Die VSIX-Paket-Projektvorlage wurde für Visual Studio 2015 aktualisiert. Um ein neues Toolfenster zu erstellen, mit der rechten Maustaste auf das VSIX-Projekt, und wählen Sie "Neues Element hinzufügen" (STRG + UMSCHALT + A). Wählen Sie unter dem Knoten Erweiterbarkeit für die Sprache des Projekts "Benutzerdefinierte Toolfenster", benennen Sie dem Toolfenster, und klicken Sie auf die Schaltfläche "Hinzufügen".  
  
 Diese stellen die wichtigsten Moniker in einem Toolfenster verwenden. Führen Sie die Schritte für jede:  
  
1.  Die Registerkarte Tool bei die Registerkarten klein genug (auch in der Strg + Tab Fenster Switcher verwendet).  
  
     Fügen Sie diese Zeile an den Konstruktor für die Klasse, abgeleitet wird, die **ToolWindowPane** Typ:  
  
    ```c#  
    // Replace this KnownMoniker with your desired ImageMoniker  
    this.BitmapImageMoniker = KnownMonikers.Blank;  
    ```  
  
2.  Der Befehl, um das Toolfenster zu öffnen.  
  
     Bearbeiten Sie in der VSCT-Datei für das Paket das Toolfenster Befehlsschaltfläche:  
  
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
  
 **Wie verwende ich die Image-Moniker in eine vorhandene Toolfenster?**  
  
 Aktualisieren einer vorhandenen Toolfenster zum Bild Moniker verwenden, ähnelt die Schritte zum Erstellen eines neuen Toolfensters.  
  
 Diese stellen die wichtigsten Moniker in einem Toolfenster verwenden. Führen Sie die Schritte für jede:  
  
1.  Die Registerkarte Tool bei die Registerkarten klein genug (auch in der Strg + Tab Fenster Switcher verwendet).  
  
    1.  Entfernen Sie diese Zeilen im Konstruktor für die Klasse, abgeleitet wird (falls vorhanden) die **ToolWindowPane** Typ:  
  
        ```c#  
        this.BitmapResourceID = <Value>;  
        this.BitmapIndex = <Value>;  
        ```  
  
    2.  Siehe Schritt 1 # die "Wie kann ich verwenden Bild Monikern in ein neues Toolfenster?" Im obigen Abschnitt.  
  
2.  Der Befehl, um das Toolfenster zu öffnen.  
  
    -   Siehe Schritt #2 der "Wie kann ich verwenden Bild Monikern in ein neues Toolfenster?" Im obigen Abschnitt.  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Wie verwende ich die Image-Moniker in einer VSCT-Datei?  
 Die VSCT-Datei zu aktualisieren, wie durch die folgenden kommentierten Zeilen:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
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
  
 **Was geschieht, wenn mein VSCT-Datei muss außerdem von älteren Versionen von Visual Studio gelesen werden?**  
  
 Ältere Versionen von Visual Studio nicht erkennen die **IconIsMoniker** Befehl Flag. In Versionen von Visual Studio, die unterstützt wird, aber weiterhin im alten Stil Bilder auf älteren Versionen von Visual Studio verwenden, können Sie Bilder aus der Image-Dienst verwenden. Zu diesem Zweck würde Sie lassen die VSCT-Datei unverändert (und daher kompatibel mit früheren Versionen von Visual Studio), und erstellen Sie eine CSV (durch Trennzeichen getrennte Werte)-Datei, die zugeordnet von GUID-ID-Paaren, die in einer VSCT-Datei definiert \< Bitmaps> Element Image Moniker GUID-ID-Paaren.  
  
 Das Format der CSV-Zuordnungsdatei ist:  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 Die CSV-Datei mit dem Paket bereitgestellt wird und seine Position wird angegeben, indem die **IconMappingFilename** Eigenschaft von der **ProvideMenuResource** Paketattribut:  
  
```c#  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
 Die **IconMappingFilename** ist entweder ein relativer Pfad implizit als Stammknoten $PackageFolder$ (wie im Beispiel oben) oder ein absoluter Pfad Stammknoten explizit ein Verzeichnis an, wie z. B. durch eine Umgebungsvariable definiert @"%UserProfile%\dir1\dir2\MyMappingFile.csv".  
  
## <a name="how-do-i-port-a-project-system"></a>Wie port ich ein Projektsystem?  
 **Gewusst wie: Angeben von ImageMonikers für ein Projekt**  
  
1.  Implementieren **VSHPROPID_SupportsIconMonikers** für des Projekts **IVsHierarchy**, und geben "true" zurück.  
  
2.  Implementieren Sie entweder **VSHPROPID_IconMonikerImageList** (wenn das ursprüngliche Projekt verwendet **VSHPROPID_IconImgList**) oder **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (wenn das ursprüngliche Projekt verwendet **VSHPROPID_IconHandle** und **VSHPROPID_OpenFolderIconHandle**).  
  
3.  Ändern Sie die Implementierung von der ursprünglichen VSHPROPIDs für Symbole "legacy" Versionen der Symbole zu erstellen, wenn Erweiterungspunkte diese anfordern. **IVsImageService2** bietet Funktionen zum Abrufen der entsprechenden Symbole  
  
 **Zusätzliche Anforderungen für VB / Arten von C#-Projekt**  
  
 Implementieren Sie nur **VSHPROPID_SupportsIconMonikers** wenn Sie feststellen, dass das Projekt ist die **äußersten Flavor**. Andernfalls der tatsächlichen äußersten Flavor unterstützen möglicherweise keine Image-Moniker in Wirklichkeit und der Basis Ausführung möglicherweise effektiv "ausblenden" benutzerdefinierte Abbilder.  
  
 **Wie verwende ich Image Moniker in CPS?**  
  
 Festlegen benutzerdefinierter Bilder in CPS (gemeinsames Projektsystem) möglich, manuell oder über eine Elementvorlage, die mit dem Projekt System Erweiterbarkeit SDK geliefert wird.  
  
 **Verwenden die System-Projekterweiterbarkeit SDK**  
  
 Folgen Sie den Anweisungen am [Geben Sie benutzerdefinierte Symbole für den Typ/Projektelement](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) CPS Bildern anpassen. Weitere Informationen zu CPS finden Sie unter [Visual Studio-Projekt System Erweiterbarkeit – Dokumentation](https://github.com/Microsoft/VSProjectSystem)  
  
 **Verwenden Sie ImageMonikers manuell**  
  
1.  Implementieren und exportieren Sie die **IProjectTreeModifier** Schnittstelle in Ihrem Projektsystem.  
  
2.  Bestimmt, welche **KnownMoniker** oder benutzerdefiniertes Image-Moniker, die Sie verwenden möchten.  
  
3.  In der **ApplyModifications** -Methode, gehen an einer beliebigen Stelle in der Methode vor der Rückgabe der neuen Struktur ähnelt der folgenden Beispiel:  
  
    ```c#  
    // Replace this KnownMoniker with your desired ImageMoniker  
    tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
    ```  
  
4.  Wenn Sie eine neue Struktur erstellen, können Sie benutzerdefinierte Bilder festlegen, durch Übergeben der gewünschten Moniker an die Methode "NewTree", die ähnlich wie das folgende Beispiel:  
  
    ```c#  
    // Replace this KnownMoniker with your desired ImageMoniker  
    ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
    ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  
  
    return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                 /*filePath*/<value>,  
                                                 /*browseObjectProperties*/<value>,  
                                                 icon,  
                                                 expandedIcon);  
    ```  
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Wie konvertiere ich aus einem Strip echten Bild in einen Moniker-basiertes Abbild Streifen?  
 **Ich benötige Unterstützung HIMAGELISTs**  
  
 Wenn ein bereits vorhandenes Image Streifen für Ihren Code, den Sie aktualisieren, um der Image-Dienst verwenden möchten, aber Sie werden durch die APIs, die Weitergabe von Bildlisten erfordern beschränkt, erhalten Sie weiterhin die Vorteile der Image-Diensts. Um einen Moniker-basiertes Abbild Streifen zu erstellen, gehen Sie zum Erstellen eines Manifests aus vorhandenen Moniker.  
  
1.  Führen Sie die **ManifestFromResources** Tool, und übergeben sie die Bild-Menüleiste. Dadurch wird ein Manifest für den Bereichsstreifen generiert.  
  
    -   Empfohlen: Geben Sie einen nicht standardmäßigen Namen für das Manifest entsprechend ihrer Verwendung.  
  
2.  Wenn Sie nur verwenden, **KnownMonikers**, gehen Sie folgendermaßen vor:  
  
    -   Ersetzen Sie die \< Bilder> -Abschnitt des Manifests mit \< Bilder />.  
  
    -   Entfernen Sie alle Teilbild-IDs (gar nichts mit \< Name der Imagestrip>_ ##).  
  
    -   Empfohlen: Benennen Sie die AssetsGuid und Image Streifen Symbol entsprechend ihrer Verwendung.  
  
    -   Ersetzen Sie jeden **ContainedImage**GUID mit $(ImageCatalogGuid), ersetzen Sie jeden **ContainedImage**-ID mit $(\<moniker>), und die externe = "true"-Attribut hinzuzufügen **ContainedImage**  
  
        -   \< Moniker> ersetzt werden sollte, mit der **KnownMoniker** entspricht das Bild jedoch mit "KnownMonikers." aus dem Namen entfernt.  
  
    -   Hinzufügen < Import Manifest="$(ManifestFolder)\\< Relative Installationspfad Dir zu\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\> an den Anfang der \< Symbole> Abschnitt.  
  
        -   Der relative Pfad wird durch den Speicherort der Bereitstellung in das Setup für das Manifest erstellen definiert bestimmt.  
  
3.  Führen Sie die **ManifestToCode** Tool Wrapper generieren, damit der vorhandene Code einen Moniker verfügt, sie den Image-Dienst für die Image-Menüleiste Abfragen können.  
  
    -   Empfohlen: bieten Sie nicht standardmäßigen Namen für den Wrapper und Namespaces, die ihre Verwendung anpassen.  
  
4.  Alle der hinzufügt, Erstellung, Setup und Bereitstellung und andere Änderungen am Code mit der Image-Dienst und die neuen Dateien arbeiten.  
  
 Beispiel-Manifest, einschließlich der interne und externe Bilder, um zu sehen, wie es aussehen sollte:  
  
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
  
 **Ich möchte nicht HIMAGELISTs zu unterstützen.**  
  
1.  Ermitteln, welche **KnownMonikers** die Bilder in Ihrem Image Bereichsstreifen entsprechen, oder erstellen Sie eigene Moniker für die Bilder auf Ihrem Image Streifen.  
  
2.  Aktualisieren Sie beliebige Zuordnung verwendet wird, an dem erforderlichen Index in dem Bild klickt, verwenden Sie stattdessen die Moniker abrufen.  
  
3.  Aktualisieren Sie den Code zur Verwendung des Image-Diensts über die aktualisierte Zuordnung Moniker anfordern. (Dies kann bedeuten, dass zum Aktualisieren **CrispImages** für verwalteten Code oder HBITMAPs nicht oder HICONs aus dem Image-Dienst anfordert und sie um für systemeigenen Code übergeben werden.)  
  
## <a name="testing-your-images"></a>Testen Ihre images  
 Das Image Library-Viewer-Tool können Sie testen die Image-Manifeste, um sicherzustellen, dass alles richtig erstellt wurde. Sie finden das Tool in der [Visual Studio 2015 SDK](http://msdn.microsoft.com/library/bb166441.aspx). Dokumentation zu diesem und anderen Tools verwendbaren [hier](http://aka.ms/VSImageThemeTools).  
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
  
### <a name="samples"></a>Proben  
 Einige der Visual Studio-Beispiele auf GitHub wurden aktualisiert, damit Sie wie den Image-Dienst als Teil der verschiedenen Punkte zur Erweiterbarkeit von Visual Studio verwenden können.  
  
 Überprüfen Sie [http://github.com/Microsoft/VSSDK-Extensibility-Samples](http://github.com/Microsoft/VSSDK-Extensibility-Samples) für aktuelle Beispiele.  
  
### <a name="tooling"></a>Tools  
 Ein Satz von Supporttools für den Image-Dienst wurde erstellt, zur Unterstützung der Benutzeroberfläche, die mit der Image-Dienst erstellt/aktualisiert. Weitere Informationen zu den einzelnen Tools überprüfen Sie die Dokumentation, die mit den Tools. Die Tools sind Bestandteil der [Visual Studio 2015 SDK.](http://msdn.microsoft.com/library/bb166441.aspx)  
  
 **ManifestFromResources**  
  
 Das Manifest von Ressourcen-Tool kann eine Liste von Bildressourcen (PNG oder XAML) und generiert eine Image-Manifestdatei für diese Images mit der Image-Dienst verwenden.  
  
 **ManifestToCode**  
  
 Manifest Code Tool nimmt eine Image-manifest-Datei und generiert eine Wrapperdatei für die Manifestdatei Werte in Code (C++, c# oder VB) oder VSCT-Dateien verweisen.  
  
 **ImageLibraryViewer**  
  
 Das Image-Bibliothek-Viewer-Tool Manifeste Bild laden, und ermöglicht dem Benutzer, die sie auf die gleiche Weise zu bearbeiten, die Visual Studio würde, um sicherzustellen, dass das Manifest ordnungsgemäß erstellt wurde. Der Benutzer kann Hintergrund, Größen, DPI-Einstellung, Kontrast und andere Einstellungen ändern. Außerdem zeigt das Laden von Informationen zum Suchen von Fehlern in den Manifesten und Quellinformationen für jedes Bild im Manifest angezeigt.  
  
## <a name="faq"></a>FAQ  
  
-   Gibt es keine Abhängigkeiten, die Sie einschließen muss, wenn beim Laden \< Verweis Include="Microsoft.VisualStudio.*. Interop.14.0.DesignTime"/>?  
  
    -   Legen Sie EmbedInteropTypes = "true" für alle Interop-DLLs.  
  
-   Wie bereit kann ich ein Bild Manifest mit my-Erweiterung?  
  
    -   Die .imagemanifest-Datei dem Projekt hinzufügen.  
  
    -   Legen Sie "Include in VSIX-Datei" auf "true" fest.  
  
-   Ich habe meine CPS-Projektsystem aktualisiert. Wo befindet sich **ImageName** und **StockIconService**?  
  
    -   o wurden diese entfernt, wenn CPS aktualisiert wurde, dass um Moniker zu verwenden. Mehr aufrufen, müssen die **StockIconService**, übergeben Sie einfach die gewünschte **KnownMoniker** an die Methode oder Eigenschaft mit dem **ToProjectSystemType()** Erweiterungsmethode in der CPS-Hilfsprogramme. Finden Sie eine Zuordnung von **ImageName** auf **KnownMonikers** unten:  
  
        |||  
        |-|-|  
        |**ImageName**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
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
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
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
  
    -   Ich bin Dienstanbieters Liste Abschluss aktualisiert. Was **KnownMonikers** übereinstimmen, auf das alte **StandardGlyphGroup** und **StandardGlyph** Werte?  
  
        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
        |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
        |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
        |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
        |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
        |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
        |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
        |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
        |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
        |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
        |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
        |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
        |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
        |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
        |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
        |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
        |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
        |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
        |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
        |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
        |GlyphGroupField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
        |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
        |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
        |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
        |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
        |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
        |GlyphGroupMap|GlyphItemPublic|MapPublic|  
        |GlyphGroupMap|GlyphItemInternal|MapInternal|  
        |GlyphGroupMap|GlyphItemFriend|MapInternal|  
        |GlyphGroupMap|GlyphItemProtected|MapProtected|  
        |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
        |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
        |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
        |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
        |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
        |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
        |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
        |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
        |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
        |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
        |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
        |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
        |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
        |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
        |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
        |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
        |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
        |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
        |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
        |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
        |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
        |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
        |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
        |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
        |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
        |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
        |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
        |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
        |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
        |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
        |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
        |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
        |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
        |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
        |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
        |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
        |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
        |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
        |GlyphGroupType|GlyphItemPublic|TypePublic|  
        |GlyphGroupType|GlyphItemInternal|TypeInternal|  
        |GlyphGroupType|GlyphItemFriend|TypeInternal|  
        |GlyphGroupType|GlyphItemProtected|TypeProtected|  
        |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
        |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
        |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
        |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
        |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
        |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
        |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
        |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
        |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
        |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
        |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
        |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
        |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
        |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
        |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
        |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
        |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
        |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
        |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
        |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
        |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupError||StatusError|  
        |GlyphBscFile||ClassFile|  
        |GlyphAssembly||Verweis|  
        |GlyphLibrary||Bibliothek|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||Dialogfeld|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||GoToNext|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||Codeausschnitt|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||Rekursion|  
        |GlyphXmlItem||Tag|  
        |GlyphJSharpProject||Dokumentensammlung|  
        |GlyphJSharpDocument||Dokument|  
        |GlyphForwardType||GoToNext|  
        |GlyphCallersGraph||CallTo|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||QuestionMark|  
        |GlyphMaybeCaller||CallTo|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||XmlAttribute|  
        |GlyphXmlChild||XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||XmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|