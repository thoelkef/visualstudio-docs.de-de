---
title: "Gewusst wie: Erstellen in einem allgemeinen Ausgabeverzeichnis | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Builds [Visual Studio], Gemeinsames Verzeichnis"
  - "Gemeinsames Verzeichnis"
  - "Ausgabeverzeichnis"
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen in einem allgemeinen Ausgabeverzeichnis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird jedes Projekt standardmäßig in einer Lösung erstellt, die sich in einem eigenen Ordner innerhalb der Lösung befindet.  Sie können die Buildausgabepfade der Projekte ändern, um zu erzwingen, dass alle Ausgaben im selben Ordner abgelegt werden.  
  
### So fügen Sie alle Projektmappenausgaben in ein gemeinsames Verzeichnis ein  
  
1.  Klicken Sie in der Projektmappe auf ein Projekt.  
  
2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
3.  Klicken Sie je nach Projekttyp entweder auf die Registerkarte **Kompilieren** oder **Erstellen**, und legen Sie den **Ausgabepfad** zu einem Ordner fest, der für alle in der Projektmappe enthaltenen Projekte verwendet werden soll.  
  
4.  Wiederholen Sie die Schritte 1\-3 für alle Projekte in der Projektmappe.  
  
## Siehe auch  
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)   
 [Gewusst wie: Ändern des Buildausgabeverzeichnisses](../ide/how-to-change-the-build-output-directory.md)