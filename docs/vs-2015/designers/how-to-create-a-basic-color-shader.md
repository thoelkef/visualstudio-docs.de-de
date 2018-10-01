---
title: 'Vorgehensweise: Erstellen eines standardmäßigen Farbshaders | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 23a7082c305bdabf139e284d448fafdf375762e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512664"
---
# <a name="how-to-create-a-basic-color-shader"></a>Gewusst wie: Erstellen eines standardmäßigen Farbshaders
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Erstellen eines standardmäßigen Farbshaders](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-color-shader).  
  
In diesem Dokument wird gezeigt, wie der Shader-Designer und die Directed Graph Shader Language (DGSL) zum Erstellen eines flachen Farbshaders verwendet wird. Dieser Shader legt die endgültige Farbe auf einen konstanten RGB-Farbwert fest.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Entfernen von Knoten aus einem Diagramm  
  
-   Hinzufügen von Knoten in ein Diagramm  
  
-   Einstellen der Knoteneigenschaften  
  
-   Verbinden der Knoten  
  
## <a name="creating-a-flat-color-shader"></a>Erstellen eines flachen Farbshaders  
 Sie können einen flachen Farbshader implementieren, indem Sie die Farbwerte einer RGB-Farbkonstante in die endgültige Ausgabefarbe schreiben.  
  
 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.  
  
#### <a name="to-create-a-flat-color-shader"></a>So erstellen Sie einen flachen Farbshader  
  
1.  Erstellen Sie einen DGSL-Shader, mit dem Sie arbeiten können. Wie Sie dem Projekt einen DGSL-Shader hinzufügen, erfahren Sie im Abschnitt „Erste Schritte“ unter [Shader-Designer](../designers/shader-designer.md)  
  
2.  Löschen Sie den Knoten **Punktfarbe**. Verwenden Sie das Tool **Auswählen**, um den Knoten **Punktfarbe** auszuwählen, und klicken Sie anschließend in der Menüleiste auf **Bearbeiten** > **Entfernen**.  
  
3.  Fügen Sie einen Knoten **Farbkonstante** zum Diagramm hinzu. Klicken Sie in der **Toolbox** unter **Konstanten** auf **Farbkonstante**, und verschieben Sie es auf die Entwurfsoberfläche.  
  
4.  Geben Sie einen Farbwert für den Knoten **Farbkonstante** an. Verwenden Sie das Tool **Auswählen**, um den Knoten **Farbkonstante** auszuwählen, und geben Sie anschließend im Fenster **Eigenschaften** unter der Eigenschaft **Ausgabe** einen Farbwert an. Geben Sie für Orange einen Wert von (1.0, 0,5, 0,2, 1.0) an.  
  
5.  Verbinden Sie die Farbkonstante mit der endgültigen Farbe. Verschieben Sie das Terminal **RGB** des Knotens **Farbkonstante** auf das Terminal **RGB** des Knotens **Endgültige Farbe**, um die Verbindungen zu herzustellen. Verschieben Sie anschließend das Terminal **Alpha** des Knotens **Farbkonstante** auf das Terminal **Alpha** des Knotens **Endgültige Farbe**. Diese Verbindungen legen die endgültige Farbe auf die Farbkonstante fest, die im vorherigen Schritt definiert wurde.  
  
 In der folgenden Abbildung wird das fertige Shader-Diagramm sowie eine Vorschau eines Würfels gezeigt, auf dem der Shader angewandt wurde.  
  
> [!NOTE]
>  In der Abbildung wurde eine orangene Farbe angegeben, um den Effekt des Shaders besser zu veranschaulichen.  
  
 ![Shader-Diagramm und seine Ergebnisse in einem 3D-Modell](../designers/media/digit-flat-color-effect.png "Digit-Flat-Color-Effect")  
  
 Bestimmte Formen sorgen vielleicht für bessere Vorschauen für einige Shader. Weitere Informationen zur Verwendung der Vorschau von Shadern im Shader-Designer finden Sie unter [Shader-Designer](../designers/shader-designer.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md)   
 [Shader-Designer](../designers/shader-designer.md)   
 [Shader-Designer-Knoten](../designers/shader-designer-nodes.md)



