---
title: 'Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a55c1e71242e59c04066c09efa2375c4bafc485b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156317"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird gezeigt, wie der Modell-Editor verwendet wird, um einen Directed Graph Shader Language (DGSL)-Shader auf ein 3-D-Modell anzuwenden.  
  
 In diesem Dokument wird die folgende Aktivität veranschaulicht:  
  
- Anwenden eines Shaders auf ein 3D-Modell  
  
## <a name="applying-a-shader-to-a-3-d-model"></a>Anwenden eines Shaders auf ein 3D-Modell  
 Sie können einen Shadereffekt auf ein 3D-Modell anwenden, um ihm ein interessantes Aussehen zu verleihen.  
  
 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** angezeigt wird.  
  
#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Anwenden eines Shaders auf ein 3D-Modell  
  
1. Beginnen Sie mit einer 3D-Szene, die ein oder mehrere Modelle enthält. Wenn Sie keine geeignete 3D-Szene haben, erstellen Sie eine wie in beschrieben [Vorgehensweise: Erstellen ein 3D-Basismodells](../designers/how-to-create-a-basic-3-d-model.md). Sie müssen ebenso über einen DGSL-Shader verfügen, den Sie auf das Modell anwenden können. Wenn kein geeigneter Shader vorhanden ist, erstellen Sie einen wie unter [Vorgehensweise: Erstellen eines standardmäßigen Farbshaders](../designers/how-to-create-a-basic-color-shader.md) und stellen Sie sicher, dass Sie es in einer Datei gespeichert haben, bevor Sie fortfahren.  
  
2. Wählen Sie das Modell, auf das Sie den Shader anwenden möchten, im Modus **Auswählen** aus. Anschließend legen Sie im Fenster **Eigenschaften** unter der Eigenschaft **Dateiname** in der Eigenschaftsgruppe **Effekt** den DGSL-Shader fest, den Sie auf das Modell anwenden möchten.  
  
   Hier finden Sie ein Modell, bei dem der grundlegende Farbeffekt angewendet wurde:  
  
   ![3D-Szene zur Darstellung des grundlegenden Farbeffekts](../designers/media/digit-3d-model-effect.png "Digit-3D-Modelleffekt")  
  
   Nachdem Sie einen Shader auf ein Modell angewendet haben, können Sie es im Shader-Designer durch Auswählen des Modells öffnen und anschließend die Schaltfläche „Ellipse“ ( **...** ) im Fenster **Eigenschaften** unter der Eigenschaft **(Erweitert)** der Eigenschaftsgruppe **Effekt** auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen eines 3D-Basismodells](../designers/how-to-create-a-basic-3-d-model.md)   
 [Vorgehensweise: Erstellen eines standardmäßigen Farbshaders](../designers/how-to-create-a-basic-color-shader.md)   
 [Modell-Editor](../designers/model-editor.md)   
 [Shader-Designer](../designers/shader-designer.md)
