---
title: "Gewusst wie: Erstellen eines 3D-Basismodells | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 18
caps.handback.revision: 18
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Gewusst wie: Erstellen eines 3D-Basismodells
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dokument veranschaulicht, wie Sie den Modell\-Editor verwenden, um ein einfaches 3D\-Modell zu erstellen.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Hinzufügen von Objekten zu einer Szene  
  
-   Auswählen vonseiten und von Rändern  
  
-   Übersetzung der Auswahl  
  
-   Verwenden der **Unterteilen Sie eine Fläche** und der **Extrudieren Sie eine Fläche** Tools  
  
-   Verwenden des Befehls **Triangulieren**  
  
## Erstellen eines einfachen 3D\-Modells  
 Sie können den Modell\-Editor verwenden, um 3D\-Modelle und \-szenen für Ihr Spiel oder Ihre App erstellen und zu ändern.  Die folgenden Schritte zeigen, wie der Modell\-Editor verwendet, um ein einfaches 3D\-Modell eines Hauses zu erstellen.  Ein einfaches Modell kann als Ressourcen endgültige Grafiken des Ersetzung verwendet werden, die noch, Gitter als für Kollisionserkennung oder als verwendet werden LOWDetailerstellt werden, Modell, wenn das Objekt, das es darstellt, zu weit weg ist, von ausführlicherem Rendering zu profitieren.  
  
 Wenn Sie fertig sind, sollte das Modell wie folgt aussehen:  
  
 ![Das abgeschlossene Modell des vereinfachten Hauses](../designers/media/gfx_model_demo_house_final.png "gfx\_model\_demo\_house\_final")  
  
 Bevor Sie beginnen, sicher, dass das Fenster **Eigenschaften** und **Werkzeugkasten** angezeigt werden.  
  
#### So ein vereinfachtes 3D\-Modell eines Hauses erstellen  
  
1.  Erstellen Sie ein 3D\-Modell, mit denen Sie arbeiten.  Informationen darüber, wie ein Modell dem Projekt, finden Sie im Abschnitt Erste Schritte in [Modell\-Editor](../designers/model-editor.md).  
  
2.  Fügen Sie einem Cube der Szene hinzugefügt.  Im Fenster **Werkzeugkasten** unter **Formen**, wählen Sie **Würfel** aus und verschieben Sie ihn auf die Entwurfsoberfläche.  
  
3.  Wechseln Sie zur FlächeAuswahl.  Auf der Modell\-Editor\-Symbolleiste wählen Sie **Seite auswählen** aus.  
  
4.  Unterteilen Sie den Anfang des Cubes.  im Flächenauswahlmodus wählen Sie den Cube einmal, um ihn für Auswahl zu aktivieren, und dann die Spitze des Cubes, um die oben auswählen.  Auf der Modell\-Editor\-Symbolleiste wählen Sie **Unterteilen Sie eine Fläche** aus.  Dies fügt neuen Schnittpunkte Anfang des Cubes hinzu, der es in vier gleichmäßig skalierte Partitionen Unterteilung.  
  
     ![Die Oberseite des Würfels wurde unterteilt](../designers/media/gfx_model_demo_house_subdiv.png "gfx\_model\_demo\_house\_subdiv")  
  
5.  Verdrängen zwei angrenzende Seiten von Cube – z. B. die Vorder\- und rechten Seite des Cubes.  im Flächenauswahlmodus wählen Sie den Cube einmal, um ihn für Auswahl zu aktivieren und eine Seite des Würfels aus.  Halten Sie STRG an, wählen Sie eine andere Seite des Würfels aus, der neben der Seite, die Sie anfänglich ausgewählt und dann auf der Modell\-Editor\-Symbolleiste ist, **Extrudieren Sie eine Fläche** auswählen.  
  
     ![Die Seiten des Würfels wurden extrudiert](../designers/media/gfx_model_demo_house_extrude.png "gfx\_model\_demo\_house\_extrude")  
  
6.  Erweitern einer der Extrusionen.  Wählen Sie eine der Seiten, die Sie gerade verdrängten, und dann, auf der Modell\-Editor\-Symbolleiste, das Tool **Verschieben** und verschieben den Übersetzungsmanipulator in derselben Richtung wie die Extrusion aus.  
  
     ![Eine Seite des Würfels wurde noch weiter extrudiert.](../designers/media/gfx_model_demo_house_extend.png "gfx\_model\_demo\_house\_extend")  
  
7.  Triangulate das Modell.  Auf der Modell\-Editor\-Symbolleiste, wählen Sie **Tools**, **TriangulierenErweitert** aus.  
  
8.  Erstellen Sie das Dach des Hauses erstellt.  In den RandAuswahlmodus, indem er auf der Modell\-Editor\-Symbolleiste **Kante auswählen** auswählt, und anschließend auswählen den Cube, um es zu aktivieren.  Halten Sie STRG an, wie Sie die Ränder auswählen, die hier angezeigt:  
  
     ![Die Kanten, die die Spitze des Dachs bilden sollen](../designers/media/gfx_model_demo_house_edges.png "gfx\_model\_demo\_house\_edges")  
  
     Wenn die Breite, auf der Modell\-Editor\-Symbolleiste ausgewählt sind, wählen Sie das Tool **Verschieben** aus und verschieben Sie dann den Übersetzungsmanipulator nach oben, um das Dach des Hauses zu erstellen.  
  
 Das vereinfacht Hausmodell ist vollständig.  Es folgt das endgültige Modell erneut, wenn die flache Schattierung angewendet ist:  
  
 ![Das abgeschlossene Modell des vereinfachten Hauses](../designers/media/gfx_model_demo_house_final.png "gfx\_model\_demo\_house\_final")  
  
 Als nächster Schritt können Sie einen Shader auf das 3D\-Modell anwenden.  Weitere Informationen finden Sie unter [Gewusst wie: Anwenden eines Shaders auf ein 3D\-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## Siehe auch  
 [Gewusst wie: Modellieren eines 3D\-Geländes](../designers/how-to-model-3-d-terrain.md)   
 [Modell\-Editor](../designers/model-editor.md)   
 [Shader\-Designer](../designers/shader-designer.md)