---
title: 'Vorgehensweise: Erstellen eines geometriebasierten Farbverlauf-Shaders | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1d9bfa9a6e9be1a97b3a606aa302defd12a8d062
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664526"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Gewusst wie: Erstellen eines geometriebasierten Farbverlauf-Shaders
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird gezeigt, wie der Shader-Designer und die Directed Graph Shader Language zum Erstellen eines geometriebasierten Farbverlauf-Shaders verwendet wird. Dieser Shader skaliert einen konstanten RGB-Farbwert anhand der Höhe von jedem Punkt eines Objekts im Raum.

 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:

- Hinzufügen von Knoten in ein Shader-Diagramm

- Einstellen der Knoteneigenschaften

- Trennen der Knoten

- Verbinden der Knoten

## <a name="creating-a-geometry-based-gradient-shader"></a>Erstellen eines geometriebasierten Farbverlauf-Shaders
 Sie können einen geometriebasierten Farbverlauf-Shader implementieren, indem Sie die Position des Pixels in Ihrem Shader aufnehmen. Ein Pixel enthält in Schattierungssprachen mehr Informationen als nur seine Farbe und Position auf einem 2D-Bildschirm. Ein Pixel, das als ein *Fragment* in manchen Systemen bekannt ist, ist eine Auflistung von Werten, das die Oberfläche beschreibt, die einem Pixel entspricht. Der Shader, der in diesem Dokument beschriebenen wird, nutzt die Höhe der einzelnen Pixel eines 3D-Objekts im Raum, um die endgültige Ausgabe des Fragments zu beeinflussen.

 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.

#### <a name="to-create-a-geometry-based-gradient-shader"></a>So erstellen einen geometriebasierten Farbverlauf-Shader

1. Erstellen Sie einen DGSL-Shader, mit dem Sie arbeiten können. Wie Sie dem Projekt einen DGSL-Shader hinzufügen, erfahren Sie im Abschnitt „Erste Schritte“ unter [Shader-Designer](../designers/shader-designer.md)

2. Trennen Sie den Knoten **Farbpunkt** vom Knoten **Endgültige Farbe**. Klicken Sie auf das Terminal **RGB** des Knotens **Farbpunkt** und anschließend auf **Link aufheben**. Dadurch wird Platz für den Knoten geschaffen, der im nächsten Schritt hinzugefügt wird.

3. Fügen Sie einen Knoten **Multiplizieren** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Mathematik** auf **Multiplizieren** und verschieben Sie es auf die Entwurfsoberfläche.

4. Fügen Sie einen Knoten **Maskierungsvektor** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Hilfsprogramme** auf **Maskierungsvektor**, und verschieben Sie es auf die Entwurfsoberfläche.

5. Geben Sie Maskierungswerte für den Knoten **Maskierungsvektor** an. Klicken Sie im Modus **Auswählen** auf den Knoten **Maskierungsvektor**, und legen Sie anschließend im Fenster **Eigenschaften** die Eigenschaft **Grün / Y** auf **TRUE** sowie die Eigenschaften **Rot / X**, **Blau / Z** und **Alpha / W** auf **FALSE** fest. In diesem Beispiel entsprechend die Eigenschaften **Rot / X**, **Grün / Y** und **Blau / Z** den Komponenten „x“, „y“ und „z“ des Knotens **Raumposition**. **Alpha / W** wird nicht verwendet. Da nur **Grün / Y** auf **TRUE** festgelegt wird, bleibt nur die Y-Komponente des Eingabevektors, nachdem sie maskiert wurde.

6. Fügen Sie einen Knoten **Raumposition** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Konstanten** auf **Raumposition**, und verschieben Sie es auf die Entwurfsoberfläche.

7. Maskieren Sie die Raumposition des Fragments. Verschieben Sie im Modus **Auswählen** das Terminal **Ausgabe** des Knotens **Raumposition** auf das Terminal **Vektor** des Knotens **Maskierungsvektor**. Diese Verbindung maskiert die Position des Fragments, um die Komponenten „x“ und „y“ zu ignorieren.

8. Multiplizieren Sie die RGB-Farbkonstante anhand der Position der maskierten Raumposition. Verschieben Sie das Terminal **RGB** des Knotens **Farbpunkt** auf das Terminal **Y** des Knotens **Multiplizieren**. Verschieben Sie anschließend das Terminal **Ausgabe** des Knotens **Maskierungsvektor** auf das Terminal **X** des Knotens **Multiplizieren**. Diese Verbindung skaliert den Farbwert anhand der Pixelhöhe im Raum.

9. Verbinden Sie den berechneten Farbwert mit der endgültige Farbe. Verschieben Sie das Terminal **Ausgabe** des Knotens **Multiplizieren** auf das Terminal **RGB** des Knotens **Endgültige Farbe**.

   In der folgenden Abbildung wird das fertige Shader-Diagramm sowie eine Vorschau einer Kugel gezeigt, auf der der Shader angewandt wurde.

> [!NOTE]
> In dieser Abbildung wird eine orangene Farbe ausgewählt, um den Effekt des Shaders besser zu veranschaulichen. Da die Vorschauform jedoch keine Position im Raum hat, kann der Shader nicht vollständig im Voraus im Shader-Designer angeschaut werden. Der Shader muss in einer echten Szene vorausgeschaut werden, um den vollen Effekt zu demonstrieren.

 ![Shader-Diagramm und eine Vorschau seiner Effekte](../designers/media/digit-gradient-effect-graph.png "Digit-Gradient-Effect-Graph")

 Bestimmte Formen sorgen vielleicht für bessere Vorschauen für einige Shader. Weitere Informationen zum Anzeigen einer Vorschau von Shadern im Shader-Designer finden Sie unter Vorschau von **Shadern** im [Shader-Designer](../designers/shader-designer.md) .

 Die folgende Abbildung zeigt den Shader, der in diesem Dokument beschrieben wird, das auf die 3D-Szene angewendet wird, die in Gewusst [wie: Modellieren eines 3D-Geländes](../designers/how-to-model-3-d-terrain.md)veranschaulicht wird. Die Farbintensität erhöht sich durch die Höhe der Punkte im Raum.

 ![Auf ein 3&#45;D-Geländemodell angewendeter Farbverlaufs Effekt](../designers/media/digit-gradient-effect-result.png "Digit-Gradient-Effect-result")

 Weitere Informationen zum Anwenden eines Shaders auf ein 3D-Modell finden Sie unter Gewusst [wie: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Weitere Informationen
 Vorgehens [Weise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md) Gewusst [wie: Exportieren eines Shaders](../designers/how-to-export-a-shader.md) Gewusst wie: Modellieren des [3D-Geländes](../designers/how-to-model-3-d-terrain.md) Gewusst [wie: Erstellen eines Graustufen Textur](../designers/how-to-create-a-grayscale-texture-shader.md) -Shader- [Designer](../designers/shader-designer.md) -Shader-Designer- [Knoten](../designers/shader-designer-nodes.md)
