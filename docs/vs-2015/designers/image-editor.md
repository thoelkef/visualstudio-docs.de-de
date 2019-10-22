---
title: Bild-Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
ms.assetid: fc71d502-c548-4863-8afc-12a1d3ec90d4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c30e6f1be9daf07f3685c06b21ed9d507b86a07
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664388"
---
# <a name="image-editor"></a>Bildbearbeitung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird beschrieben, wie Sie den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Bild-Editor verwenden, um Textur- und Bildressourcen anzuzeigen und zu ändern.

 Sie können in der Bildbearbeitung mit den umfassenden Textur- und Bildformaten arbeiten, die in der Entwicklung von DirectX-Apps verwendet werden. Hierzu gehört die Unterstützung gängiger Bilddateiformate und Farbcodierungen, von Funktionen wie Alphakanäle und MIP-Zuordnung sowie von vielen der hochkomprimierten, hardwarebeschleunigten Texturformate, die DirectX unterstützt.

## <a name="supported-formats"></a>Unterstützte Formate
 Folgende Bildformate werden von der Bildbearbeitung unterstützt:

|Formatname|Dateinamenerweiterung|
|-----------------|-------------------------|
|Portable Network Graphics|.png|
|JPEG|.jpg, .jpeg, .jpe, .jfif|
|Direct Draw Surface|.dds|
|Graphics Interchange Format|GIF|
|Bitmap|.bmp, .dib|
|Tagged Image File Format|.tif, .tiff|
|TGA (Targa)|.tga|

## <a name="getting-started"></a>Erste Schritte
 In diesem Abschnitt wird beschrieben, wie Sie Ihrem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt ein Bild hinzufügen und dieses Ihren Anforderungen gemäß konfigurieren.

#### <a name="to-add-an-image-to-your-project"></a>So fügen Sie Ihrem Projekt ein Bild hinzu

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü des Projekts, zu dem Sie das Image hinzufügen möchten, und klicken Sie dann auf **Hinzufügen** und **Neues Element**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **Installiert** die Option **Grafiken** und anschließend ein entsprechendes Dateiformat für das Bild aus. Informationen zur Auswahl eines Dateiformats, das Ihren Anforderungen entspricht, finden Sie im nachfolgenden Abschnitt.

3. Legen Sie den **Namen** der Bilddatei und den **Speicherort** fest, an dem diese erstellt werden soll.

4. Wählen Sie die Schaltfläche **Hinzufügen** aus.

### <a name="choosing-the-image-format"></a>Auswählen des Bildformats
 Abhängig von der geplanten Verwendung des Bilds sind bestimmte Dateiformate möglicherweise besser geeignet als andere. Möglicherweise unterstützen manche Formate eine benötigte Funktion nicht – wie Transparenz oder ein bestimmtes Farbformat – oder für die geplanten Bildinhalte kann keine geeignete Komprimierung bereitgestellt werden.

 Die folgenden Informationen können Ihnen bei der Auswahl eines Bildformats helfen, das Ihre Anforderungen erfüllt.

 **Bitmap-Bild (BMP):** Das Bitmap-Bildformat. Ein nicht komprimiertes Bildformat, das 24-Bit-Farbe unterstützt. Das Bitmapformat unterstützt keine Transparenz.

 **GIF-Bild (GIF):** Das GIF-Bildformat (Graphics Interchange Format). Ein LZW-komprimiertes, verlustfreies Bildformat, das bis zu 256 Farben unterstützt. Ungeeignet für Fotografien und Bilder mit hohen Farbendetails. Es verfügt jedoch über gute Komprimierungsverhältnisse für Bilder mit wenig Farbe aber einem hohen Grad an Farbenkohärenz.

 **JPG-Bild (JPG):** Das JPEG-Bildformat (Joint Photographic Experts Group). Ein hochkomprimiertes, verlustbehaftetes Bildformat, das 24-Bit-Farbe unterstützt und für allgemeine Zwecke zur Komprimierung von Bildern mit hoher Farbenkohärenz geeignet ist.

 **PNG-Bild (PNG):** Das PNG-Bildformat (Portable Network Graphics). Ein mittelmäßig stark komprimiertes, verlustfreies Bildformat, das 24-Bit-Farben- und -Alphatransparenz unterstützt. Es ist sowohl für natürliche als auch künstliche Bilder geeignet. Die Komprimierungsverhältnisse sind jedoch nicht so gut wie bei verlustbehafteten Formaten, wie JPG oder GIF.

 **TIFF-Bild (TIF):** Das TIFF- oder TIF-Bildformat (Tagged Image File Format). Ein flexibles Bildformat, das mehrere Komprimierungsschemas unterstützt.

 **DDS-Textur (DDS):** Das DDS-Texturformat (DirectDraw Surface). Ein stark komprimiertes, verlustbehaftetes Texturformat, das 24-Bit-Farben und Alphatransparenz unterstützt. Die Komprimierungsverhältnisse können bis zu 8:1 betragen. Es basiert auf dem Texturkomprimierungssystem "S3 Texture Compression", das mithilfe von Grafikhardware dekomprimiert werden kann.

 **TGA-Bild (TGA):** Das TGA-Bildformat (Truevision Graphics Adapter, auch unter der Bezeichnung „Targa“ bekannt). Ein RLE-komprimiertes, verlustfreies Bildformat, das sowohl farbzugeordnete (Farbpalette) oder Direct Color-Bilder bis zu 24-Bit-Farben und Alphatransparenz unterstützt. Unpassend für Fotografien und Bilder mit hohem Farbendetails. Es stellt verfügt jedoch über gute Komprimierungsverhältnisse für Bilder mit weitflächigen identischen Farben.

