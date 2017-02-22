---
title: "Gewusst wie: Modellieren eines 3D-Gel&#228;ndes | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 17
caps.handback.revision: 17
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Gewusst wie: Modellieren eines 3D-Gel&#228;ndes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dokument veranschaulicht, wie Sie den Modell\-Editor verwenden, um ein 3D\-Geländemodell zu erstellen.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Hinzufügen von Objekten zu einer Szene  
  
-   Auswählen vonseiten und Punkten  
  
-   Übersetzung der Auswahl  
  
-   Verwenden des Tools **Unterteilen Sie eine Fläche**  
  
-   Framing eines Objekts auf der Entwurfsoberfläche  
  
## Erstellen eines 3D\-Geländemodells  
 Sie können ein 3D\-Gelände erstellen, indem Sie eine Ebene unterteilen, um zusätzliche Seiten zu erhalten. Dann ändern Sie deren Vertices, um interessante Geländefunktionen zu erstellen.  
  
 Wenn Sie fertig sind, sollte das Modell wie folgt aussehen:  
  
 ![3D&#45;Szene zur Darstellung eines Geländemodells](../designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 Bevor Sie beginnen, sicher, dass das Fenster **Eigenschaften** und **Werkzeugkasten** angezeigt werden.  
  
#### So erstellen Sie ein 3D\-Geländemodell  
  
1.  Erstellen Sie ein 3D\-Modell, mit denen Sie arbeiten.  Informationen darüber, wie ein Modell dem Projekt, finden Sie im Abschnitt Erste Schritte in [Modell\-Editor](../designers/model-editor.md).  
  
2.  Fügen Sie der Szene eine Ebene hinzu.  Wählen Sie im **Werkzeugkasten** unter **Formen** die Option **Ebene** aus, und verschieben Sie sie auf die Entwurfsoberfläche.  
  
    > [!TIP]
    >  Um das flache Objekt zu erleichtern mit zu arbeiten, können Sie es auf der Entwurfsoberfläche\) umgeben.  In Modus **Auswählen** das Ebenenobjekt dann auf der Modell\-Editor\-Symbolleiste, die Schaltfläche **Rahmenobjekt** aus.  
  
3.  Geben Sie Flächenauswahlmodus ein.  Auf der Modell\-Editor\-Symbolleiste wählen Sie **Seite auswählen** aus.  
  
4.  Unterteilen Sie die Ebene.  im Flächenauswahlmodus wählen Sie die Ebene, um sie einmal für Auswahl zu aktivieren, und wählen Sie sie dann wieder, seine nur Fläche auszuwählen.  Auf der Modell\-Editor\-Symbolleiste wählen Sie **Unterteilen Sie eine Fläche** aus.  Dies fügt neuen Schnittpunkte der Ebene hinzu, die es in vier gleichmäßig skalierte Partitionen Unterteilung.  
  
5.  Erstellen Sie weitere Unterteilungen.  Wenn die neuen Flächen weiterhin ausgewählt sind, wählen Sie zwei weitere Male **Unterteilen Sie eine Fläche** aus.  Dadurch werden insgesamt 64 Seiten erstellt.  Wenn Sie weitere Unterteilungen erstellen, können Sie das Gelände noch detaillierter darstellen.  
  
6.  Geben Sie Punktauswahlmodus ein.  Auf der Modell\-Editor\-Symbolleiste wählen Sie **Punkt auswählen** aus.  
  
7.  Ändern Sie einen Punkt, um eine Geländefunktion zu erstellen.  Im Punktauswahlmodus wählen Sie einen der Punkte und dann auf der Modell\-Editor\-Symbolleiste, das Tool **Verschieben** aus.  Auf der Entwurfsoberfläche wird ein Feld angezeigt, das den Punkt darstellt.  Verwenden Sie den grünen Pfeil, um das Feld zu verschieben und so die Höhe des Punkts zu ändern.  Wiederholen Sie diesen Schritt für verschiedene Punkte, um interessante Geländefunktionen zu erstellen.  
  
    > [!TIP]
    >  Sie können auch mehrere Punkte gleichzeitig auswählen, um sie in einer einheitlichen Weise zu ändern.  
  
 Das Geländemodell ist vollständig.  Es folgt das endgültige Modell erneut, wenn Phong\-Schattierung angewendet ist:  
  
 ![3D&#45;Szene zur Darstellung eines Geländemodells](../designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 Sie können dieses Geländemodell verwenden, um die Auswirkungen des Farbverlauf\-Shaders zu veranschaulichen, der unter [Gewusst wie: Erstellen eines geometriebasierten Farbverlauf\-Shaders](../designers/how-to-create-a-geometry-based-gradient-shader.md) beschrieben wird.  
  
## Siehe auch  
 [Modell\-Editor](../designers/model-editor.md)