---
title: "Manifest aus Ressourcen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Manifest aus Ressourcen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Manifest von Ressourcen\-Tool ist eine Konsolenanwendung, die eine Liste von Bildressourcen \(PNG oder XAML\-Dateien\) und generiert eine .imagemanifest\-Datei, die diese Abbilder mit dem Visual Studio\-Bild\-Dienst verwendet werden kann. Darüber hinaus kann dieses Tool zum Hinzufügen von Bildern in einem vorhandenen .imagemanifest verwendet werden. Dieses Tool ist nützlich für die Unterstützung von High\-DPI und\-Design für Bilder in einer Visual Studio\-Erweiterung hinzufügen. Die generierte .imagemanifest\-Datei sollte in enthalten und als Teil von Visual Studio\-Erweiterung \(VSIX\) bereitgestellt werden.  
  
## Zum Verwenden der Tools  
 **Syntax**  
  
 ManifestFromResources Systemablagen: \< Dir1 \>; \< Img1 \>\/Assembly: \< AssemblyName \>\< optionale Argumente \>  
  
 **Argumente**  
  
||||  
|-|-|-|  
|**SwitchName**|**Notizen**|**Erforderlich oder Optional**|  
|Systemablagen|Eine durch Semikolons getrennte Liste der Bilder oder Verzeichnisse. Diese Liste sollte immer die vollständige Liste der Bilder enthalten, die im Manifest werden. Wenn nur eine unvollständige Liste angegeben ist, werden die Einträge nicht enthalten gelöscht.<br /><br /> Ist eine angegebene Ressourcendatei ein Bild entfernen, wird das Tool es in einzelne Bilder aufteilen, bevor Manifest jedes Teilbild hinzugefügt.<br /><br /> Das Bild eine PNG\-Datei ist, sollten Sie den Namen wie folgt formatieren, sodass das Tool in den richtigen Attributen für das Bild ausgefüllt werden kann: \< Name \>. \< Breite \>. \< Höhe \> PNG.|Erforderlich|  
|\/ Assembly|Der Name der verwalteten Assembly \(nicht einschließlich der Erweiterung\) oder der Common Language Runtime\-Pfad der systemeigenen Assembly, die die Ressourcen \(relativ zum Speicherort für das Manifest Common Language Runtime\) hostet.|Erforderlich|  
|"\/ manifest"|Der Name der generierten .imagemanifest Datei erteilen. Dies kann auch einen absoluten oder relativen Pfad zum Erstellen der Datei an einem anderen Speicherort enthalten. Der Standardname entspricht der Name der Assembly.<br /><br /> Standard: \< aktuelles Verzeichnis \> \\ \< Assembly \> .imagemanifest|Optional|  
|\/guidName|Der Name der GUID\-Symbol für alle Bilder im generierten Manifest zugewiesen.<br /><br /> Standard: AssetsGuid|Optional|  
|\/rootPath|Der Stammpfad, die vor dem Erstellen von verwalteten Ressourcen\-URIs entfernt werden soll. \(Dieses Flag ist in Fällen helfen, in dem das Tool den relativen URI\-Pfad falsch ist, wird daher nicht geladen ruft.\)<br /><br /> Standard: \< aktuelles Verzeichnis \>|Optional|  
|\/ Recursive|Dieses Flag weist das Tool rekursiv alle Verzeichnisse im Argument Systemablagen suchen. Das Auslassen dieses Flag führt eine Suche in top\-Niveau nur Verzeichnisse.|Optional|  
|\/isNative|Legen Sie dieses Flag an, wenn das Assemblyargument einen Pfad für eine systemeigene Assembly ist. Lassen Sie dieses Flag an, wenn Sie das Assemblyargument der Name einer verwalteten Assembly ist. \(Siehe Abschnitt "Hinweise" Weitere Informationen zu diesem Flag\).|Optional|  
|\/newGuids|Dieses Flag weist das Tool zum Erstellen eines neuen Werts für Bilder GUID\-Symbol anstelle von vorhandenen Manifest zusammenführen.|Optional|  
|\/newIds|Dieses Flag weist das Tool zum Erstellen von neuen ID Symbolwerte für jedes Bild anstelle der Werte aus dem vorhandenen Manifest zusammenführen.|Optional|  
|\/noLogo|Dieses Flag wird beendet, Produkt und Copyright\-Informationen drucken.|Optional|  
|\/?|Drucken Sie Hilfeinformationen.|Optional|  
|\/help|Drucken Sie Hilfeinformationen.|Optional|  
  
 **Beispiele**  
  
