---
title: "Gewusst wie: &#196;ndern des Pivotpunkts eines 3D-Modells | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 14
caps.handback.revision: 14
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Gewusst wie: &#196;ndern des Pivotpunkts eines 3D-Modells
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dokument veranschaulicht, wie der Modell\-Editor verwendet, um den *Pivotpunkt* eines 3D\-Modells zu ändern.  Der Pivotpunkt ist der Punkt im Raum, der den mathematischen Mittelpunkt des Objekts für Drehung und Skalierung definiert.  
  
 In diesem Dokument wird die folgende Aktivität veranschaulicht:  
  
-   Ändern des Pivotpunkts eines Objekts  
  
## Ändern des Pivotpunkts eines 3D\-Modells  
 Sie können den Ursprung eines 3D\-Modells neu definieren, indem Sie den Pivotpunkt des Objekts ändern.  
  
 Stellen Sie sicher, dass das Fenster **Eigenschaften** und der **Werkzeugkasten** angezeigt werden.  
  
#### Um den Pivotpunkt von 3D\-Objekten zu ändern Sie  
  
1.  Beginnen Sie mit einem vorhandenen 3D\-Modell, wie z. B. demjenigen, das in [Gewusst wie: Erstellen eines 3D\-Basismodells](../designers/how-to-create-a-basic-3-d-model.md) beschrieben wird.  
  
2.  Aktivieren Sie den Pivot\-Modus.  Klicken Sie auf der Symbolleiste **Modell\-Editor\-Modus** wählen Sie die Schaltfläche **Pivot\-Modus**, um den Pivot\-Modus zu aktivieren.  Ein Rahmen wird um die Schaltfläche **Pivot\-Modus**, anzugeben, dass der Modell\-Editor jetzt im Pivot\-Modus befindet.  Im Pivot\-Modus beeinflussen Vorgänge wie die Übersetzung den Pivotpunkt des Objekts und nicht die Struktur des Objekts im Raum.  
  
3.  Ändern Sie den Pivotpunkt des Objekts.  Wählen Sie im Modus **Auswählen** das Objekt aus, und wählen Sie dann auf der Symbolleiste **Model Viewer** das Tool **Verschieben** aus.  Auf der Entwurfsoberfläche wird ein Feld angezeigt, das den Pivotpunkt darstellt.  Verschieben Sie das Feld, um den Pivotpunkt des Objekts zu ändern.  
  
     Durch Verschieben des Felds können Sie den Pivotpunkt in alle drei Richtungen verschieben.  Um den Pivotpunkt entlang einer Achse zu verschieben, bewegen Sie den Pfeil, der dieser Achse entspricht.  Das Feld und die Pfeile werden gelb, um die Achse anzugeben, die von der Verschiebung betroffen ist.  
  
     Sie können den Pivotpunkt auch angeben, indem Sie die Eigenschaft **Pivot\-Übersetzung** im Fenster **Eigenschaften** verwenden.  
  
    > [!TIP]
    >  Sie können die Auswirkungen des neuen Pivotpunkts anzeigen, indem Sie das Objekt drehen.  Verwenden Sie zum Drehen das Tool **Drehen**, oder ändern Sie die Eigenschaft **Drehung**.  
  
 Im Folgenden ein Modell, das einen geänderten Pivotpunkt verfügt:  
  
 ![Modell eines Hauses mit einem geänderten Pivotpunkt](../designers/media/digit-modified-model.png "Digit\-Modified\-Model")  
  
## Siehe auch  
 [Gewusst wie: Erstellen eines 3D\-Basismodells](../designers/how-to-create-a-basic-3-d-model.md)   
 [Modell\-Editor](../designers/model-editor.md)