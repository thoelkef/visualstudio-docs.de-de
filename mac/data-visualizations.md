---
title: 'Debuggen: Datenvisualisierungen'
description: Das Debuggen ist ein üblicher und notwendiger Teil des Programmierens. Visual Studio für Mac enthält eine Reihe von Features, die das Debuggen vereinfachen. Dieser Artikel behandelt die verschiedenen Datenvisualisierungen, die angezeigt werden können, wenn Objekte im Debugger überprüft werden.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 14696040160dfc33f89b7647fb73b116b41afa16
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691735"
---
# <a name="data-visualizations"></a>Datenvisualisierungen

Visual Studio für Mac beinhaltet eine UI-Unterstützung für den Debugger, durch die Visualisierungen der Werte einer Variable, eines Felds oder einer Eigenschaft während des Debuggens ermöglicht werden. Diese Daten-Schnellansichten zeigen eine erweiterte Version der Daten an und ermöglichen es Entwicklern, bekannte Strukturen zu überprüfen, zum Beispiel das Anzeigen der Farbe einer Color-Struktur.

Die Schnellansichten im Debugpad **Local** (Lokal) können angezeigt werden, indem Sie auf das Vorschausymbol klicken, das rechts des Werts angezeigt wird, wenn der Benutzer den Mauszeiger über die Reihe bewegt:

![Pad „Lokal“](media/data-visualizations-image9.png)

Die nachfolgende Liste behandelt viele der neuen Visualisierungen, die beim Debuggen in Visual Studio für Mac verfügbar sind.

## <a name="point"></a>Point
Ein Point, PointF oder CGPoint unter iOS und Mac wird als Tupel gerendert, der die X- und Y-Werte im Debugpad anzeigt:

![Punktvisualisierung](media/data-visualizations-image10.png)

## <a name="size"></a>Size
Eine Size, SizeF oder CGSize unter iOS und Mac wird als Rechteck gerendert. Dieses wird maßstabsgetreu gezeichnet, bis eine Dimension 250 px überschreitet. An diesem Punkt wird das Rechteck auf eine Größe von 250 px für die größte Dimension skaliert:

[Größenvisualisierung](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Rechteck
Ein Rectangle, RectangleF oder CGRect unter iOS und Mac zeigt die Dimensionen und den Ursprung an. Ähnlich wie bei der Größe wird es maßstabsgetreu gezeichnet, bis eine Dimension 250 px überschreitet:

![Rechteckvisualisierung](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Koordinaten
Die Koordinaten werden auf einer Karte eingezeichnet und der Standort wird an die Mitte angeheftet:

[Koordinatenvisualisierung](media/data-visualizations-image13.png)

## <a name="color"></a>Color
Hierdurch werden die Eigenschaften von UIColor, CGColor und Color angezeigt, wodurch die Farbvorschau, RGBA-Komponenten, die Werte für Farbton, Sättigung und Helligkeit und der Farbtonwert dargestellt werden:

![Farbvisualisierung](media/data-visualizations-image14.png)

## <a name="images"></a>Bilder

Medien werden bis zu einer maximalen Dimension von 250 px maßstabsgetreu gerendert. Wenn das Bild größer als 250 px ist, wird es passend skaliert:

![Bildvisualisierung](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Bezier-Kurven

Die Schnellansicht zeigt eine `NSBezierPath` an:

![Visualisierung der Bezier-Kurve](media/data-visualizations-image16.png)

## <a name="string"></a>String

Eine Zeichenfolge mit weniger als 100 Zeichen wird vollständig und ohne Vorschau angezeigt. Längere Zeichenfolgen werden in der Vorschau vollständig angezeigt. Zeichenfolgen sind bearbeitbar und die Schnellansicht verfügt über die Schaltfläche „Bearbeiten“, sodass der Zeichenfolgenwert wie unten dargestellt entweder in der Vorschau oder im Zeichenfolgenwert-Editor bearbeitet werden kann:

![Zeichenfolgenvisualisierung](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Kurze Zeichenfolgen:
![Visualisierung von kurzen Zeichenfolgen](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Mittellange Zeichenfolgen:
![Visualisierung von mittellangen Zeichenfolgen](media/data-visualizations-image19.png)

### <a name="editor"></a>Editor:

![Editorvisualisierung](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumberable zählt alle Werte auf und jeder Wert kann angezeigt werden, indem Sie auf die Schaltfläche zum **Anzeigen** der Werte klicken. Die Option „IEnumberable“ zeigt keine Werte für Objekte wie `Array`, `ArrayList`, `List<>`, und `Dictionary<,>`, da diese über ihre eigenen Debuggervisualisierungen verfügen.

![Visualisierung von IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Andere Schnellansichten

Einige andere Typen, die ebenfalls über ihre eigenen Inline-Schnellansichten verfügen, werden im Folgenden aufgelistet:

![Andere Visualisierung](media/data-visualizations-image23.png)

* **Primitive**
  * Dadurch wird der Rohwert des primitiven Typs angezeigt.
* **Enum**
  * Dadurch wird der Feldwert ohne den Qualifizierer des Enumerationstyps angezeigt.
* **Tuple**
  * Wird im Format „(,)“ angezeigt.
* **NULL**
  * Zeigt den Wert „NULL“ an.
* **URL**
  * Dadurch wird ein anklickbarer Link angezeigt.
* **IntPtr**
  * Dadurch wird eine hexadezimale Darstellung des IntPtr angezeigt.

## <a name="see-also"></a>Weitere Informationen

- [Untersuchen von Variablen in den Fenstern „Auto“ und „Lokal“ (Visual Studio unter Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Anzeigen von Zeichenfolgen in einer Schnellansicht (Visual Studio unter Windows)](/visualstudio/debugger/string-visualizer-dialog-box)