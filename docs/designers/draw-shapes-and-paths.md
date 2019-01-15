---
title: Zeichnen von Formen und Pfaden
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29cd9da26b632d8ed8b1d09b0803f27599dba95e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942644"
---
# <a name="draw-shapes-and-paths"></a>Zeichnen von Formen und Pfaden

In XAML-Designer ist eine *Form* genau das, was Sie erwarten. Beispielsweise ein Rechteck, ein Kreis oder eine Ellipse. Ein *Pfad* ist eine flexiblere Version einer Form. Sie können diese z. B. umformen oder miteinander kombinieren, um neue Formen zu kreieren.

Formen und Pfade verwenden Vektorgrafiken, sodass sie gut für Displays mit hoher Auflösung skaliert werden können. Weitere Informationen zu Vektorgrafiken finden Sie unter [Was sind Vektorgrafiken](https://www.youtube.com/watch?v=MoCSwF0n-io) oder unter [Vektorgrafiken](http://www.webopedia.com/TERM/V/vector_graphics.html).

##  <a name="Shape"></a> Zeichnen einer Form
 Formen finden Sie im Bereich **Objekte** .

 ![Formenkategorie im Objektbereich](../designers/media/b4_shapes_assetspanel.png)

 Ziehen Sie die gewünschte Form auf die Zeichenfläche. Anschließend können Sie die Handles an der Form verwenden, um die Form zu skalieren, zu drehen, zu verschieben oder zu neigen.

 ![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

##  <a name="Path"></a> Zeichnen eines Pfads
 Ein Pfad besteht aus einer Reihe von miteinander verbundenen Linien und Kurven. Verwenden Sie einen Pfad, um interessante Formen zu erstellen, die nicht im Bereich **Objekte** verfügbar sind.

 Sie können einen Pfad mit einer Linie, einem Stift oder einem Zeichenstift zeichnen. Diese Tools finden Sie im Bereich **Tools** .

 ![Stifttool](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png) ![Optionen des Stifttools](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png)

### <a name="draw-a-straight-line"></a>Zeichnen einer geraden Linie
 Verwenden Sie das **Stifttool** ![Stifttool](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) oder das **Linientool** ![Linientool](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png) verwenden.

 **Verwenden des Stifttools** ![Stifttool](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png)

 Klicken Sie einmal auf die Zeichenfläche, um den Anfangspunkt zu definieren, und klicken Sie dann erneut, um das Ende der Linie zu definieren.

 **Verwenden des Linientools** ![Linientool](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png)

 Ziehen Sie auf der Zeichenfläche vom gewünschten Anfangspunkt der Linie, und lassen Sie die Maustaste an dem Punkt los, an dem die Linie enden soll.

### <a name="draw-a-curve"></a>Zeichnen einer Kurve
 Verwenden Sie das **Stifttool** ![Stifttool](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Klicken Sie einmal auf die Zeichenfläche, um den Ausgangspunkt einer Linie zu definieren, und ziehen Sie dann bei gedrückter Maustaste den Mauszeiger, um die gewünschte Kurve zu erstellen.

 Wenn Sie den Pfad schließen möchten, klicken Sie auf den ersten Punkt der Linie.

### <a name="change-the-shape-of-a-curve"></a>Ändern der Form einer Kurve
 Verwenden Sie das **Direktauswahltool** ![Direktauswahltool](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Klicken Sie auf die Form, und ziehen Sie dann einen beliebigen Punkt der Form, um die Kurvenformen zu ändern.

### <a name="draw-a-free-form-path"></a>Zeichnen eines Freihandformpfads
 Verwenden Sie das **Bleistifttool** ![Bleistifttool](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png).

 Zeichnen Sie auf der Zeichenfläche einen Freihandformpfad genau so, als würden Sie einen echten Zeichenstift verwenden.

### <a name="remove-part-of-a-path"></a>Entfernen eines Pfadsegments
 Verwenden Sie das **Direktauswahltool** ![Direktauswahltool](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Wählen Sie den Pfad aus, der das Segment enthält, das Sie löschen möchten, und klicken Sie dann auf die Schaltfläche **Löschen** .

### <a name="remove-a-point-in-a-path"></a>Entfernen eines Punkts in einem Pfad
 Verwenden Sie das **Auswahltool** ![Auswahltool](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) und das **Stifttool** ![Stifttool](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Verwenden Sie das **Auswahltool** ![Auswahltool](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png), um den Pfad auszuwählen. Verwenden Sie dann das **Stifttool** ![Stifttool](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png), um auf den Punkt zu klicken, den Sie entfernen möchten.

### <a name="add-a-point-to-a-path"></a>Hinzufügen eines Punkts zu einem Pfad
 Verwenden Sie das **Auswahltool** ![Auswahltool](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) und das **Stifttool** ![Stifttool](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Verwenden Sie das **Auswahltool** ![Auswahltool](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png), um den Pfad auszuwählen. Verwenden Sie das **Stifttool** ![Stifttool](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png), um an eine beliebige Stelle auf dem Pfad zu klicken, an der Sie den Punkt hinzufügen möchten.

##  <a name="Convert"></a> Konvertieren von Formen in Pfade
 Um eine Form auf die gleiche Weise wie einen Pfad zu ändern, konvertieren Sie die Form in einen Pfad.

 **Sehen Sie sich ein kurzes Video an:** ![Installierte Features konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png) [Arbeiten mit Pfaden: Konvertieren von Formen in Pfade](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147)

##  <a name="Combine"></a> Kombinieren von Pfaden
 Sie können Pfade und Formen zu einem einzelnen Pfad kombinieren.

 ![Kombinieren von Pfaden](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|||||
|-|-|-|-|
|![Zwei Formen vor dem Vereinen](../designers/media/b1_1.png)|Zwei Formen vor dem Vereinen|![Überschneiden](../designers/media/b1_4.png)|Überschneiden|
|![Überlappung ausschließen](../designers/media/b1_2.png)|Vereinigen|![](../designers/media/b1_5.png)|Überlappung ausschließen|
|![Subtrahieren](../designers/media/b1_3.png)|Teilen|![](../designers/media/b1_6.png)|Subtrahieren|

 **Sehen Sie sich ein kurzes Video an:** ![Installierte Features konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png) [Arbeiten mit Pfaden: Kombinieren von Pfaden](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195)

##  <a name="Compound"></a> Erstellen eines zusammengesetzten Pfads
 Wenn Sie einen zusammengesetzten Pfad erstellen, werden sich überschneidende Pfadsegmente vom Ergebnis subtrahiert. Der resultierende Pfad übernimmt die visuellen Eigenschaften des untersten Pfads.

 Sie können einen zusammengesetzten Pfad nach der Erstellung jederzeit teilen.

 ![Teilen eines zusammengesetzten Pfads](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

 **Sehen Sie sich ein kurzes Video an:** ![Installierte Features konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png) [Arbeiten mit Pfaden: Erstellen eines zusammengesetzten Pfads](https://www.youtube.com/watch?v=Io5bC0-nH6Q)

##  <a name="Clipping"></a> Erstellen eines Beschneidungspfads
 Freistellungspfade sind Pfade oder Formen, die auf ein anderes Objekt angewendet werden. Die Teile des maskierten Objekts, die außerhalb des Freistellungspfads liegen, werden ausgeblendet.

 ![Beschneidungspfad](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

 **Sehen Sie sich ein kurzes Video an:** ![Installierte Features konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.png) [Arbeiten mit Pfaden: Erstellen eines Beschneidungspfads](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232)

## <a name="see-also"></a>Siehe auch

- [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)