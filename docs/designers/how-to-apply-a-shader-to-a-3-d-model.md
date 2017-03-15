---
title: "Gewusst wie: Anwenden eines Shaders auf ein 3D-Modell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 15
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 15
---
# Gewusst wie: Anwenden eines Shaders auf ein 3D-Modell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dokument veranschaulicht, wie der Modell\-Editor verwendet, um einen Shader\-Sprachen \(dgsl\)\- Shader eines gerichteten Diagramms auf ein 3D\-Modell anzuwenden.  
  
 In diesem Dokument wird die folgende Aktivität veranschaulicht:  
  
-   Anwenden eines Shaders auf ein 3D\-Modell  
  
## Anwenden eines Shaders auf ein 3D\-Modell  
 Sie können einen Shadereffekt auf ein 3D\-Modell anwenden, um ihm eine interessanteres Aussehen zu verleihen.  
  
 Bevor Sie beginnen, sicher, dass das Fenster **Eigenschaften** angezeigt wird.  
  
#### So wenden Sie einen Shader auf ein 3D\-Modell an  
  
1.  Beginnen Sie mit einer 3D\-Szene, die eine oder mehrere Modelle enthält.  Wenn Sie keine geeignete 3D\-Szene haben, erstellen Sie ein, wie in [Gewusst wie: Erstellen eines 3D\-Basismodells](../designers/how-to-create-a-basic-3-d-model.md) beschrieben.  Sie müssen einen DGSL\-Shader verfügen, der auf das Modell anwenden können.  Wenn Sie keine geeignete Shader verfügen, erstellen Sie ein, wie in [Gewusst wie: Erstellen eines standardmäßigen Farbshaders](../designers/how-to-create-a-basic-color-shader.md) beschrieben und überprüfen Sie, ob Sie es in einer Datei gespeichert haben, bevor Sie fortfahren.  
  
2.  Im Modus **Auswählen** wählen Sie das Modell aus, dass Sie den Shader anwenden möchten, und dann im Fenster **Eigenschaften**, in der Eigenschaft **Filename** der Eigenschaftengruppe **Effekt**, geben Sie den DGSL\-Shader, den Sie auf das Modell anwenden möchten.  
  
 Im Folgenden ein Modell, das den grundlegenden Farbeneffekt verfügt, der angewendet wird:  
  
 ![3D&#45;Szene zur Darstellung des grundlegenden Farbeffekts](../designers/media/digit-3d-model-effect.png "Digit\-3D\-Model\-Effect")  
  
 Nachdem Sie einen Shader auf ein Modell anwenden, können Sie es im Shader\-Designer, indem Sie das Modell öffnen, und wählen im Fenster **Eigenschaften**, in der Eigenschaft **\(Erweitert\)** der Eigenschaftengruppe **Effekt** und die Schaltfläche mit den Auslassungspunkten \(**...**\) klicken.  
  
## Siehe auch  
 [Gewusst wie: Erstellen eines 3D\-Basismodells](../designers/how-to-create-a-basic-3-d-model.md)   
 [Gewusst wie: Erstellen eines standardmäßigen Farbshaders](../designers/how-to-create-a-basic-color-shader.md)   
 [Modell\-Editor](../designers/model-editor.md)   
 [Shader\-Designer](../designers/shader-designer.md)