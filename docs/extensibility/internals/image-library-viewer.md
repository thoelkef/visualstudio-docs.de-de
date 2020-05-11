---
title: Bildbibliothek Viewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707746"
---
# <a name="image-library-viewer"></a>Bildbibliotheks-Viewer
Das Visual Studio Image Library Viewer-Tool kann Bildmanifeste laden und durchsuchen, sodass der Benutzer sie auf die gleiche Weise bearbeiten kann wie Visual Studio. Der Benutzer kann Hintergrund, Größen, DPI, hohen Kontrast und andere Einstellungen ändern. Das Tool zeigt auch Ladeinformationen für jedes Bildmanifest und Quellinformationen für jedes Bild im Bildmanifest an. Dieses Tool ist nützlich für:

1. Fehlerdiagnose

2. Sicherstellen, dass Attribute in benutzerdefinierten Bildmanifesten richtig festgelegt werden

3. Suchen nach Bildern im Visual Studio-Bildkatalog, damit eine Visual Studio-Erweiterung Bilder verwenden kann, die dem Stil von Visual Studio entsprechen

   ![Bildbibliotheks-Viewer-Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Bildbibliotheks-Viewer-Hero")

   **Bildmoniker**

   Ein Bildmoniker (oder kurz Moniker) ist ein GUID:ID-Paar, das ein Bild- oder Bildlistenobjekt in der Bildbibliothek eindeutig identifiziert.

   **Bildmanifestdateien**

   Bildmanifestdateien (.imagemanifest) sind XML-Dateien, die eine Reihe von Bildassets definieren, die Moniker, die diese Assets darstellen, und das reale Bild oder die Bilder, die jedes Asset darstellen. Bildmanifeste können eigenständige Bilder oder Bildlisten für die Unterstützung der älteren Benutzeroberfläche definieren. Darüber hinaus gibt es Attribute, die entweder für die Anlage oder für die einzelnen Bilder hinter jedem Asset festgelegt werden können, um zu ändern, wann und wie diese Assets angezeigt werden.

   **Bildmanifestschema**

   Ein vollständiges Bildmanifest sieht wie folgt aus:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
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
|Importieren|Importiert die Symbole der angegebenen Manifestdatei zur Verwendung im aktuellen Manifest.|
|Guid|Das Symbol stellt eine GUID dar und muss mit der GUID-Formatierung übereinstimmen.|
|id|Das Symbol stellt eine ID dar und muss eine nicht negative ganze Zahl sein.|
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
|System|Der Ordner Windows-System32|
|WinDir|Der Wert der Umgebungsvariablen %WinDir%|

 **Image**

 Das \<Bild->-Element definiert ein Bild, auf das ein Moniker verweisen kann. Die GUID und die ID, die zusammen genommen werden, bilden den Bildmoniker. Der Moniker für das Bild muss in der gesamten Bildbibliothek eindeutig sein. Wenn mehr als ein Bild einen bestimmten Moniker hat, wird das erste Bild beim Erstellen der Bibliothek beibehalten.

 Sie muss mindestens eine Quelle enthalten. Obwohl größenneutrale Quellen die besten Ergebnisse in einer breiten Palette von Größen liefern, sind sie nicht erforderlich. Wenn der Dienst nach einem Abbild einer \<Größe gefragt wird, die nicht im Image->-Element definiert ist, und es keine größenneutrale Quelle gibt, wählt der Dienst die beste größenspezifische Quelle aus und skaliert sie auf die angeforderte Größe.

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
|Uri|[Erforderlich] Ein URI, der definiert, aus wo das Bild geladen werden kann. Folgende Werte sind möglich:<br /><br /> - Ein [Pack-URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf) mit der application:///-Berechtigung<br /><br /> - Eine absolute Komponentenressourcenreferenz<br /><br /> - Ein Pfad zu einer Datei, die eine systemeigene Ressource enthält|
|Hintergrund|[Optional] Gibt an, welche Quelle auf der Art des Hintergrunds verwendet werden soll.<br /><br /> Folgende Werte sind möglich:<br /><br /> - *Licht*: Die Quelle kann auf einem hellen Hintergrund verwendet werden.<br /><br /> - *Dunkel*: Die Quelle kann auf einem dunklen Hintergrund verwendet werden.<br /><br /> - *HighContrast*: Die Quelle kann auf jedem Hintergrund im Modus "Hoher Kontrast" verwendet werden.<br /><br /> - *HighContrastLight*: Die Quelle kann auf einem hellen Hintergrund im Modus "Hoher Kontrast" verwendet werden.<br /><br /> -*HighContrastDark*: Die Quelle kann auf einem dunklen Hintergrund im Modus "Hoher Kontrast" verwendet werden.<br /><br /> Wenn das **Background-Attribut** weggelassen wird, kann die Quelle auf jedem Hintergrund verwendet werden.<br /><br /> Wenn **Hintergrund** *Light*, *Dark*, *HighContrastLight*oder *HighContrastDark*ist, werden die Farben der Quelle nie invertiert. Wenn **Background** weggelassen oder auf *HighContrast*festgelegt ist, wird die Umkehrung der Farben der Quelle durch das **AllowColorInversion-Attribut** des Bildes gesteuert.|

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

## <a name="how-to-use-the-tool"></a>Verwendung des Tools
 **Überprüfen eines benutzerdefinierten Bildmanifests**

 Um ein benutzerdefiniertes Manifest zu erstellen, wird empfohlen, das ManifestFromResources-Tool zu verwenden, um das Manifest automatisch zu generieren. Um das benutzerdefinierte Manifest zu überprüfen, starten Sie den Bildbibliotheks-Viewer, und wählen Sie Datei > Pfade festlegen... , um das Dialogfeld Suchverzeichnisse zu öffnen. Das Tool verwendet die Suchverzeichnisse zum Laden von Bildmanifesten, aber es wird es auch verwenden, um die DLL-Dateien zu finden, die die Bilder in einem Manifest enthalten, also stellen Sie sicher, dass Sie sowohl die Manifest- als auch die DLL-Verzeichnisse in diesem Dialogfeld enthalten.

 ![Bildbibliotheks-Viewer-Suche](../../extensibility/internals/media/image-library-viewer-search.png "Bildbibliotheks-Viewer-Suche")

 Klicken Sie auf **Hinzufügen...,** um neue Suchverzeichnisse auszuwählen, um nach Manifesten und den entsprechenden DLLs zu suchen. Das Tool merkt sich diese Suchverzeichnisse, und sie können durch Überprüfen oder Deaktivieren eines Verzeichnisses aktiviert oder deaktiviert werden.

 Standardmäßig versucht das Tool, das Visual Studio-Installationsverzeichnis zu finden und diese Verzeichnisse der Suchverzeichnisseliste hinzuzufügen. Sie können manuell Verzeichnisse hinzufügen, die das Tool nicht findet.

 Sobald alle Manifeste geladen sind, kann das Tool verwendet werden, um **Hintergrundfarben,** **DPI,** **hohen Kontrast**oder **Grauskalierung** für die Bilder umzuschalten, sodass ein Benutzer Bildelemente visuell überprüfen kann, um sicherzustellen, dass sie für verschiedene Einstellungen korrekt gerendert werden.

 ![Bildbibliotheks-Viewer-Hintergrund](../../extensibility/internals/media/image-library-viewer-background.png "Bildbibliotheks-Viewer-Hintergrund")

 Die Hintergrundfarbe kann auf Hell, Dunkel oder einen benutzerdefinierten Wert festgelegt werden. Wenn Sie "Benutzerdefinierte Farbe" auswählen, wird ein Farbauswahldialogfeld geöffnet und diese benutzerdefinierte Farbe am unteren Rand des Hintergrundkombinationsfelds hinzugefügt, um später einfach zurückzurufen.

 ![Bildbibliotheks-Viewer, „Benutzerdefinierte Farbe“](../../extensibility/internals/media/image-library-viewer-custom-color.png "Bildbibliotheks-Viewer, „Benutzerdefinierte Farbe“")

 Wenn Sie einen Bildmoniker auswählen, werden die Informationen für jedes reale Bild hinter diesem Moniker im Bereich Bilddetails auf der rechten Seite angezeigt. Der Bereich ermöglicht es Benutzern auch, einen Moniker nach Namen oder nach unformatiertem GUID:ID-Wert zu kopieren.

 ![Bildbibliotheks-Viewer-Bilddetails](../../extensibility/internals/media/image-library-viewer-image-details.png "Bildbibliotheks-Viewer-Bilddetails")

 Die für jede Bildquelle angezeigten Informationen umfassen, auf welcher Art von Hintergrund sie angezeigt werden sollen, ob sie thematisiert werden kann oder Hohen Kontrast unterstützt, für welche Größen sie gültig ist oder ob sie größenneutral ist und ob das Bild von einer systemeigenen Assembly stammt.

 ![Bildbibliotheks-Viewer-Design „Dose“](../../extensibility/internals/media/image-library-viewer-can-theme.png "Bildbibliotheks-Viewer-Design „Dose“")

 Beim Überprüfen eines Bildmanifests wird empfohlen, dass Sie die Manifest- und Image-DLL an ihren realen Speicherorten bereitstellen. Dadurch wird überprüft, ob alle relativen Pfade ordnungsgemäß funktionieren und dass die Bildbibliothek das Manifest und die Image-DLL finden und laden kann.

 **Suchen nach Bildkatalog KnownMonikers**

 Um das Visual Studio-Styling besser zu entsprechen, kann eine Visual Studio-Erweiterung Bilder im Visual Studio-Bildkatalog verwenden, anstatt eigene zu erstellen und zu verwenden. Dies hat den Vorteil, dass diese Bilder nicht verwaltet werden müssen, und garantiert, dass das Bild über ein High-DPI-Backing-Image verfügt, sodass es in allen Von Visual Studio unterstützten DPI-Einstellungen korrekt aussehen sollte.

 Der Bildbibliotheks-Viewer ermöglicht die Suche nach einem Manifest, sodass ein Benutzer den Moniker finden kann, der ein Bildobjekt darstellt, und diesen Moniker im Code verwenden kann. Um nach Bildern zu suchen, geben Sie den gewünschten Suchbegriff in das Suchfeld ein und drücken Sie die Eingabetaste. Die Statusleiste unten zeigt an, wie viele Übereinstimmungen aus den Gesamtbildern in allen Manifesten gefunden wurden.

 ![Bildbibliotheks-Viewer-Filter](../../extensibility/internals/media/image-library-viewer-filter.png "Bildbibliotheks-Viewer-Filter")

 Bei der Suche nach Bildmonikern in vorhandenen Manifesten wird empfohlen, dass Sie nur die Moniker des Visual Studio-Bildkatalogs, andere absichtlich öffentlich zugängliche Moniker oder Ihre eigenen benutzerdefinierten Moniker suchen und verwenden. Wenn Sie nicht öffentliche Moniker verwenden, kann die benutzerdefinierte Benutzeroberfläche unterbrochen oder ihre Bilder auf unerwartete Weise geändert werden, wenn oder wenn diese nicht öffentlichen Moniker und Bilder geändert oder aktualisiert werden.

 Darüber hinaus ist die Suche nach GUID möglich. Diese Art der Suche ist nützlich, um die Liste auf ein einzelnes Manifest oder einen einzelnen Unterabschnitt eines Manifests zu filtern, wenn dieses Manifest mehrere GUIDs enthält.

 ![Bildbibliotheks-Viewer-Filter-GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Bildbibliotheks-Viewer-Filter-GUID")

 Schließlich ist auch die Suche nach ID möglich.

 ![Bildbibliotheks-Viewer-Filter-ID](../../extensibility/internals/media/image-library-viewer-filter-id.png "Bildbibliotheks-Viewer-Filter-ID")

## <a name="notes"></a>Notizen

- Standardmäßig ruft das Tool mehrere Bildmanifeste ein, die im Visual Studio-Installationsverzeichnis vorhanden sind. Das einzige, das öffentlich verbrauchsfähige Moniker hat, ist das **Microsoft.VisualStudio.ImageCatalog-Manifest.** GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (diese GUID **nicht** in einem benutzerdefinierten Manifest überschreiben) Typ: KnownMonikers

- Das Tool versucht beim Start, alle gefundenen Bildmanifeste zu laden, sodass es einige Sekunden dauern kann, bis die Anwendung tatsächlich angezeigt wird. Es kann auch langsam oder nicht reagieren, während das Laden der Manifeste.

## <a name="sample-output"></a>Beispielausgabe
 Dieses Tool generiert keine Ausgabe.
