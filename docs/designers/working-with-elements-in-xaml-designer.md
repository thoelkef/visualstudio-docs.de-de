---
title: Arbeiten mit Elementen im XAML-Designer
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 1fa232ccefed20608ec2391f591ac0a8a6f31fe2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931337"
---
# <a name="work-with-elements-in-xaml-designer"></a>Arbeiten mit Elementen im XAML-Designer

Sie können Elemente – Steuerelemente, Layouts und Formen – der App in XAML, im Code oder mit dem XAML-Designer hinzufügen. Dieses Thema beschreibt, wie Elemente im XAML-Designer in Visual Studio oder in Blend für Visual Studio verwendet werden.

## <a name="add-an-element-to-a-layout"></a>Hinzufügen eines Elements zu einem Layout

*Layout* ist der Prozess der Größenanpassung und Positionierung von Elementen in einer Benutzeroberfläche. Um visuelle Elemente zu positionieren, müssen Sie sie in einen [Bereich](/uwp/api/Windows.UI.Xaml.Controls.Panel) eines Layouts einfügen. Ein `Panel` verfügt über eine untergeordnete Eigenschaft, die eine Auflistung von [FrameworkElement](/uwp/api/Windows.UI.Xaml.FrameworkElement)-Typen ist. Sie können verschiedene untergeordnete `Panel`-Elemente wie z.B. [Canvas](/uwp/api/Windows.UI.Xaml.Controls.Canvas), [StackPanel](/uwp/api/Windows.UI.Xaml.Controls.StackPanel) und [Grid](/uwp/api/Windows.UI.Xaml.Controls.Grid) verwenden, um sie als Layoutcontainer zu nutzen und auf einer Seite zu positionieren und anzuordnen.

Standardmäßig wird ein `Grid`-Bereich als Layoutcontainer der obersten Ebene innerhalb einer Seite oder eines Formulars verwendet. Sie können Layoutbereiche, Steuerelemente oder andere Elemente innerhalb des Seitenlayouts der obersten Ebene hinzufügen.

Wenn Sie in XAML-Designer einem Layout ein Element hinzufügen möchten, müssen Sie einen der folgenden Schritte ausführen:

- Doppelklicken Sie auf ein Element in der **Toolbox** (oder wählen Sie ein Element in der Toolbox aus, und drücken Sie die **EINGABETASTE**).

- Ziehen Sie ein Element aus der **Toolbox** auf die Zeichenfläche.

- Klicken Sie in der **Toolbox** auf eines der Zeichenwerkzeuge (z.B. [Ellipse](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) oder [Rechteck](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)), und zeichnen Sie dann ein Element im aktiven Bereich.

## <a name="change-the-layering-order-of-elements"></a>Ändern der Ebenenreihenfolge von Elementen

Wenn auf der Zeichenfläche im XAML-Designer zwei Elemente vorhanden sind, wird ein Element vor dem anderen in der Ebenenreihenfolge angezeigt. Am unteren Rand der Liste der Elemente im Dokumentgliederungsfenster ist das vorderste Element (außer wenn die **ZIndex**-Eigenschaft für ein Element festgelegt ist). Wenn Sie ein Element in eine Seite, ein Formular oder einen Layoutcontainer einfügen, wird das Element automatisch vor anderen Elementen im aktiven Containerelement platziert. Um die Reihenfolge von Elementen zu ändern, können Sie die **Reihenfolge**-Befehle verwenden oder die Elemente in der Objektstruktur im Dokumentgliederungsfenster verschieben.

Wenn Sie Ebenenreihenfolge ändern möchten, müssen Sie einen der folgenden Schritte ausführen:

- Ziehen Sie im Fenster **Dokumentgliederung** die Elemente nach oben oder unten, um die gewünschte Ebenenreihenfolge zu erstellen.

