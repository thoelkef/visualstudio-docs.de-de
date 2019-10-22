---
title: Arbeiten mit Elementen in XAML-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 483023fbd28da26d9967dd2d88bc37748d00f088
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663984"
---
# <a name="working-with-elements-in-xaml-designer"></a>Arbeiten mit Elementen im XAML-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Ihrer App in XAML im Code oder unter Verwendung des XAML-Designers Elemente hinzufügen (Steuerelemente, Layouts und Formen). Dieses Thema beschreibt, wie Elemente im XAML-Designer in Visual Studio oder in Blend für Visual Studio verwendet werden.

## <a name="adding-an-element-to-a-layout"></a>Einem Layout ein Element hinzufügen
 *Layout* ist der Prozess der Größenanpassung und Positionierung von Elementen in einer Benutzeroberfläche. Um visuelle Elemente zu positionieren, müssen Sie sie in einen [Bereich](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx) eines Layouts einfügen. Ein `Panel` verfügt über eine untergeordnete Eigenschaft, die eine Auflistung von [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/br208706.aspx)-Typen ist. Sie können verschiedene untergeordnete `Panel`-Elemente wie z.B. [Canvas](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx) und [Grid](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) verwenden, um sie als Layoutcontainer zu nutzen und auf einer Seite zu positionieren und anzuordnen.

 Standardmäßig wird ein `Grid`-Bereich als Layoutcontainer der obersten Ebene innerhalb einer Seite oder eines Formulars verwendet. Sie können Layoutbereiche, Steuerelemente oder andere Elemente innerhalb der obersten Ebene des Seitenlayouts hinzufügen.

#### <a name="to-add-an-element-to-a-layout"></a>Einem Layout ein Element hinzufügen

- Führen Sie im XAML-Designer eine der folgenden Aktionen aus:

  - Doppelklicken Sie auf ein Element in der **Toolbox** (oder wählen Sie ein Element in der Toolbox aus, und drücken Sie die EINGABETASTE).

  - Ziehen Sie ein Element aus der **Toolbox** auf die Zeichenfläche.

  - Klicken Sie in der **Toolbox** auf eines der Zeichenwerkzeuge (z.B. [Ellipse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) oder [Rechteck](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)), und zeichnen Sie dann ein Element im aktiven Bereich.

## <a name="changing-the-layering-order-of-elements"></a>Die Ebenenreihenfolge von Elementen ändern
 Gibt es zwei Elemente auf der Zeichenfläche im XAML-Designer, wird ein Element vor dem anderen in der Ebenenreihenfolge angezeigt. Am unteren Rand der Liste der Elemente im Dokumentgliederungsfenster ist das vorderste Element (außer wenn die **ZIndex**-Eigenschaft für ein Element festgelegt ist). Wenn Sie ein Element in eine Seite, ein Formular oder einen Layoutcontainer einfügen, wird das Element automatisch vor anderen Elementen im aktiven Containerelement platziert. Um die Reihenfolge von Elementen zu ändern, können Sie die **Reihenfolge**-Befehle verwenden oder die Elemente in der Objektstruktur im Dokumentgliederungsfenster verschieben.

#### <a name="to-change-the-layering-order"></a>So ändern Sie die Ebenenreihenfolge

- Führen Sie einen der folgenden Schritte aus:

  - Ziehen Sie im Fenster **Dokumentgliederung** die Elemente nach oben oder unten, um die gewünschte Ebenenreihenfolge zu erstellen.

  - Klicken Sie mit der rechten Maustaste auf das Element im Dokumentgliederungsfenster oder auf der Zeichenfläche, für das Sie die Ebenenreihenfolge ändern möchten, zeigen Sie auf **Reihenfolge**, und klicken Sie dann auf eine der folgenden Optionen:

    - **In den Vordergrund**, um das Element in der Reihenfolge ganz nach vorne zu verschieben.

    - **Eine Ebene nach vorne**, um das Objekt eine Ebene in der Reihenfolge nach vorne zu holen.

    - **Eine Ebene nach hinten**, um das Objekt eine Ebene in der Reihenfolge nach hinten zu verschieben.

    - **In den Hintergrund**, um das Element hinter alle anderen Elemente in der Reihenfolge zu verschieben.

    Ändern Sie die **ZIndex**-Eigenschaft im **Layout**-Abschnitt im Eigenschaftenfenster. Bei überlappenden Elementen hat die **ZIndex**-Eigenschaft Vorrang vor der Reihenfolge der Elemente, die im Dokumentgliederungsfenster angezeigt werden. Ein Element mit einem niedrigeren **ZIndex**-Wert wird im Vordergrund angezeigt, wenn sich Elemente überlappen.

