---
title: 'Vorgehensweise: Erstellen eines 3D-Basismodells | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf8180f13328c198131ee3d5fca3884dcd20be2c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511508"
---
# <a name="how-to-create-a-basic-3-d-model"></a>Gewusst wie: Erstellen eines 3D-Basismodells
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: erstellen ein 3D-Basismodells](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-3-d-model).  
  
In diesem Dokument wird gezeigt, wie der Modell-Editor zum Erstellen eines 3D-Basismodells verwendet wird.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Hinzufügen von Objekten in einer Szene  
  
-   Flächen und Kanten auswählen  
  
-   Übertragen der Auswahl  
  
-   Verwenden der Tools **Unterteilen von Flächen** und **Extrudieren von Flächen**  
  
-   Verwenden des Befehls **Triangulieren**  
  
## <a name="creating-a-basic-3-d-model"></a>Erstellen eines 3D-Basismodells  
 Sie können den Modell-Editor zum Erstellen und Ändern von 3D-Modellen und -Szenen für Ihre Spiele und Apps verwenden. Die folgenden Schritte zeigen, wie Sie den Modell-Editor verwenden, um ein vereinfachtes 3D-Modell eines Hauses zu erstellen. Ein vereinfachtes Modell kann als Ersatz für die endgültigen Grafikobjekte verwendet werden, die noch erstellt werden. Es dient als ein Gitter zur Kollisionserkennung oder als ein Modell mit niedrigen Details, das verwendet wird, wenn ein Objekt, das es darstellt, zu weit weg ist, um von detaillierterem Rendering zu profitieren.  
  
 Das Modell sollte dann etwa so aussehen:  
  
 ![Das fertige Modell des vereinfachten Hauses](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>So erstellen Sie ein vereinfachtes 3D-Modell eines Hauses  
  
1.  Erstellen Sie ein 3D-Modell, mit dem Sie arbeiten. Weitere Informationen zum Hinzufügen eines Modells zu Ihren Projekten finden Sie im Abschnitt „Erste Schritte“ unter [Modell-Editor](../designers/model-editor.md).  
  
2.  Fügen Sie einen Würfel in die Szene ein. Wählen Sie im Fenster **Toolbox** unter **Formen** **Würfel** aus und verschieben Sie ihn auf die Entwurfsoberfläche.  
  
3.  Wechseln Sie zur Flächenauswahl. Klicken Sie auf der Symbolleiste des Modell-Editors auf **Fläche auswählen**.  
  
4.  Unterteilen Sie die Oberseite des Würfels. Klicken Sie im Flächenauswahlmodus den Würfel einmal an, um ihn auswählen zu können. Klicken Sie anschließend auf die Oberfläche des Würfels, um die Anfangsfläche auszuwählen. Klicken Sie auf der Symbolleiste des Modell-Editors auf **Fläche unterteilen**. Dadurch werden neue Schnittpunkte auf der Oberfläche des Würfels hinzugefügt, die ihn in vier gleichgroße Teile aufteilen.  
  
     ![Die Oberseite des Würfels wurde unterteilt](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")  
  
5.  Extrudieren Sie zwei angrenzende Seiten des Würfels, z.B. die Vorderseite und die rechte Seite. Klicken Sie im Flächenauswahlmodus den Würfel einmal an, um ihn zu aktivieren, und klicken Sie anschließend auf eine Seite des Würfels. Drücken und halten Sie die STRG-Taste gedrückt, klicken Sie auf eine andere Seite des Würfels, die an der zuerst ausgewählten Seite angrenzt, und klicken anschließend auf der Symbolleiste des Editors auf **Fläche extrudieren**.  
  
     ![Die Würfelseiten wurden extrudiert ](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")  
  
6.  Erweitern Sie eine der Extrusionen. Wählen Sie eine der Flächen aus, die sie gerade extrudiert haben, und klicken in der Symbolleiste des Modell-Editors anschließend auf das Tool **Verschieben**. Bewegen Sie den Verschiebungsmanipulator in die gleiche Richtung wie die Extrusion.  
  
     ![Eine Würfelseite wurde noch weiter extrudiert](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")  
  
7.  Triangulieren Sie das Modell. Klicken Sie auf der Symbolleiste des Modell-Editors auf **Erweitert** > **Tools** > **Triangulieren**.  
  
8.  Erstellen Sie das Dach des Hauses. Wechseln Sie zum Kantenauswahlmodus, indem Sie auf der Symbolleiste des Modell-Editors auf **Kante auswählen** klicken. Klicken Sie anschließend auf den Würfel, um ihn zu aktivieren. Halten Sie die STRG-Taste gedrückt, während Sie die Kanten auswählen, die hier gezeigt werden:  
  
     ![Die Kanten, die die Dachspitze bilden werden](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")  
  
     Nachdem die Kanten ausgewählt sind klicken sie auf der Symbolleiste des Modell-Editors auf **Verschieben** und bewegen Sie den Verschiebungsmanipulator nach oben, um das Dach des Hauses zu erstellen.  
  
 Das Modell des vereinfachten Hauses ist abgeschlossen. Hier ist noch einmal das fertige Modell, bei dem eine flache Schattierung angewandt wurde.  
  
 ![Das fertige Modell des vereinfachten Hauses](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")  
  
 Im nächsten Schritt können Sie einen Shader auf diese 3D-Modell anwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Modellieren eines 3D-Geländes](../designers/how-to-model-3-d-terrain.md)   
 [Modell-Editor](../designers/model-editor.md)   
 [Shader-Designer](../designers/shader-designer.md)