### <a name="configuring-the-image"></a>Konfigurieren des Bilds
 Bevor Sie mit dem soeben erstellten Bild zu arbeiten beginnen, können Sie seine Standardkonfiguration ändern. Beispielsweise können Sie seine Abmessungen oder das verwendete Farbformat ändern. Weitere Informationen zur Konfiguration dieser und anderer Bildeigenschaften finden Sie unter [Bildeigenschaften](#ImageProperties).

> [!NOTE]
> Bevor Sie Ihre Arbeit speichern, legen Sie die Eigenschaft **Farbformat** fest, wenn Sie ein bestimmtes Farbformat verwenden möchten. Sie können die Komprimierungseinstellungen anpassen, wenn Sie die Datei zum ersten Mal speichern oder **Speichern unter** auswählen, sofern das Dateiformat die Komprimierung unterstützt.

## <a name="working-with-the-image-editor"></a>Arbeiten mit der Bildbearbeitung
 In diesem Abschnitt wird beschrieben, wie Sie mit dem Bild-Editor Texturen und Bilder erstellen und ändern.

### <a name="image-editor-toolbars"></a>Symbolleisten der Bildbearbeitung
 Die Symbolleisten der Bildbearbeitung enthalten Befehle, die Sie bei der Bearbeitung von Bildern unterstützen.

 Auf der Symbolleiste für den **Bild-Editor-Modus** finden Sie Befehle, die Auswirkungen auf den Zustand des Bild-Editors haben, sowie erweiterte Befehle. Die Symbolleiste befindet sich am oberen Rand der Entwurfsoberfläche des Bild-Editors. Die Zeichentools befinden sich auf der Symbolleiste des **Bild-Editors** am linken Rand der Entwurfsoberfläche.

 Dies ist die Symbolleiste des **Bildbearbeitungsmodus**:

 ![Die modale Symbolleiste des Bild-Editors.](../designers/media/digit-tre-modal-toolbar.png "Digit-Tre-Modal-Toolbar")

 In dieser Tabelle werden die Elemente der Symbolleiste des **Bildbearbeitungsmodus** beschrieben und in der Reihenfolge aufgelistet, in der sie auf der Symbolleiste von links nach rechts angezeigt werden.

|Element der Symbolleiste|Beschreibung|
|------------------|-----------------|
|**Auswählen**|Ermöglicht die Auswahl eines rechteckigen Bereichs eines Bilds. Nachdem Sie einen Bereich ausgewählt haben, können Sie ihn ausschneiden, kopieren, verschieben, skalieren, drehen, spiegeln oder löschen. Wenn eine aktive Auswahl vorhanden ist, haben die Zeichenwerkzeuge nur Auswirkungen auf den ausgewählten Bereich.|
|**Unregelmäßige Auswahl**|Ermöglicht die Auswahl eines unregelmäßigen Bereichs eines Bilds. Nachdem Sie einen Bereich ausgewählt haben, können Sie ihn ausschneiden, kopieren, verschieben, skalieren, drehen, spiegeln oder löschen. Wenn eine aktive Auswahl vorhanden ist, haben die Zeichenwerkzeuge nur Auswirkungen auf den ausgewählten Bereich.|
|**Stabsauswahl**|Ermöglicht die Auswahl eines ähnlich farbigen Bereichs eines Bilds. Die *Toleranz*, d.h. der maximale Unterschied zwischen benachbarten Farben, innerhalb dessen sie als ähnlich betrachtet werden, lässt sich so konfigurieren, dass ein kleinerer oder größerer Bereich von ähnlichen Farben berücksichtigt werden kann. Nachdem Sie einen Bereich ausgewählt haben, können Sie ihn ausschneiden, kopieren, verschieben, skalieren, drehen, spiegeln oder löschen. Wenn eine aktive Auswahl vorhanden ist, haben die Zeichenwerkzeuge nur Auswirkungen auf den ausgewählten Bereich.|
|**Schwenken**|Ermöglicht das Verschieben des Bilds relativ zum Fensterrahmen. Wählen Sie im **Schwenken**-Modus einen Punkt auf dem Bild aus, und bewegen Sie ihn.<br /><br /> Sie können den **Schwenken**-Modus vorübergehend aktivieren, indem Sie die STRG-Taste gedrückt halten.|
|**Zoom**|Ermöglicht das Anzeigen von mehr oder weniger Bilddetails relativ zum Fensterrahmen. Wählen Sie im **Zoom**-Modus einen Punkt auf dem Bild aus, und verschieben Sie ihn: zum Vergrößern nach rechts oder nach unten und zum Verkleinern nach links oder nach oben.<br /><br /> Sie können ihn vergrößern oder verkleinern, indem Sie die STRG-TASTE gedrückt halten, während Sie entweder das Mausrad verwenden oder das Pluszeichen (+) oder Minuszeichen (-) drücken.|
|**Originalgröße anzeigen**|Zeigt das Bild in einem 1:1-Verhältnis zwischen Pixel des Bilds und Pixel des Bildschirms.|
|**Mit Zoom anpassen**|Zeigt das ganze Bild im Fensterrahmen an.|
|**Auf Breite vergrößern**|Zeigt die gesamte Breite des Bilds im Fensterrahmen an.|
|**Raster**|Aktiviert oder deaktiviert das Raster, das die Pixelgrenzen anzeigt. Das Raster wird möglicherweise erst angezeigt, wenn Sie das Bild vergrößern.|
|**Nächste MIP-Ebene anzeigen**|Aktiviert die nächsthöhere MIP-Ebene in einer MIP-Zuordnungskette. Die aktive MIP-Ebene wird auf der Entwurfsoberfläche angezeigt. Dieses Element ist nur für Texturen mit MIP-Ebenen verfügbar.|
|**Vorherige MIP-Ebene anzeigen**|Aktiviert die nächstkleinere MIP-Ebene in einer MIP-Zuordnungskette. Die aktive MIP-Ebene wird auf der Entwurfsoberfläche angezeigt. Dieses Element ist nur für Texturen mit MIP-Ebenen verfügbar.|
|**Roter Kanal**<br /><br /> **Grüner Kanal**<br /><br /> **Blauer Kanal**<br /><br /> **Alphakanal**|Aktiviert oder deaktiviert den spezifischen Farbkanal. **Hinweis:** Durch systematisches Aktivieren oder Deaktivieren von Farbkanälen können Sie Probleme isolieren, die mit einem oder mehreren Farbkanälen zusammenhängen. Sie können beispielsweise eine falsche Alphatransparenz identifizieren.|
|**Hintergrund**|Aktiviert oder deaktiviert die Anzeige des Hintergrunds durch transparente Teile des Bilds. Sie können durch Auswahl einer der folgenden Optionen konfigurieren, wie der Hintergrund angezeigt wird:<br /><br /> **Schachbrett**<br /> Verwendet eine grüne Farbe zusammen mit der angegebenen Hintergrundfarbe, um den Hintergrund als Schachbrettmuster darzustellen. Sie können diese Option verwenden, um transparente Teile des Bilds sichtbarer zu machen.<br /><br /> Weißer Hintergrund<br /> Verwendet die Farbe Weiß, um den Hintergrund anzuzeigen.<br /><br /> Schwarzer Hintergrund<br /> Verwendet die Farbe Schwarz, um den Hintergrund anzuzeigen.<br /><br /> Hintergrund animieren<br /> Schwenkt das Schachbrettmuster langsam. Sie können diese Option verwenden, um transparente Teile des Bilds sichtbarer zu machen.|
|**Eigenschaften**|Öffnet bzw. schließt das Fenster **Eigenschaften**.|
|**Erweitert**|Enthält zusätzliche Befehle und Optionen.<br /><br /> **Filter**<br /><br /> Stellt einige allgemeine Bildfilter bereit: **Schwarz und weiß**, **Weichzeichner**, **Aufhellen**, **Abdunkeln**, **Kantenerkennung**, **Relief**, **Farben umkehren**, **Wellen**, **Sepia** und **Scharfzeichnen**.<br /><br /> **Grafik-Engines**<br /><br /> **Mit D3D11 rendern**<br /> Verwendet Direct3D 11 zum Rendern der Entwurfsoberfläche der Bildbearbeitung.<br /><br /> **Mit D3D11WARP rendern**<br /> Verwendet Direct3D 11 Windows Advanced Rasterization Platform (WARP) zum Rendern der Entwurfsoberfläche der Bildbearbeitung.<br /><br /> **Extras**<br /><br /> **Horizontal spiegeln**<br /> Vertauscht das Bild um seine horizontale bzw. X-Achse.<br /><br /> **Vertikal spiegeln**<br /> Vertauscht das Bild um seine vertikale bzw. Y-Achse.<br /><br /> **MIPS generieren**<br /> Generiert MIP-Ebenen für ein Bild. Wenn bereits MIP-Ebenen vorhanden sind, werden sie von der größten MIP-Ebene neu erstellt. Alle Änderungen, die an kleineren MIP-Ebenen vorgenommen wurden, gehen verloren. Um die MIP-Ebenen zu speichern, die Sie generiert haben, müssen Sie zum Speichern des Bilds das DDS-Format verwenden.<br /><br /> **Ansicht**<br /><br /> **Bildfrequenz**<br /> Bei aktivierter Option wird in der rechten oberen Ecke der Entwurfsoberfläche die Framerate angezeigt. Die Einzelbildrate ist die Anzahl von Bildern, die pro Sekunde gezeichnet werden. **Tipp:** Klicken Sie zum erneuten Ausführen des letzten Befehls auf die Schaltfläche **Erweitert**.|

 Dies ist die Symbolleiste des **Bild-Editors**.

 ![Symbolleiste der Bildbearbeitung](../designers/media/digit-tre-toolbar.png "Ziffer-Tre-Toolbar")

 In der folgenden Tabelle werden die Elemente der Symbolleiste des **Bild-Editors** beschrieben und in der Reihenfolge aufgelistet, in der sie auf der Symbolleiste von oben nach unten angezeigt werden.

|Element der Symbolleiste|Beschreibung|
|------------------|-----------------|
|**Zeichenstift**|Verwendet die aktive Farbauswahl, um einen Aliasstrich zu zeichnen. Sie können Farbe und Stärke des Strichs im Fenster **Eigenschaften** festlegen.|
|**Pinsel**|Verwendet die aktive Farbauswahl, um einen Strich mit Antialiasing zu zeichnen. Sie können Farbe und Stärke des Strichs im Fenster **Eigenschaften** festlegen.|
|**Airbrush**|Verwendet die aktive Farbauswahl, um einen Strich mit Antialiasing zu zeichnen, der in das Bild übergeht und im Laufe der Zeit mehr an Sättigung gewinnt. Sie können Farbe und Stärke des Strichs im Fenster **Eigenschaften** festlegen.|
|**Formatpipette**|Legt die aktive Farbauswahl für die Farbe des ausgewählten Pixels fest.|
|**Füllen**|Verwendet die aktive Farbauswahl, um einen Bereich des Bilds auszufüllen. Der betreffende Bereich wird als der Pixel definiert, auf den die Füllung angewendet wird, zusammen mit jedem Pixel, das mit ihm durch Pixel derselben Farbe verbunden ist und dieselbe Farbe aufweist. Wenn die Füllung innerhalb einer aktiven Auswahl angewendet wird, wird der betroffene Bereich von der Auswahl beschränkt.<br /><br /> Standardmäßig geht die aktive Farbauswahl in den betroffenen Bereich des Bilds entsprechend des Alphaanteils über. Um den betroffenen Bereich mit der aktiven Farbauswahl zu überschreiben, halten Sie die UMSCHALTTASTE gedrückt, während Sie das Füllwerkzeug verwenden.|
|**Radierer**|Legt Pixel auf eine vollständig transparente Farbe fest, wenn das Bild einen Alphakanal unterstützt. Andernfalls werden die Pixel auf die aktuelle Hintergrundfarbe festgelegt.|
|**Linie**, **Rechteck**, **Abgerundetes Rechteck**, **Ellipse**|Zeichnet eine Form auf dem Bild. Sie können Farbe und Stärke der Kontur im Fenster **Eigenschaften** festlegen.<br /><br /> Um ein Primitiv mit gleicher Breite und Höhe zu zeichnen, halten Sie die UMSCHALTTASTE beim Zeichnen gedrückt.|
|**Text**|Verwendet die Vordergrundfarben-Auswahl, um Text zu zeichnen. Die Hintergrundfarbe wird durch die Hintergrundfarben-Auswahl bestimmt. Für einen transparenten Hintergrund muss der Alphawert der Hintergrundfarben-Auswahl 0 sein. Wenn der Textbereich aktiv ist, können Sie festlegen, ob der Text mit einem Strich mit Antialiasing gezeichnet wird. Im Fenster **Eigenschaften** können Sie **Wert**, **Schriftart**, **Größe** und Stil (**Fett**, **Kursiv** oder **Unterstrichen**) für den Text festlegen. Der Inhalt und die Darstellung des Texts wird fertig gestellt, wenn der Textbereich nicht mehr aktiv ist.|
|**Drehen**|Dreht das Bild um 90 Grad im Uhrzeigersinn.|
|**Trim** (Kürzen)|Schneidet das Bild gemäß der aktuellen Auswahl ab.|

### <a name="working-with-mip-levels"></a>Arbeiten mit MIP-Ebenen
 Einige Bildformate, z. B. DirectDraw Surface (.dds), unterstützen MIP-Ebenen für die Detailebene Texturraum. Informationen zum Generieren von und Arbeiten mit MIP-Ebenen finden Sie unter [Vorgehensweise: Erstellen und Ändern von MIP-Ebenen](../designers/how-to-create-and-modify-mip-levels.md).

### <a name="working-with-transparency"></a>Arbeiten mit Transparenz
 Einige Bildformate, z. B. DirectDraw Surface (.dds), unterstützen Transparenz. Es gibt mehrere Möglichkeiten, mit Transparenz zu arbeiten. Dies hängt vom Werkzeug ab, das Sie verwenden. Legen Sie im Fenster **Eigenschaften** die Komponente **A** (Alpha) für die Farbauswahl fest, um die Ebene der Transparenz für eine Farbauswahl anzugeben. Im Folgenden wird gezeigt, wie die verschiedenen Werkzeuge die Anwendung von Transparenz steuern:

|Tool|Beschreibung|
|----------|-----------------|
|**Zeichenstift**, **Pinsel**, **Airbrush**, **Linie**, **Rechteck**, **Abgerundetes Rechteck**, **Ellipse**, **Text**|Erweitern Sie zum Verschmelzen der aktiven Farbauswahl mit dem Bild die Eigenschaftengruppe **Kanäle** im Fenster **Eigenschaften**, und aktivieren Sie das Kontrollkästchen **Zeichnen** des **Alphakanals**. Zeichnen Sie dann ganz normal.<br /><br /> Deaktivieren Sie das Kontrollkästchen **Zeichnen** des **Alphakanals**, und zeichnen Sie normal weiter, um mit der aktiven Farbauswahl zu zeichnen und den Alphawert des Bilds unverändert zu lassen.|
|**Füllen**|Um die aktive Farbauswahl mit dem Bild zu verschmelzen, wählen Sie einfach den Bereich aus, der gefüllt werden soll.<br /><br /> Um das Bild mit der aktiven Farbauswahl (einschließlich des Werts des Alphakanals) zu überschreiben, halten Sie die UMSCHALTTASTE gedrückt, und wählen Sie dann den zu füllenden Bereich aus.|

### <a name="ImageProperties"></a> Bildeigenschaften
 Über das Fenster **Eigenschaften** können Sie verschiedene Eigenschaften des Bilds festlegen. Beispielsweise können Sie die Breite und Höhe festlegen, um die Größe des Bilds zu ändern.

 In der folgenden Tabelle werden die Bildeigenschaften beschrieben.

|property|Beschreibung|
|--------------|-----------------|
|Breite|Die Breite des Bilds.|
|Höhe|Die Höhe des Bilds.|
|Bits pro Pixel|Die Anzahl der Bits, die jedes Pixel darstellen. Der Wert dieser Eigenschaft hängt vom **Farbformat** des Bilds ab.|
|Transparente Auswahl|**TRUE**, um die Auswahlebene mit dem Hauptbild basierend auf dem Alphawert der Auswahlebene zu verschmelzen; andernfalls **FALSE**. Dieses Element ist nur verfügbar für Bilder, die Alpha unterstützen.|
|Format|Das Farbformat des Bilds. Es können viele verschiedene Farbenformate abhängig vom Bildformat angegeben werden. Das Farbformat definiert die Anzahl und Art der Farbkanäle, die im Bild enthalten sind, und auch die Größe und die Codierung der verschiedenen Kanäle.|
|Mip-Ebene|Die aktive MIP-Ebene. Dieses Element ist nur für Texturen mit MIP-Ebenen verfügbar.|
|Anzahl der Mip-Ebenen|Die Gesamtanzahl der MIP-Ebenen im Bild. Dieses Element ist nur für Texturen mit MIP-Ebenen verfügbar.|
|Anzahl der Frames|Die Gesamtanzahl der Frames im Bild. Dieses Element ist nur für Bilder verfügbar, die Texturarrays unterstützen.|
|Frame|Der aktuelle Frame. Nur der erste Frame kann angezeigt werden, alle anderen Frames gehen beim Speichern des Bilds verloren.|
|Anzahl der Tiefensegmente|Die Gesamtanzahl der Tiefensegmente im Bild. Dieses Element ist nur für Bilder nur verfügbar, die Umfangstexturen unterstützen.|
|Tiefensegment|Das aktuelle Tiefensegment. Nur das erste Tiefensegment kann angezeigt werden, alle anderen Segmente gehen beim Speichern des Bilds verloren.|

> [!NOTE]
> Die Eigenschaft **Drehen um** kann auf alle Tools und ausgewählte Bereiche angewendet werden und wird daher immer zusammen mit anderen Tooleigenschaften am unteren Rand des Fensters **Eigenschaften** angezeigt. **Drehen um** wird immer angezeigt, da das gesamte Bild implizit ausgewählt ist, wenn keine andere Auswahl oder kein aktives Tool vorhanden ist. Weitere Informationen zur Eigenschaft **Drehen um** finden Sie unter [Tooleigenschaften](#ToolProperties).

#### <a name="resizing-images"></a>Ändern der Bildgröße
 Es gibt folgende zwei Möglichkeiten, die Größe eines Bilds zu ändern. In beiden Fällen verwendet die Bildbearbeitung eine bilineare Interpolation, um das Bild neu zu berechnen.

- Geben Sie im Fenster **Eigenschaften** die neuen Werte für die Eigenschaften **Breite** und **Höhe** an.

- Wählen Sie das gesamte Bild aus, und ändern Sie die Größe des Bilds mithilfe der Rahmenmarker.

### <a name="working-with-tools"></a>Arbeiten mit Werkzeugen

#### <a name="selected-regions"></a>Ausgewählte Bereiche
 Die Auswahl in der Bildbearbeitung legt die Bereiche des Bilds fest, die aktiv sind, das heißt, diese Bereiche sind durch Anwendung der Werkzeuge und Transformationen betroffen. Wenn eine aktive Auswahl vorhanden ist, werden Bereiche außerhalb des ausgewählten Bereichs von den meisten Tools und Transformationen nicht beeinflusst. Gibt es keine aktive Auswahl, ist das gesamte Bild aktiv.

 Die meisten Tools, wie z.B. **Zeichenstift**, **Pinsel**, **Airbrush**, **Füllen**, **Radierer** und 2D-Primitive sowie Transformationen, z.B. **Drehen**, **Trim** (Kürzen), **Farben umkehren**, **Horizontal spiegeln** und **Vertikal spiegeln**, werden durch die aktive Auswahl eingeschränkt oder definiert. Es gibt jedoch Tools, z.B. **Formatpipette** und **Text**, und Transformationen, z.B. **MIPS generieren**, die durch eine aktive Auswahl nicht betroffen sind. Diese Tools verhalten sich stets so, als ob das gesamte Bild die aktive Auswahl ist.

 Während Sie einen Bereich auswählen, können Sie die UMSCHALTTASTE gedrückt halten, um eine proportionale (quadratische) Auswahl zu treffen. Andernfalls wird die Auswahl nicht beschränkt.

##### <a name="resizing-selections"></a>Auswahlmöglichkeiten für die Größenänderung
 Nachdem Sie einen Bereich ausgewählt haben, können Sie dessen Größe oder die Größe des Bildinhalts ändern, indem Sie die Größe des Auswahlmarkers ändern. Beim Ändern der Größe des ausgewählten Bereichs können Sie die folgenden Zusatztasten verwenden, um das Verhalten des ausgewählten Bereichs zu ändern (drücken und halten Sie die Taste beim Ändern der Größe).

 STRG kopiert den Inhalt des ausgewählten Bereichs, bevor die Größe geändert wird. Belässt das Originalbild unverändert, während die Größe der Kopie geändert wird.

 Shift ändert die Größe des ausgewählten Bereichs proportional zur ursprünglichen Größe.

 Alt ändert die Größe des Auswahl Bereichs. Das Bild bleibt unverändert.

 Im Folgenden sind die gültigen Kombinationen der Zusatztasten aufgeführt:

|Ctrl|Shift|Alt|Beschreibung|
|----------|-----------|---------|-----------------|
||||Ändert die Größe des Inhalts des ausgewählten Bereichs.|
||Shift||Ändert proportional die Größe des Inhalts des ausgewählten Bereichs.|
|||Alt|Ändert die Größe des ausgewählten Bereichs. Dadurch wird ein neuer Auswahlbereich definiert.|
||Shift|Alt|Ändert die Größe des ausgewählten Bereichs proportional. Dadurch wird ein neuer Auswahlbereich definiert.|
|Ctrl|||Kopiert und ändert dann die Größe des Inhalts des ausgewählten Bereichs.|
|Ctrl|Shift||Kopiert und ändert dann die Größe des Inhalts des ausgewählten Bereichs proportional.|

#### <a name="ToolProperties"></a> Tooleigenschaften
 Wenn ein Tool ausgewählt ist, können Sie über das Fenster **Eigenschaften** angeben, wie es sich auf das Bild auswirken soll. Sie können z.B. die Breite des **Zeichenstift**-Tools oder die Farbe des **Pinsel**-Tools festlegen.

 Sie können eine Vordergrundfarbe und eine Hintergrundfarbe festlegen. Beide unterstützen einen Alphakanal, um benutzerdefinierte Deckkraft bereitzustellen. Die Einstellungen gelten für alle Werkzeuge. Wenn Sie eine Maus verwenden, entspricht die linke Maustaste der Vordergrundfarbe und die rechte Maustaste der Hintergrundfarbe.

 In der folgenden Tabelle werden die Tooleigenschaften beschrieben.

|Tool|Eigenschaften|
|----------|----------------|
|Alle Tools und Auswahlmöglichkeiten|**Drehen um**<br /> Definiert, um wie viel Grad die Auswahl oder der Tooleffekt im Uhrzeigersinn gedreht wird.|
|**Zeichenstift**, **Pinsel**, **Airbrush**, **Radierer**|**Stärke**<br /> Legt die Größe des Bereichs fest, der vom Werkzeug beeinflusst wird.|
|**Text**|**Antialiasing**<br /> Zeichnet Text, der über Ränder mit Antialiasing verfügt. Dadurch wird Text weicher dargestellt.<br /><br /> **Wert**<br /> Der zu zeichnende Text.<br /><br /> **Schriftart**<br /> Die Schriftart zum Zeichnen des Texts.<br /><br /> **Size**<br /> Die Größe des Texts.<br /><br /> **Fett**<br /> Formatiert die Schrift fett.<br /><br /> **Kursiv**<br /> Formatiert die Schrift kursiv.<br /><br /> **Unterstrichen**<br /> Formatiert die Schrift unterstrichen.|
|**2D-Primitiv**|**Antialiasing**<br /> Zeichnet Primitive, die über Ränder mit Antialiasing verfügen. Dadurch werden sie weicher dargestellt.<br /><br /> **Stärke**<br /> Legt die Stärke der Linie fest, die die Begrenzung des Primitivs bildet.<br /><br /> **Radius X**<br /> (Nur abgerundetes Rechteck) Legt den Rundungsradius für die oberen und unteren Kanten des Primitivs fest.<br /><br /> **Radius Y**<br /> (Nur abgerundetes Rechteck) Legt den Rundungsradius für die linken und rechten Kanten des Primitivs fest.|
|**Zeichenstift**, **Pinsel**, **Airbrush**, **2D-Primitiv**|**Kanäle**<br /> Aktiviert oder deaktiviert bestimmte Farbkanäle für die Anzeige und das Zeichnen. Wenn **Ansicht** für einen bestimmten Farbkanal festgelegt wird, ist dieser Kanal im Bild sichtbar, andernfalls ist er nicht sichtbar. Wenn **Zeichnen** für einen bestimmten Farbkanal festgelegt wird, ist dieser Kanal von Zeichenvorgängen betroffen, andernfalls nicht.|
|**Stabsauswahl**, **Füllen**|**Toleranz**<br /> Definiert den maximalen Unterschied zwischen benachbarten Farben, innerhalb dessen sie als ähnlich betrachtet werden, sodass weniger oder mehr ähnliche Farben einen Teil des betroffenen oder ausgewählten Bereichs ausmachen. Standardmäßig lautet der Wert 32. Das bedeutet, dass benachbarte Pixel in 32 Schatten (heller oder dunkler) der ursprünglichen Farbe als Teil des Bereichs betrachtet werden.|

## <a name="keyboard-shortcuts"></a>Tastenkombinationen

|Befehl|Tastenkombinationen|
|-------------|------------------------|
|In den Modus **Auswählen** wechseln|S|
|In den Modus **Zoom** wechseln|Z|
|In den Modus **Schwenken** wechseln|K|
|Alles auswählen|STRG + A|
|Die aktuelle Auswahl löschen|Löschen|
|Brechen Sie die aktuelle Auswahl ab.|Escape|
|Vergrößern|STRG+Mausrad vorwärts<br /><br /> STRG+BILD-AUF<br /><br /> Pluszeichen (+)|
|Verkleinern|STRG+Mausrad rückwärts<br /><br /> STRG+BILD-AB<br /><br /> Minuszeichen (-)|
|Bild nach oben schwenken|Mausrad rückwärts<br /><br /> BILD-AB|
|Bild nach unten schwenken|Mausrad vorwärts<br /><br /> BILD-AUF|
|Bild nach links schwenken|UMSCHALT+Mausrad rückwärts<br /><br /> Mausrad links<br /><br /> UMSCHALT+BILD-AB|
|Bild nach rechts schwenken|UMSCHALT+Mausrad vorwärts<br /><br /> Mausrad rechts<br /><br /> UMSCHALT+BILD-AUF|
|Originalgröße anzeigen|STRG+0 (null)|
|Bild an Fenster anpassen|STRG+G, STRG+F|
|Bildbreite an Fenster anpassen|STRG+G, STRG+I|
|Raster umschalten|STRG+G, STRG+G|
|Bild auf aktuelle Auswahl zuschneiden|STRG+G, STRG+C|
|Nächste MIP-Ebene (mehr Detail) anzeigen|STRG+G, STRG+6|
|Vorherige MIP-Ebene (weniger Detail) anzeigen|STRG+G, STRG+7|
|Roten Farbkanal ein-/ausschalten|STRG+G, STRG+1|
|Grünen Farbkanal ein-/ausschalten|STRG+G, STRG+2|
|Blauen Farbkanal ein-/ausschalten|STRG+G, STRG+3|
|Alphakanal (Transparenz) ein-/ausschalten|STRG+G, STRG+4|
|Alphaschachbrettmuster ein-/ausschalten|STRG+G, STRG+B|
|Zum unregelmäßigen Auswahlwerkzeug wechseln|L|
|Zum Stabsauswahlwerkzeug wechseln|M|
|Zum Stiftwerkzeug wechseln|P|
|Zum Pinselwerkzeug wechseln|B|
|Zum Füllwerkzeug wechseln|F|
|Zum Radiererwerkzeug wechseln|E|
|Zum nächsten Werkzeug wechseln|T|
|Zum Farbauswahlwerkzeug (Formatpipette) wechseln|I|
|Aktive Auswahl mit Inhalt verschieben.|Pfeiltasten.|
|Größe der aktiven Auswahl mit Inhalt ändern.|STRG+Pfeiltasten|
|Aktive Auswahl ohne Inhalt verschieben.|UMSCHALT+Pfeiltasten|
|Größe der aktiven Auswahl ohne Inhalt ändern.|UMSCHALT+STRG+Pfeiltasten|
|Aktuelle Ebene bestätigen|Return|
|Stärke des Werkzeugs verringern|[|
|Stärke des Werkzeugs erhöhen|]|

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Arbeiten mit 3D-Objekten für Spiele und Apps](../designers/working-with-3-d-assets-for-games-and-apps.md)|Bietet eine Übersicht über die Werkzeuge, die Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwenden können, um mit Grafikressourcen wie Texturen und Bildern, 3D-Modellen und Shadereffekten zu arbeiten.|
|[Modell-Editor](../designers/model-editor.md)|Beschreibt, wie der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modell-Editor für die Arbeit mit 3D-Modellen verwendet wird.|
|[Shader-Designer](../designers/shader-designer.md)|Beschreibt die Verwendung des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shader-Designers zur Arbeit mit Shadern.|
