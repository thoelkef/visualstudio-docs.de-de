---
title: "Gewusst wie: Erstellen eines standardm&#228;&#223;igen Farbshaders | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 24
---
# Gewusst wie: Erstellen eines standardm&#228;&#223;igen Farbshaders
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dokument wird die Verwendung des Shader\-Designers und der Directed Graph Shader Language \(DGSL\) zur Erstellung eines einfachen Farb\-Shaders veranschaulicht.  Dieser Shader legt die endgültige Farbe auf einen konstanten RGB\-Farbwert fest.  
  
 In diesem Dokument werden die folgenden Aktivitäten veranschaulicht:  
  
-   Knoten aus einem Diagramm entfernen  
  
-   Knoten einem Diagramm hinzufügen  
  
-   Knoteneigenschaften festlegen  
  
-   Knoten verbinden  
  
## Erstellen eines einfachen Farb\-Shaders  
 Sie können einen einfachen Farb\-Shader implementieren, indem Sie den Farbwert einer RGB\-Farbkonstante in die endgültige Ausgabefarbe schreiben.  
  
 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und der **Werkzeugkasten** angezeigt werden.  
  
#### So erstellen Sie einen einfachen Farb\-Shader  
  
1.  Erstellen Sie einen DGSL\-Shader, mit dem Sie arbeiten können.  Wie Sie dem Projekt einen DGSL\-Shader hinzufügen, erfahren Sie im Abschnitt "Erste Schritte" in [Shader\-Designer](../designers/shader-designer.md).  
  
2.  Löschen Sie den Knoten **Punktfarbe**.  Wählen Sie mit dem Tool **Auswahl** den Knoten **Punktfarbe** aus, und wählen Sie dann in der Menüleiste **Bearbeiten** und anschließend **Löschen** aus.  
  
3.  Fügen Sie dem Diagramm einen Knoten **Farbkonstante** hinzu.  Wählen Sie im **Werkzeugkasten** unter **Konstanten** die Option **Farbkonstante** aus und verschieben Sie den Knoten auf die Entwurfsoberfläche.  
  
4.  Geben Sie für den Knoten **Farbkonstante** einen Farbwert an.  Verwenden Sie das Tool **Auswählen**, um den Knoten **Farbkonstante** auszuwählen. Geben Sie dann im Fenster **Eigenschaften** in der Eigenschaft **Ausgabe** einen Farbwert an.  Geben Sie für Orange einen Wert von \(1,0, 0,5, 0,2, 1,0\) an.  
  
5.  Verbinden Sie die Farbkonstante mit der endgültigen Farbe.  Verschieben Sie zum Erstellen der Verbindungen das **RGB**\-Terminal des Knotens **Farbkonstante** in das **RGB**\-Terminal des Knotens **Endgültige Farbe**, und verschieben Sie das **Alpha**\-Terminal des Knotens **Farbkonstante** anschließend zum **Alpha**\-Terminal des Knotens **Endgültige Farbe**.  Diese Verbindungen legen die endgültige Farbe auf die im vorherigen Schritt definierte Farbkonstante fest.  
  
 Die folgende Abbildung zeigt das endgültige Shaderdiagramm und eine Vorschau des auf einen Würfel angewendeten Shaders.  
  
> [!NOTE]
>  In der Abbildung wurde eine orangefarbene Farbe verwendet, um die Auswirkungen des Shaders besser zu veranschaulichen.  
  
 ![Shader&#45;Diagramm und seine Ergebnisse in einem 3D&#45;Modell](../designers/media/digit-flat-color-effect.png "Digit\-Flat\-Color\-Effect")  
  
 Für einige Shader erzielen Sie mit bestimmte Formen möglicherweise bessere Vorschauen.  Weitere Informationen über die Vorschau von Shadern im Shader\-Designer finden Sie unter [Shader\-Designer](../designers/shader-designer.md)  
  
## Siehe auch  
 [Gewusst wie: Anwenden eines Shaders auf ein 3D\-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Gewusst wie: Exportieren eines Shaders](../designers/how-to-export-a-shader.md)   
 [Shader\-Designer](../designers/shader-designer.md)   
 [Shader\-Designer\-Knoten](../designers/shader-designer-nodes.md)