## <a name="changing-the-alignment-of-an-element"></a>Die Ausrichtung eines Elements ändern
 Sie können Elemente auf der Zeichenfläche mit Menübefehlen oder durch Ziehen von Elementen an Ausrichtungslinien ausrichten.

 Eine *Ausrichtungslinie* ist ein visueller Hinweis, an dem Sie ein Element relativ zu anderen Elementen in der App ausrichten können.

#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>So richten Sie zwei oder mehr Elemente mithilfe von Menübefehlen aus

1. Wählen Sie die Elemente aus, welche Sie ausrichten möchten. Sie können mehr als ein Element auswählen, indem Sie die STRG-Taste gedrückt halten, während Sie die Elemente auswählen.

2. Wählen Sie eine der folgenden Eigenschaften unter **Horizontale Ausrichtung** im **Layout**-Abschnitt des Eigenschaftenfensters aus: **Links**, **Mitte**, **Rechts** oder **Strecken**.

3. Wählen Sie eine der folgenden Eigenschaften unter **Vertikale Ausrichtung** im **Layout**-Abschnitt des Eigenschaftenfensters aus: **Oben**, **Mitte**, **Unten** oder **Strecken**.

#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>Zwei oder mehr Elemente mithilfe von Ausrichtungslinien ausrichten

- Im XAML-Designer, in einem Layout mit mindestens zwei Elementen: Ziehen Sie eines der Elemente oder ändern Sie dessen Größen, sodass die Kante an einem anderen Element ausgerichtet ist.

     Wenn die Kanten ausgerichtet sind, wird eine *Ausrichtungsgrenze* angezeigt, um die Ausrichtung anzugeben. Die Ausrichtungsgrenze ist eine rot-gestrichelte Linie. Ausrichtungsgrenzen werden nur angezeigt, wenn **Andocken an Ausrichtungslinien** aktiviert ist. Eine Abbildung der Zeichenfläche, die eine Ausrichtungsgrenze zeigt, finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="changing-the-an-elements-margins"></a>Ändern der Ränder eines Elements
 Die Ränder im XAML-Designer bestimmen den Umfang des Leerraums, der sich um einem Element auf der Zeichenfläche befindet. Ränder geben beispielsweise den Raum zwischen den äußeren Kanten eines Elements und den Grenzen eines `Grid`-Bereichs an, welcher das Element enthält. Ränder geben auch den vorhandenen Raum zwischen Elementen an, die in einem `StackPanel` enthalten sind.

#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>So ändern Sie die Ränder eines Elements im Eigenschaftenfenster

1. Wählen Sie das Element aus, dessen Ränder Sie ändern möchten.

2. Ändern Sie im Eigenschaftenfenster unter **Layout** den Wert (in Pixel oder in geräteunabhängigen Einheiten von etwa 1/96 Zoll) für die gewünschten **Ränder**-Eigenschaften: **Oben**, **Links**, **Rechts** oder **Unten**.

#### <a name="to-change-an-elements-margins-in-the-artboard"></a>So ändern Sie die Ränder eines Elements auf der Zeichenfläche