-   ManifestFromResources \/resources:D:\\Images \/assembly:My.Assembly.Name \/isNative  
  
-   ManifestFromResources \/resources:D:\\Images\\Image1.png;D:\\Images\\Image1.xaml \/assembly:My.Assembly.Name \/manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources \/resources:D:\\Images\\Image1.png;D:\\Images\\Image1.xaml \/assembly:My.Assembly.Name \/guidName:MyImages \/newGuids \/newIds  
  
## Notizen  
  
-   Das Tool unterstützt nur PNG\- und XAML\-Dateien. Alle anderen Bild oder Dateitypen werden ignoriert. Für alle nicht unterstützten Typen, die bei der Analyse von Ressourcen wird eine Warnung generiert. Wenn nicht unterstützt Bilder befinden sich Abschluss das Tool analysiert die Ressourcen, wird ein Fehler generiert  
  
-   Befolgen Sie das empfohlene Format PNG\-Bilder, wird das Tool den Größe und Dimension\-Wert für die PNG der Datenbankgröße Format angegeben festlegen, auch wenn es die tatsächliche Größe des Bilds unterscheidet.  
  
-   Das Format für die Breite und Höhe für PNG\-Bilder ausgelassen werden, aber das Tool des Bilds tatsächliche Breite und Höhe lesen und verwenden Sie diese für die Größe und Dimension Wert des Bilds.  
  
-   Ausführen dieses Tools auf das gleiche Bild mehrmals für den gleichen .imagemanifest führt manifest Doppeleinträge daran, dass das Tool Bild Balken in eigenständigen Bilder aufteilen und tragen Sie in der vorhandenen Manifest.  
  
-   Zusammenführen \(vermeiden Sie \/newGuids oder \/newIds\) sollte nur für Tool\-generierte Manifeste vorgenommen werden. Manifeste, die angepasst oder auf andere Weise generiert wurden möglicherweise nicht ordnungsgemäß zusammengeführt werden.  
  
-   Nach Generierung auf ID Symbole entsprechen den Ressourcen\-IDs aus der systemeigenen Assembly RC\-Datei manuell bearbeitet werden, möglicherweise Manifeste, die für die systemeigenen Assemblys generiert werden müssen.  
  
## Beispielausgabe  
 **Bild einfach manifest**  
  
 Ein Image\-Manifest werden diese XML\-Datei ähnelt:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15197 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" /> <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" /> <ID Name="MyImage" Value="0" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImage)"> <Source Uri="$(Resources)/Xaml/MyImage.xaml" /> <Source Uri="$(Resources)/Png/MyImage.16.16.png"> <Size Value="16" /> </Source> </Image> </Images> <ImageLists /> </ImageManifest>  
```  
  
 **Image\-Manifest für ein Bild entfernen**  
  
 Ein Image\-Manifest für ein Bild Bereichsstreifen werden dieser XML\-Datei ähnelt:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15197 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" /> <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" /> <ID Name="MyImageStrip_0" Value="1" /> <ID Name="MyImageStrip_1" Value="2" /> <ID Name="MyImageStrip" Value="3" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)"> <Source Uri="$(Resources)/MyImageStrip_0.png"> <Size Value="16" /> </Source> </Image> <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)"> <Source Uri="$(Resources)/MyImageStrip_1.png"> <Size Value="16" /> </Source> </Image> </Images> <ImageLists> <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)"> <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" /> <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" /> </ImageList> </ImageLists> </ImageManifest>  
```  
  
 **Image\-Manifest für systemeigene Assembly Bildressourcen**  
  
 Ein Image\-Manifest für systemeigene Abbilder wird in dieser XML\-Datei ähnlich sein:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15198 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" /> <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" /> <ID Name="MyImage1" Value="0" /> <ID Name="MyImage2" Value="1" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImage1)"> <Source Uri="$(Resources)"> <Size Value="16" /> <NativeResource ID="$(MyImage1)" Type="PNG" /> </Source> </Image> <Image Guid="$(AssetsGuid)" ID="$(MyImage2)"> <Source Uri="$(Resources)"> <Size Value="16" /> <NativeResource ID="$(MyImage2)" Type="PNG" /> </Source> </Image> </Images> <ImageLists /> </ImageManifest>  
```