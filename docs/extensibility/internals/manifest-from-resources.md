---
title: Manifest aus Ressourcen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707277"
---
# <a name="manifest-from-resources"></a>Manifest aus Ressourcen
Das Tool Manifest aus Ressourcen ist eine Konsolenanwendung, die eine Liste von Bildressourcen (.png- oder .xaml-Dateien) aufnimmt und eine .imagemanifest-Datei generiert, mit der diese Bilder mit dem Visual Studio Image Service verwendet werden können. Darüber hinaus kann dieses Tool verwendet werden, um Bilder zu einem vorhandenen .imagemanifest hinzuzufügen. Dieses Tool ist nützlich, um einer Visual Studio-Erweiterung Unterstützung für Bilder hinzuzufügen und Sie zu thematisieren. Die generierte .imagemanifest-Datei sollte in eine Visual Studio-Erweiterung (.vsix) aufgenommen und bereitgestellt werden.

## <a name="how-to-use-the-tool"></a>Verwendung des Tools
 **Syntax**

 ManifestFromResources /resources:\<Dir1>; \<Img1> /assembly:\< \<AssemblyName> Optionalargs>

 **Argumente**

||||
|-|-|-|
|**Switch-Name**|**Hinweise**|**Erforderlich oder Optional**|
|/Ressourcen|Eine durch Semikolons getrennte Liste von Bildern oder Verzeichnissen. Diese Liste sollte immer die vollständige Liste der Bilder enthalten, die sich im Manifest befinden. Wenn nur eine Teilliste angegeben wird, gehen die nicht enthaltenen Einträge verloren.<br /><br /> Wenn es sich bei einer bestimmten Ressourcendatei um einen Bildstreifen handelt, teilt das Tool sie in separate Bilder auf, bevor jedes Unterbild zum Manifest hinzugefügt wird.<br /><br /> Wenn es sich bei dem Bild um eine PNG-Datei handelt, empfehlen wir Ihnen, den \<Namen so zu formatieren, dass das Tool die richtigen Attribute für das Bild ausfüllen kann: Name>. \<Breite>. \<Höhe>.png.|Erforderlich|
|/Assembly|Der Name der verwalteten Assembly (ohne die Erweiterung) oder der Laufzeitpfad der systemeigenen Assembly, die die Ressourcen hostet (relativ zum Laufzeitort des Manifests).|Erforderlich|
|/manifest|Der Name, der der generierten .imagemanifest-Datei zugeben soll. Dies kann auch einen absoluten oder relativen Pfad enthalten, um die Datei an einem anderen Speicherort zu erstellen. Der Standardname stimmt mit dem Assemblynamen überein.<br /><br /> Standard: \<Aktuelles \\ Verzeichnis\>><Assembly .imagemanifest|Optional|
|/guidName|Der Name, der dem GUID-Symbol für alle Bilder im generierten Manifest zugeben soll.<br /><br /> Standard: AssetsGuid|Optional|
|/rootPath|Der Stammpfad, der vor dem Erstellen von URIs für verwaltete Ressourcen entfernt werden muss. (Dieses Flag soll bei Fällen helfen, in denen das Tool den relativen URI-Pfad falsch macht, wodurch Ressourcen nicht geladen werden können.)<br /><br /> Standard: \<Aktuelleverzeichnis->|Optional|
|/rekursiv|Durch Festlegen dieses Flags wird das Tool aufgefordert, alle Verzeichnisse im Argument /resources rekursiv zu durchsuchen. Wenn Sie dieses Flag auslassen, wird nur die oberste Ebene nach Verzeichnissen durchsucht.|Optional|
|/isNative|Legen Sie dieses Flag fest, wenn das Assemblyargument ein Pfad für eine systemeigene Assembly ist. Lassen Sie dieses Flag weg, wenn das Assemblyargument der Name einer verwalteten Assembly ist. (Weitere Informationen zu diesem Flag finden Sie im Abschnitt Hinweise.)|Optional|
|/newGuids|Durch Festlegen dieses Flags wird das Tool aufgefordert, einen neuen Wert für das GUID-Symbol der Bilder zu erstellen, anstatt den Wert aus dem vorhandenen Manifest zusammenzuführen.|Optional|
|/newIds|Durch Festlegen dieses Flags wird das Tool aufgefordert, neue ID-Symbolwerte für jedes Bild zu erstellen, anstatt Werte aus dem vorhandenen Manifest zu verschmelzen.|Optional|
|/noLogo|Durch das Setzen dieses Flags werden Produkt- und Copyrightinformationen nicht mehr gedruckt.|Optional|
|/?|Drucken Sie Hilfeinformationen aus.|Optional|
|/help|Drucken Sie Hilfeinformationen aus.|Optional|

 **Beispiele**

- ManifestFromResources /resources:D:'Images /assembly:My.Assembly.Name /isNative

- ManifestFromResources /resources:D:'Images'Image1.png;D:'Images'Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest

- ManifestFromResources /resources:D:'Images'Image1.png;D:'Images'Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Notizen

- Das Tool unterstützt nur .png- und .xaml-Dateien. Alle anderen Bild- oder Dateitypen werden ignoriert. Für alle nicht unterstützten Typen, die beim Analysieren der Ressourcen auftreten, wird eine Warnung generiert. Wenn keine unterstützten Bilder gefunden werden, wenn das Tool mit der Analyse der Ressourcen fertig ist, wird ein Fehler generiert.

- Wenn Sie dem vorgeschlagenen Format für PNG-Bilder folgen, legt das Werkzeug den Größen-/Dimensionswert für die .png auf die formatspezifische Größe fest, auch wenn er sich von der tatsächlichen Größe des Bildes unterscheidet.

- Das Breite/Höhe-Format kann für PNG-Bilder weggelassen werden, aber das Werkzeug liest die tatsächliche Breite/Höhe des Bildes und verwendet diese für den Größe/Dimensionswert des Bildes.

- Wenn Sie dieses Werkzeug mehrmals auf demselben Bildstreifen für dasselbe .imagemanifest ausführen, führt dies zu doppelten Manifesteinträgen, da das Werkzeug versucht, den Bildstreifen in eigenständige Bilder aufzuteilen und diese dem vorhandenen Manifest hinzuzufügen.

- Das Zusammenführen (auslassen von /newGuids oder /newIds) sollte nur für werkzeuggenerierte Manifeste erfolgen. Manifeste, die auf andere Weise angepasst oder generiert wurden, werden möglicherweise nicht korrekt zusammengeführt.

- Manifeste, die für systemeigene Assemblys generiert werden, müssen möglicherweise nach der Generierung von Hand bearbeitet werden, damit die ID-Symbole mit den Ressourcen-IDs aus der .rc-Datei der systemeigenen Assembly übereinstimmen.

## <a name="sample-output"></a>Beispielausgabe
 **Einfaches Bildmanifest**

 Ein Bildmanifest ähnelt dieser XML-Datei:

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

 Ein Bildmanifest für einen Image-Strip ähnelt dieser XML-Datei:

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

 **Bildmanifest für systemeigene Assembly-Imageressourcen**

 Ein Bildmanifest für systemeigene Images ähnelt dieser XML-Datei:

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