- Um die Ränder eines Elements relativ zu dessen Layoutcontainer zu ändern, klicken Sie auf die *Rand-Adorner*, die um das Element auf der Zeichenfläche angezeigt werden, wenn das Element ausgewählt ist und sich in einem Container befindet. Eine Abbildung der Rand-Adorner finden Sie unter [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     Wenn ein Randfunktionsindikator geöffnet ist, sei es vertikal oder horizontal, dann ist besagter Rand noch nicht festgelegt. Wenn ein Randfunktionsindikator geschlossen ist, dann ist besagter Rand festgelegt.

     Wenn Sie ein Rand-Adorner öffnen und der gegenüberliegende Rand nicht festgelegt ist, wird der gegenüberliegende Rand auf den richtigen Wert gemäß der Position des Elements auf der Zeichenfläche festgelegt. Für gegenüberliegende Ränder wie die Ränder **Links** und **Rechts** wird stets mindestens eine Eigenschaft festgelegt.

    > [!IMPORTANT]
    > Elemente, die innerhalb irgendwelcher Layoutcontainers platziert werden, wie beispielsweise ein <xref:Windows.UI.Xaml.Controls.Canvas>, haben keine Randfunktionsindikatoren. Elemente, die innerhalb eines <xref:Windows.UI.Xaml.Controls.StackPanel> platziert werden, haben Funktionsindikatoren für entweder die linken und rechten Ränder oder für die oberen und unteren Ränder, abhängig von der Ausrichtung des `StackPanel`.

## <a name="grouping-and-ungrouping-elements"></a>Elemente gruppieren und dessen Gruppierung aufheben
 Durch die Gruppierung von zwei oder mehr Elementen im XAML-Designer wird ein neuer Layoutcontainer erstellt und die betreffenden Elemente innerhalb dieses Containers platziert. Durch die gemeinsame Platzierung von zwei oder mehr Elementen in einem Layoutcontainer wird Ihnen ermöglicht, die Gruppe einfach auszuwählen, zu bewegen und zu transformieren, so als ob die Elemente innerhalb dieser Gruppe ein Element wären. Die Gruppierung ist auch zur Bestimmung von Elementen nützlich, die in irgend einer Weise im Verhältnis zueinander stehen, wie die Schaltflächen, die ein Navigationselement ergeben. Wenn Sie die Gruppierung für Elemente aufheben, löschen Sie einfach den Layoutcontainer, welcher die Elemente enthielt.

#### <a name="to-group-elements-into-a-new-layout-container"></a>So gruppieren Sie Elemente in einen neuen Layoutcontainer

1. Wählen Sie die Elemente aus, welche Sie gruppieren möchten. (Um mehrere Elemente auszuwählen, halten Sie die STRG-Taste gedrückt, während Sie auf die Elemente klicken.)

2. Klicken Sie mit der rechten Maustaste auf die ausgewählten Elemente, zeigen Sie auf **Gruppieren in**, und klicken Sie dann auf den Typ des Layoutcontainers, in dem die Gruppe platziert werden soll.

    > [!TIP]
    > Bei der Auswahl von <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> oder <xref:Windows.UI.Xaml.Controls.ScrollViewer>, um die Elemente zu gruppieren, werden die Elemente in einem neuen <xref:Windows.UI.Xaml.Controls.Grid>-Bereich innerhalb von <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> oder <xref:Windows.UI.Xaml.Controls.ScrollViewer> platziert. Wenn Sie die Gruppierung von Elementen in einem dieser Layoutcontainer aufheben, werden nur das <xref:Windows.UI.Xaml.Controls.Viewbox>, der <xref:Windows.UI.Xaml.Controls.Border> oder der <xref:Windows.UI.Xaml.Controls.ScrollViewer> gelöscht, und der Bereich <xref:Windows.UI.Xaml.Controls.Grid> wird beibehalten. Löschen Sie den `Grid`-Bereich, heben Sie die Gruppierung der Elemente erneut auf.

#### <a name="to-ungroup-elements-and-delete-the-layout"></a>So heben Sie die Gruppierung von Elementen auf und löschen das Layout

- Klicken Sie mit der rechten Maustaste auf die Gruppierung, die Sie aufheben möchten, und klicken Sie auf **Gruppierung aufheben**.

  Sie können Elemente auch durch einen Rechtsklick auf ausgewählte Elemente im Dokumentgliederungsfenster und durch Klicken auf **Gruppieren in** oder **Gruppierung aufheben** gruppieren bzw. die Gruppierung aufheben.

## <a name="resetting-the-element-layout"></a>Zurücksetzen des Elementlayouts
 Sie können Standardwerte für bestimmte Layouteigenschaften eines Elements wiederherstellen, indem Sie die Befehlen zum Zurücksetzen von Layouts verwenden. Mit diesem Befehl können Sie den Rand, die Ausrichtung, die Breite, Höhe sowie Größe eines Elements zurücksetzen, entweder für jedes Element einzeln oder zusammen.

#### <a name="to-reset-the-element-layout"></a>So setzen Sie das Elementlayout zurück

- Klicken Sie im Dokumentgliederungsfenster oder auf der Zeichenfläche mit der rechten Maustaste auf das Element, und wählen Sie **Layout**, **Zurücksetzen** *Eigenschaftsname* aus, wobei *Eigenschaftsname* die Eigenschaft ist, die Sie zurücksetzen möchten (oder wählen Sie **Layout**, **Alle zurücksetzen** aus, um alle Layouteigenschaften für das Element zurückzusetzen).

## <a name="see-also"></a>Siehe auch
 [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
