---
title: Manifest aus Ressourcen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 286ec5b71691777af601c00e26c2db5772bd5f1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993974"
---
# <a name="manifest-from-resources"></a>Manifest aus Ressourcen
Das Manifest aus Ressourcen Tool ist eine Konsolenanwendung, die akzeptiert eine Liste von Bildressourcen (PNG oder XAML-Dateien) und generiert eine .imagemanifest-Datei, die diese Images mit dem Visual Studio-Image-Dienst verwendet werden kann. Darüber hinaus kann dieses Tool verwendet werden, eine vorhandene .imagemanifest Bilder hinzugefügt. Dieses Tool eignet sich für das Hinzufügen von hohen dpi- und Design-Unterstützung für Bilder für Visual Studio-Erweiterung. Die generierte .imagemanifest-Datei sollte in enthalten und als Teil der Visual Studio-Erweiterung (VSIX) bereitgestellt werden.  
  
## <a name="how-to-use-the-tool"></a>Gewusst wie: Verwenden Sie das tool  
 **Syntax**  
  
 ManifestFromResources Systemablagen:\<Dir1 >;\< Img1 >/Assembly:\<AssemblyName > \<optionale Argumente >  
  
 **Argumente**  
  
||||  
|-|-|-|  
|**SwitchName**|**Notizen**|**Erforderlich oder Optional**|  
|Systemablagen|Eine durch Semikolons getrennte Liste von Bildern oder Verzeichnisse. Diese Liste sollte immer die vollständige Liste der Bilder enthalten, die im Manifest werden. Wenn nur eine unvollständige Liste angegeben ist, werden die Einträge nicht enthalten gelöscht.<br /><br /> Wenn eine bestimmte Ressource-Datei einen Bildstreifen handelt, teilt das Tool es in einzelne Bilder vor dem Hinzufügen jedes Teilbild im Manifest.<br /><br /> Wenn das Bild eine PNG-Datei ist, wird empfohlen, dass Sie den Namen wie folgt formatieren, sodass das Tool in den richtigen Attributen für das Bild gefüllt werden kann: \<Name>.\<Width>.\<Height>.png.|Erforderlich|  
|/assembly|Der Name, der die verwaltete Assembly (nicht einschließlich Erweiterung), oder der Common Language Runtime-Pfad, der systemeigenen Assembly, auf dem die Ressourcen (relativ zum Speicherort des Manifests Common Language Runtime) gehostet werden soll.|Erforderlich|  
|/manifest|Der Name der generierten .imagemanifest-Datei zugewiesen. Dies kann auch einen absoluten oder relativen Pfad zum Erstellen der Datei an einem anderen Speicherort enthalten. Der Standardname entspricht der Name der Assembly.<br /><br /> Standardeinstellung: \<Aktuelles Verzeichnis >\\< Assembly\>.imagemanifest|Optional|  
|/guidName|Der Name, auf das Symbol "GUID" für alle Images im generierten Manifest zu gewähren.<br /><br /> Standardeinstellung: AssetsGuid|Optional|  
|/rootPath|Der Stammpfad, der vor dem Erstellen von verwalteten Ressourcen-URIs entfernt werden muss. (Dieses Flag ist in Fällen helfen, in dem das Tool den relativen URI-Pfad falsch sein, sodass Ressourcen, die Fehler beim Laden der ruft.)<br /><br /> Standardeinstellung: \<Aktuelles Verzeichnis >|Optional|  
|/recursive|Wenn Sie dieses Flag weist das Tool rekursiv durchsucht Verzeichnisse im Systemablagen-Argument. Das Auslassen dieses Flags führt zu einer top-Ebenen nur Suche von Verzeichnissen.|Optional|  
|/isNative|Legen Sie dieses Flag an, wenn das Assemblyargument einen Pfad für eine native Assembly ist. Lassen Sie dieses Flag an, wenn das Assemblyargument den Namen einer verwalteten Assembly ist. (Siehe Abschnitt "Hinweise" Weitere Informationen über dieses Flag).|Optional|  
|/newGuids|Wenn Sie dieses Flag weist das Tool zum Erstellen eines neuen Werts für Bilder GUID-Symbol anstelle der Definition aus der vorhandenen Manifest zusammenführen.|Optional|  
|/newIds|Wenn Sie dieses Flag weist das Tool zum Erstellen der neuen ID-Symbolwerte für jedes Bild anstelle von Werten aus dem vorhandenen Manifest zusammenführen.|Optional|  
|/noLogo|Dieses Flag wird beendet, Produkt und das Copyright-Informationen aus drucken.|Optional|  
|/?|Ausgeben von Hilfeinformationen.|Optional|  
|/help|Ausgeben von Hilfeinformationen.|Optional|  
  
 **Beispiele**  
  
-   ManifestFromResources /resources:D:\Images                       /assembly:My.Assembly.Name                       /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml                       /assembly:My.Assembly.Name                       /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Hinweise  
  
-   Das Tool unterstützt nur PNG und XAML-Dateien. Alle anderen Bild oder Dateitypen werden ignoriert. Für alle nicht unterstützten Typen aufgetreten beim Analysieren von Ressourcen wird eine Warnung generiert. Wenn keine unterstützte Images befinden sich Wenn das Tool abgeschlossen ist analysieren die Ressourcen, wird ein Fehler generiert werden  
  
-   Befolgen Sie die vorgeschlagene Format für PNG-Bilder, wird das Tool der Größe/Dimensionen bestehenden Wert für die PNG-Format angegebene Größe des, festgelegt, auch wenn es die tatsächliche Größe des Bilds unterscheidet.  
  
-   Das Format der Breite/Höhe kann für PNG-Bilder weggelassen werden, aber das Tool des Bilds tatsächliche Breite und Höhe zu lesen und verwenden Sie diese für die Größe/Dimensionen bestehenden Wert des Bilds.  
  
-   Ausführen dieses Tools auf den gleichen Bildstreifen mehrmals für den gleichen .imagemanifest führt zu doppelten manifesteinträge, daran, dass das Tool versucht, teilen den Bildstreifen in separate Abbildungen und tragen Sie in der vorhandenen Manifest.  
  
-   Zusammenführen (durch das weglassen /newGuids bzw. /newIds) sollte nur für die Tool-generierte Manifeste durchgeführt werden. Manifeste, die angepasst oder auf andere Weise generiert wurden möglicherweise nicht richtig gemergt werden.  
  
-   Manifeste, die für die systemeigenen Assemblys generiert werden müssen möglicherweise manuell bearbeitet werden, nach der Generierung, stellen die ID-Symbole, die die Ressourcen-IDs aus der nativen Assembly RC-Datei übereinstimmen werden.  
  
## <a name="sample-output"></a>Beispielausgabe  
 **Einfache bildmanifest**  
  
 Einem bildmanifest werden dieser XML-Datei ähnelt:  
  
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
  
 **Bildmanifest für einen Bildstreifen**  
  
 Einem bildmanifest für einen Bildstreifen werden dieser XML-Datei ähnelt:  
  
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
  
 **Bildmanifest für systemeigene Assembly Bildressourcen**  
  
 Einem bildmanifest für systemeigene Images werden dieser XML-Datei ähnelt:  
  
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