- Klicken Sie mit der rechten Maustaste auf das Element im Dokumentgliederungsfenster oder auf der Zeichenfläche, für das Sie die Ebenenreihenfolge ändern möchten, zeigen Sie auf **Reihenfolge**, und klicken Sie dann auf eine der folgenden Optionen:

   - **In den Vordergrund**, um das Element in der Reihenfolge ganz nach vorne zu verschieben.

   - **Eine Ebene nach vorne**, um das Objekt eine Ebene in der Reihenfolge nach vorne zu holen.

   - **Eine Ebene nach hinten**, um das Objekt eine Ebene in der Reihenfolge nach hinten zu verschieben.

   - **In den Hintergrund**, um das Element hinter alle anderen Elemente in der Reihenfolge zu verschieben.

   Ändern Sie die **ZIndex**-Eigenschaft im **Layout**-Abschnitt im Eigenschaftenfenster. Bei überlappenden Elementen hat die **ZIndex**-Eigenschaft Vorrang vor der Reihenfolge der Elemente, die im Dokumentgliederungsfenster angezeigt werden. Ein Element mit einem höheren **ZIndex**-Wert wird im Vordergrund angezeigt, wenn sich Elemente überlappen.

## <a name="change-the-alignment-of-an-element"></a>Ändern der Ausrichtung eines Objekts

Sie können Elemente auf der Zeichenfläche mit Menübefehlen oder durch Ziehen von Elementen an Ausrichtungslinien ausrichten.

Eine *Ausrichtungslinie* ist ein visueller Hinweis, an dem Sie ein Element relativ zu anderen Elementen in der App ausrichten können.

So richten Sie zwei oder mehr Elemente mithilfe der Menübefehle aus:

1.  Wählen Sie die Elemente aus, die Sie ausrichten möchten. Sie können mehr als ein Element auswählen, indem Sie die **STRG-TASTE** gedrückt halten, während Sie die Elemente auswählen.

2.  Wählen Sie im Abschnitt **Layout** des Eigenschaftenfensters unter **Horizontale Ausrichtung** eine der folgenden Eigenschaften aus: **Links**, **Mitte**, **Rechts** oder **Strecken**.

3.  Wählen Sie im Abschnitt **Layout** des Eigenschaftenfensters unter **Vertikale Ausrichtung** eine der folgenden Eigenschaften aus: **Oben**, **Mitte**, **Unten** oder **Strecken**.

Wenn Sie zwei oder mehr Elemente in XAML-Designer mithilfe von Ausrichtungslinien ausrichten möchten, ziehen Sie in einem Layout mit mindestens zwei Elementen eines der Elemente (oder ändern Sie die Größe), sodass der Rand auf ein anderes Element ausgerichtet ist.

Wenn die Kanten ausgerichtet sind, wird eine *Ausrichtungsgrenze* angezeigt, um die Ausrichtung anzugeben. Die Ausrichtungsgrenze ist eine rote gestrichelte Linie. Ausrichtungsgrenzen werden nur angezeigt, wenn **Andocken an Ausrichtungslinien** aktiviert ist. Eine Abbildung der Zeichenfläche, die eine Ausrichtungsgrenze zeigt, finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Ändern der Ränder eines Elements

Die Ränder im XAML-Designer bestimmen die Menge an leerem Platz um ein Element in der Zeichenfläche. Ränder geben beispielsweise an, wie viel Platz zwischen den äußeren Kanten eines Elements und den Begrenzungen eines `Grid`-Bereichs frei bleibt, der das Objekt enthält. Durch Ränder wird auch die Größe des Abstands zwischen Elementen angegeben, die in einem `StackPanel`-Element enthalten sind.

So ändern Sie die Ränder eines Elements im Eigenschaftenfenster:

1.  Wählen Sie das Element aus, dessen Ränder Sie ändern möchten.

2.  Ändern Sie im Eigenschaftenfenster unter **Layout** den Wert (in Pixel oder in geräteunabhängigen Einheiten von etwa 1/96 Zoll) für die gewünschten **Ränder**-Eigenschaften: **Oben**, **Links**, **Rechts** oder **Unten**.

Wenn Sie auf der Zeichenfläche die Ränder eines Elements relativ zu dessen Layoutcontainer ändern möchten, klicken Sie auf die *Rand-Adorner*, die um das Element angezeigt werden, wenn es ausgewählt ist und sich in einem Container befindet. Eine Abbildung der Rand-Adorner finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Wenn ein Adorner für den Rand (vertikal oder horizontal) geöffnet ist, wurde der jeweilige Rand nicht festgelegt. Wenn ein Rand-Adorner geschlossen wird, wird dieser Rand festgelegt.

Wenn Sie einen Randfunktionsindikator öffnen und der gegenüber liegende Rand nicht festgelegt ist, wird für den gegenüber liegenden Rand der richtige Wert gemäß der Position des Elements auf der Zeichenfläche festgelegt. Für gegenüberliegende Ränder wie die Ränder **Links** und **Rechts** wird stets mindestens eine Eigenschaft festgelegt.

