---
title: 'Vorgehensweise: Modellieren eines 3D-Geländes | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3c9d088be89e2cf963df65a0163713c297615121
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097478"
---
# <a name="how-to-model-3-d-terrain"></a>Vorgehensweise: Modell 3D-Geländes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird gezeigt, wie der Modell-Editor zum Erstellen eines 3D-Geländes verwendet wird.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
- Hinzufügen von Objekten in einer Szene  
  
- Auswählen von Flächen und Punkten  
  
- Übertragen der Auswahl  
  
- Verwenden des Tools **Flächen unterteilen**  
  
- Umrahmen eines Objekt in der Entwurfsoberfläche  
  
## <a name="creating-a-3-d-terrain-model"></a>Erstellen eines 3D-Geländemodells  
 Sie können ein 3D-Gelände erstellen, indem Sie eine Ebene unterteilen, um zusätzliche Flächen zu erstellen und anschließend ihre Schnittpunkte zur Erstellung interessanter Geländefunktionen zu bearbeiten.  
  
 Das Modell sollte dann etwa so aussehen:  
  
 ![3D-Szene zur Darstellung eines Geländemodells](../designers/media/digit-terrain-model.png "Digit-Terrain-Model")  
  
 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.  
  
#### <a name="to-create-a-3-d-terrain-model"></a>So erstellen Sie ein 3D-Geländemodell  
  
1. Erstellen Sie ein 3D-Modell, mit dem Sie arbeiten. Weitere Informationen zum Hinzufügen eines Modells zu Ihren Projekten finden Sie im Abschnitt „Erste Schritte“ unter [Modell-Editor](../designers/model-editor.md).  
  
2. Fügen Sie eine Fläche in die Szene ein. Klicken Sie in der **Toolbox** unter **Formen** auf **Ebene**, und verschieben Sie es auf die Entwurfsoberfläche.  
  
   > [!TIP]
   >  Sie können das Ebenenobjekt auf der Entwurfsoberfläche umrahmen, um damit einfacher arbeiten zu können. Klicken Sie im Modus **Auswählen** auf das Ebenenobjekt und anschließend auf der Symbolleiste des Modell-Editors auf die Schaltfläche **Rahmenobjekt**  
  
3. Gehen Sie in den Flächenauswahlmodus. Wählen Sie auf der Symbolleiste des Modell-Editors **Fläche auswählen** aus.  
  
4. Unterteilen Sie die Ebene. Klicken Sie im Flächenauswahlmodus die Ebene einmal an, um sie auswählen zu können. Klicken Sie anschließend auf die Oberfläche der Ebene, um ihre einzige Fläche auszuwählen. Klicken Sie auf der Symbolleiste des Modell-Editors auf **Fläche unterteilen**. Dadurch werden neue Schnittpunkte auf der Oberfläche der Ebene hinzugefügt, die sie in vier gleichgroße Teile aufteilen.  
  
5. Erstellen Sie weitere Unterteilungen. Klicken Sie zweimal auf **Fläche unterteilen**, während die neuen Flächen noch ausgewählt sind. Dadurch werden insgesamt 64 Flächen erstellt. Sie können dem Gelände sogar noch mehr Details verleihen, indem Sie mehr Unterteilungen erstellen.  
  
6. Gehen Sie in den Punktauswahlmodus. Wählen Sie auf der Symbolleiste des Modell-Editors **Punkt auswählen** aus.  
  
7. Ändern Sie einen Punkt, um eine Geländefunktion zu erstellen. Klicken Sie im Punktauswahlmodus auf einen der Punkte und wählen Sie anschließend auf der Symbolleiste des Modell-Editors das Tool **Übertragen** aus. Ein Feld, das den Punkt darstellt, wird auf der Entwurfsoberfläche angezeigt. Verwenden Sie den grünen Pfeil, um das Feld zu verschieben, wodurch die Punkthöhe verändert wird. Wiederholen Sie diesen Schritt für verschiedene Punkte, um interessante Geländefunktionen zu erstellen.  
  
   > [!TIP]
   >  Sie können mehrere Punkte gleichzeitig auswählen, um sie auf einmal zu bearbeiten.  
  
   Das Geländemodell ist fertig. Hier ist noch einmal das fertige Modell, bei dem eine Phong-Schattierung angewandt wurde.  
  
   ![3D-Szene zur Darstellung eines Geländemodells](../designers/media/digit-terrain-model.png "Digit-Terrain-Model")  
  
   Sie können dieses Geländemodell zur Veranschaulichung des Effekts des Farbverlauf-Shaders verwenden, das unter [Vorgehensweise: Erstellen eines Geometriebasierten Farbverlauf-Shaders](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Modell-Editor](../designers/model-editor.md)
