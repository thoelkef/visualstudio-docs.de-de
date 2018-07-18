---
title: Assemblymanifest aus Ressourcen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 514135e5c6ba932d7b3b4319dd39c1df4e8cb212
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134280"
---
# <a name="manifest-from-resources"></a>Assemblymanifest aus Ressourcen
Die Manifestdatei aus Ressourcen Tool ist eine Konsolenanwendung, die eine Liste von Bildressourcen (PNG oder XAML-Dateien) und generiert eine .imagemanifest-Datei, die diesen Images, die mit der Visual Studio-Image-Dienst verwendet werden kann. Darüber hinaus kann dieses Tool verwendet werden, um eine vorhandene .imagemanifest Bilder hinzufügen. Dieses Tool eignet sich für Unterstützung hoher DPI-Einstellung und Designs für die Bilder für ein Visual Studio-Erweiterung hinzufügen. Die generierte .imagemanifest-Datei sollte in enthalten und als Teil einer Visual Studio-Erweiterung (VSIX) bereitgestellt werden.  
  
## <a name="how-to-use-the-tool"></a>Gewusst wie: Verwenden Sie das tool  
 **Syntax**  
  
 ManifestFromResources Systemablagen:\<Dir1 >;\< Img1 >/Assembly:\<AssemblyName > \<Optional Args >  
  
 **Argumente**  
  
||||  
|-|-|-|  
|**SwitchName**|**Notizen**|**Erforderlich oder Optional**|  
|Systemablagen|Eine durch Semikolons getrennte Liste der Bilder oder Verzeichnisse. Diese Liste sollte immer die vollständige Liste der Bilder enthalten, die im Manifest werden. Wenn nur eine nicht erschöpfende Liste angegeben ist, werden die Einträge nicht enthalten verloren gehen.<br /><br /> Wenn eine angegebene Ressourcendatei ein Bild Bereichsstreifen ist, wird das Tool sie in separate Bilder aufgeteilt vor dem Hinzufügen jedes Teilbild dem Manifest.<br /><br /> Wenn das Bild eine PNG-Datei ist, wird empfohlen, damit das Tool in der richtigen Attribute für das Bild gefüllt werden kann, formatieren den Namen wie folgt: \<Name >.\< Breite >. \<Höhe > PNG.|Erforderlich|  
|/ Assembly|Der Name der verwalteten Assembly (nicht einschließlich der Erweiterung) oder der Common Language Runtime-Pfad der systemeigenen Assembly, die die Ressourcen (relativ zum Speicherort für das Manifest Common Language Runtime) hostet.|Erforderlich|  
|"/ manifest"|Der Name der generierten .imagemanifest Datei erteilen. Dies kann auch einen absoluten oder relativen Pfad zum Erstellen der Datei an einem anderen Speicherort umfassen. Der Standardname entspricht der Name der Assembly.<br /><br /> Standard: \<aktuelles Verzeichnis >\\< Assembly\>.imagemanifest|Optional|  
|/guidName|Der Name für das GUID-Symbol für alle Bilder in das generierte Manifest.<br /><br /> Standard: AssetsGuid|Optional|  
|/rootPath|Der Stammpfad, der vor dem Erstellen der verwalteten Ressourcen-URIs übrig werden muss. (Dieses Kennzeichen ist beim Fällen hilfreich sein, in dem das Tool den relativen URI-Pfad falsch sein, sodass Ressourcen, um Fehler beim Laden der ruft.)<br /><br /> Standard: \<aktuellen Verzeichnis >|Optional|  
|/ Recursive|Wenn dieses Flag weist das Tool rekursiv alle Verzeichnisse im Argument Systemablagen zu suchen. Das Auslassen dieses Flag führt zu einer top-Niveau reine Suche von Verzeichnissen.|Optional|  
|/isNative|Legen Sie dieses Flag an, wenn das Assemblyargument einen Pfad für eine systemeigene Assembly ist. Lassen Sie dieses Flag aus, wenn das Assemblyargument den Namen einer verwalteten Assembly ist. (Siehe Abschnitt "Hinweise" Weitere Informationen über dieses Flag).|Optional|  
|/newGuids|Dieses Flag weist das Tool zum Erstellen eines neuen Werts für die Bilder GUID Symbol anstelle von vorhandenen Manifest zusammenführen.|Optional|  
|/newIds|Wenn dieses Flag weist das Tool zum Erstellen der neuen ID Symbolwerte für jedes Bild anstelle von Werten aus dem vorhandenen Manifest zusammenführen.|Optional|  
|/noLogo|Dieses Flag hält Produkt- und Copyright-Informationen drucken.|Optional|  
|/?|Drucken Sie Hilfeinformationen.|Optional|  
|/help|Drucken Sie Hilfeinformationen.|Optional|  
  
 **Beispiele**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Hinweise  
  