> [!IMPORTANT]
> Elemente, die innerhalb von Layoutcontainern platziert sind, zum Beispiel ein <xref:Windows.UI.Xaml.Controls.Canvas>-Element, haben keine Rand-Adorner. Elemente, die innerhalb eines <xref:Windows.UI.Xaml.Controls.StackPanel>-Elements platziert sind, haben Rand-Adorner für die linken und rechten Rändern oder für Die oberen und unteren Ränder, je nach Ausrichtung des `StackPanel`-Elements.

## <a name="group-and-ungroup-elements"></a>Gruppieren von Elementen und Gruppierung aufheben

Das Gruppieren von zwei oder mehr Elementen im XAML-Designer erstellt einen neuen Layoutcontainer und platziert diese Elemente innerhalb dieses Containers. Wenn Sie zwei oder mehr Elemente gemeinsam in einem Layoutcontainer platzieren, können Sie die Gruppe genauso problemlos auswählen, verschieben und transformieren, als ob die Elemente in dieser Gruppe ein einzelnes Element wären. Das Gruppieren ist außerdem zum Identifizieren von Elementen hilfreich, die auf eine bestimmte Weise miteinander verbunden sind, wie z. B. die Schaltflächen, die zusammen ein Navigationselement bilden. Wenn Sie die Gruppierung von Elementen aufheben, löschen Sie lediglich den Layoutcontainer, in dem die Elemente enthalten waren.

So gruppieren Sie Elemente in einem neuen Layoutcontainer:

1. Wählen Sie die zu gruppierenden Elemente aus. (Um mehrere Elemente auszuwählen, halten Sie die **STRG-TASTE** gedrückt, während Sie auf die Elemente klicken.)

2. Klicken Sie mit der rechten Maustaste auf die ausgewählten Elemente, zeigen Sie auf **Gruppieren in**, und klicken Sie dann auf den Typ des Layoutcontainers, in dem die Gruppe platziert werden soll.

    > [!TIP]
    > Bei der Auswahl von <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> oder <xref:Windows.UI.Xaml.Controls.ScrollViewer>, um die Elemente zu gruppieren, werden die Elemente in einem neuen <xref:Windows.UI.Xaml.Controls.Grid>-Bereich innerhalb von <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> oder <xref:Windows.UI.Xaml.Controls.ScrollViewer> platziert. Wenn Sie die Gruppierung von Elementen in einem dieser Layoutcontainer aufheben, werden nur <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> oder <xref:Windows.UI.Xaml.Controls.ScrollViewer> gelöscht, und der <xref:Windows.UI.Xaml.Controls.Grid>-Bereich bleibt. Um den `Grid`-Bereich zu löschen, heben Sie die Gruppierung der Elemente wieder auf.

Wenn Sie die Gruppierung von Elementen aufheben möchten, klicken Sie mit der rechten Maustaste auf die Gruppierung, die Sie aufheben möchten, und klicken Sie dann auf **Gruppierung aufheben**. Sie können Elemente auch durch einen Rechtsklick auf ausgewählte Elemente im Dokumentgliederungsfenster und durch Klicken auf **Gruppieren in** oder **Gruppierung aufheben** gruppieren bzw. die Gruppierung aufheben.

## <a name="reset-the-element-layout"></a>Zurücksetzen des Elementlayouts

Sie können Standardwerte für bestimmte Layouteigenschaften eines Elements wiederherstellen, indem Sie die Befehlen zum Zurücksetzen von Layouts verwenden. Mit diesem Befehl können Sie Rand, Ausrichtung, Breite, Höhe und Größe eines Elements einzeln oder gemeinsam zurücksetzen.

Wenn Sie das Elementlayout zurücksetzen möchten, klicken Sie im Dokumentgliederungsfenster oder auf der Zeichenfläche mit der rechten Maustaste auf das Element, und wählen Sie dann **Layout** > **Zurücksetzen** *Eigenschaftsname* aus, wobei *Eigenschaftsname* die Eigenschaft ist, die Sie zurücksetzen möchten (oder wählen Sie **Layout** > **Alle zurücksetzen** aus, um alle Layouteigenschaften für das Element zurückzusetzen).

## <a name="see-also"></a>Siehe auch

- [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
