---
title: 'Gewusst wie: Erstellen eines Graustufentextur-Shaders'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c1910926c6cb2d181f4e5e24ffb1bc1c75a56b3
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924186"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Vorgehensweise: Erstellen eines Graustufentexturshaders

In diesem Artikel wird veranschaulicht, wie der Shader-Designer und die Directed Graph Shader Language (DGSL) zum Erstellen eines Graustufentextur-Shaders verwendet werden. Dieser Shader verändert die RGB-Farbwerte des Textursamples und verwendet es anschließend zusammen mit dem unveränderten Alphawert, um die endgültige Farbe festzulegen.

## <a name="create-a-grayscale-texture-shader"></a>Erstellen eines Graustufentextur-Shaders

Sie können einen Graustufentextur-Shader implementieren, indem Sie den Farbwert eines Textursamples ändern, bevor Sie es in die endgültige Ausgabefarbe schreiben.

Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.

1.  Erstellen Sie wie unter [Vorgehensweise: Erstellen eines Basistexturshaders](../designers/how-to-create-a-basic-texture-shader.md) beschrieben einen Basistexturshader.

2.  Trennen Sie das Terminal **RGB** des Knotens **Textursample** vom Terminal **RGB** des Knotens **Endgültige Farbe**. Klicken Sie im Modus **Auswählen** auf das Terminal **RGB** des Knotens **Textursample** und anschließend auf **Link aufheben**. Dadurch wird Platz für den Knoten geschaffen, der im nächsten Schritt hinzugefügt wird.

3.  Fügen Sie einen Knoten **Entsättigen** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Filter** auf **Entsättigen**, und verschieben Sie es auf die Entwurfsoberfläche.

4.  Berechnen Sie den Graustufenwert mithilfe des Knotens **Entsättigen**. Verschieben Sie im Modus **Auswählen** das Terminal **RGB** des Knotens **Textursample** auf das Terminal **RGB** des Knotens **Entsättigen**.

    > [!NOTE]
    > In der Standardeinstellung entsättigt der Knoten **Entsättigen** die Eingabefarbe vollständig und nutzt für die Graustufen-Konvertierung die normale Gewichtung der Leuchtdichte. Sie können ändern, wie sich der Knoten **Entsättigen** verhält, indem Sie entweder den Wert der Eigenschaft **Leuchtdichte** ändern, oder indem Sie die Eingabefarbe teilweise entsättigen. Bestimmen Sie einen Skalarwert im Bereich [0,1) für das Terminal **Prozent** des Knotens **Entsättigen**, um die Eingabefarbe teilweise zu entsättigen.

5.  Verbinden Sie den berechneten Graustufenwert mit der endgültige Farbe. Verschieben Sie das Terminal **Ausgabe** des Knotens **Entsättigen** auf das Terminal **RGB** des Knotens **Endgültige Farbe**.

In der folgenden Abbildung wird das fertige Shader-Diagramm sowie eine Vorschau eines Würfels gezeigt, auf dem der Shader angewandt wurde.

> [!NOTE]
> In dieser Abbildung wird eine Ebene als Vorschauform verwendet, und eine Textur wurde angegeben, um den Effekt des Shaders besser zu veranschaulichen.

![Shader-Diagramm und eine Vorschau seiner Effekte](../designers/media/digit-grayscale-effect.png)

Bestimmte Formen sorgen vielleicht für bessere Vorschauen für einige Shader. Weitere Informationen zur Verwendung der Vorschau von Shadern im Shader-Designer finden Sie unter [Shader-Designer](../designers/shader-designer.md).

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md)
- [Bildbearbeitung](../designers/image-editor.md)
- [Shader-Designer](../designers/shader-designer.md)
- [Shader-Designer-Knoten](../designers/shader-designer-nodes.md)