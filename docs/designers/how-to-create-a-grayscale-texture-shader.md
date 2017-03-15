---
title: "Gewusst wie: Erstellen eines Graustufentextur-Shaders | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
caps.latest.revision: 18
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 18
---
# Gewusst wie: Erstellen eines Graustufentextur-Shaders
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dokument wird die Verwendung des Shader\-Designers und der Directed Graph Shader Language \(DGSL\) zur Erstellung eines Graustufen\-Textur\-Shaders veranschaulicht.  Dieser Shader ändert den RGB\-Farbwert des Texturbeispiels und verwendet ihn dann zusammen mit dem unverändertem Alphawert zum Festlegen der endgültigen Farbe.  
  
## Erstellen eines Graustufen\-Textur\-Shaders  
 Sie können einen Graustufen\-Textur\-Shader implementieren, indem Sie den Farbwert eines Texturbeispiels ändern, bevor Sie es in die endgültige Ausgabefarbe schreiben.  
  
 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und der **Werkzeugkasten** angezeigt werden.  
  
#### So erstellen Sie einen Graustufen\-Textur\-Shader  
  
1.  Erstellen Sie einen Basistexturshader, wie in [Gewusst wie: Erstellen eines Basistextur\-Shaders](../designers/how-to-create-a-basic-texture-shader.md) beschrieben.  
  
2.  Trennen Sie das Terminal **RGB** des Knotens **Texturbeispiel** vom Terminal **RGB** des Knotens **Endgültige Farbe**.  Im Modus **Auswählen** wählen Sie das **RGB** Terminal des Knotens **Textursample**, und dann **Zeilen umbrechen** aus.  Dadurch wird Platz für den Knoten geschaffen, der im nächsten Schritt hinzugefügt wird.  
  
3.  Fügen Sie einem Knoten **Entsättigen** Diagramm hinzu.  In **Werkzeugkasten** unter **Filter**, wählen Sie **Entsättigen** aus und verschieben Sie es auf die Entwurfsoberfläche.  
  
4.  Berechnet den Graustufenwert, indem Sie den Knoten **Entsättigen** verwenden.  Im Modus **Auswählen** verschieben Sie das **RGB** Terminal des Knotens **Textursample** auf das Terminal **RGB** des Knotens **Entsättigen**.  
  
    > [!NOTE]
    >  Standardmäßig entsättigt der Knoten **Entsättigen** vollständig die Eingabefarbe und verwendet die Standardleuchtdichtegewichtungen für Graustufenkonvertierung.  Sie können, wie der Knoten **Entsättigen** verhält, indem er den Wert der Eigenschaft **Sättigung** ändert oder, indem Sie nur teilweise die Eingabefarbe ändern entsättigen.  Um die Eingabefarbe teilweise zu entsättigen, erstellen Sie einen Skalarwert im Bereich \[0,1\) zum Terminal **Prozent** des Knotens **Entsättigen** bereit.  
  
5.  Verbinden Sie den Graustufenfarbwert mit der endgültigen Farbe.  Verschieben Sie das **Ausgabe** Terminal des Knotens **Entsättigen** auf das Terminal **RGB** des Knotens **Endgültige Farbe**.  
  
 Die folgende Abbildung zeigt das endgültige Shaderdiagramm und eine Vorschau des auf einen Würfel angewendeten Shaders.  
  
> [!NOTE]
>  In dieser Abbildung ist eine Ebene verwendet, da die Vorschauform und eine Textur angegeben wurde, um die Auswirkungen des Shaders besser zu veranschaulichen.  
  
 ![Shader&#45;Diagramm und eine Vorschau seiner Effekte](../designers/media/digit-grayscale-effect.png "Digit\-Grayscale\-Effect")  
  
 Für einige Shader erzielen Sie mit bestimmte Formen möglicherweise bessere Vorschauen.  Weitere Informationen über die Vorschau von Shadern im Shader\-Designer finden Sie unter [Shader\-Designer](../designers/shader-designer.md)  
  
## Siehe auch  
 [Gewusst wie: Anwenden eines Shaders auf ein 3D\-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Gewusst wie: Exportieren eines Shaders](../designers/how-to-export-a-shader.md)   
 [Grafik\-Editor](../designers/image-editor.md)   
 [Shader\-Designer](../designers/shader-designer.md)   
 [Shader\-Designer\-Knoten](../designers/shader-designer-nodes.md)