-   Das Tool unterstützt nur PNG und XAML-Dateien. Alle anderen Bild oder Dateitypen werden ignoriert. Für alle nicht unterstützten Typen, die bei der Analyse der Ressourcen wird eine Warnung generiert. Sofern unterstützt keine Bilder befinden Abschluss das Tool analysiert die Ressourcen an, wird ein Fehler generiert  
  
-   Anhand der vorgeschlagenen Format PNG-Bilder wird das Tool der Größe/Dimensionen bestehenden Wert für die PNG der Datenbankgröße Format angegeben festgelegt, auch wenn sie über die tatsächliche Größe des Bilds unterscheidet.  
  
-   Das Format der Breite/Höhe kann für PNG-Bilder ausgelassen werden, jedoch das Tool Lesen des Bilds tatsächliche Breite/Höhe und die für das Bild Größe/Dimensionen bestehenden Wert verwenden.  
  
-   Ausführen dieses Tools auf den gleichen Bildstreifen mehrfach für dieselbe .imagemanifest führt manifest Doppeleinträge, da das Tool versucht, die Image-Menüleiste in eigenständige Bilder aufzuteilen, und fügen Sie diese dem vorhandenen Manifest hinzu.  
  
-   Zusammenführen von (durch das weglassen /newGuids bzw. /newIds) sollte nur für Manifeste toolgenerierte vorgenommen werden. Manifeste, die angepasst oder über andere Mittel generiert wurden möglicherweise nicht ordnungsgemäß zusammengeführt werden.  
  
-   Manifeste, die für die systemeigenen Assemblys generiert werden, müssen möglicherweise manuell bearbeitet werden, nach der Generierung, stellen die ID-Symbole, die die Ressourcen-IDs aus der systemeigenen Assembly RC-Datei übereinstimmen.  
  
## <a name="sample-output"></a>Beispielausgabe  
 **Einfache bildmanifest**  
  
 Ein bildmanifest wird in dieser XML-Datei ähnlich sein:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImage" Value="0" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">  
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />  
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```  
  
 **Bildmanifest für ein Bild Bereichsstreifen**  
  
 Ein bildmanifest für ein Bild Bereichsstreifen werden dieser XML-Datei ähnelt:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImageStrip_0" Value="1" />  
    <ID Name="MyImageStrip_1" Value="2" />  
    <ID Name="MyImageStrip" Value="3" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">  
      <Source Uri="$(Resources)/MyImageStrip_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">  
      <Source Uri="$(Resources)/MyImageStrip_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists>  
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />  
    </ImageList>  
  </ImageLists>  
</ImageManifest>  
```  
  
 **Bildmanifest für systemeigene Images Assemblyressourcen**  
  
 Ein bildmanifest für systemeigene Abbilder wird in dieser XML-Datei ähnlich sein:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15198 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />  
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />  
    <ID Name="MyImage1" Value="0" />  
    <ID Name="MyImage2" Value="1" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage1)" Type="PNG" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage2)" Type="PNG" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```