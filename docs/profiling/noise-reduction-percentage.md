---
title: "Prozentsatz der Rauschunterdr&#252;ckung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.filter"
helpviewer_keywords: 
  - "Parallelitätsschnellansicht, Prozentsatz der Rauschunterdrückung"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Prozentsatz der Rauschunterdr&#252;ckung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Standardmäßig beträgt der prozentuale Wert für die Rauschunterdrückungseinstellung 2.  Nur Einträge mit einem Prozentsatz der inklusiven Zeit, der größer oder gleich dieser Einstellung ist, werden in der Aufrufstruktur angezeigt.  Durch Ändern der Einstellung können Sie die Anzahl von Einträgen steuern, die in der Aufrufstruktur angezeigt werden.  Wenn Sie zum Beispiel den Wert in 10 ändern, werden nur Aufrufstruktureinträge mit einer inklusiven Zeit größer oder gleich 10 % angezeigt.  Wenn Sie den Wert der Einstellung vergrößern, können Sie sich auf Einträge konzentrieren, die größere Auswirkungen auf die Leistung des Prozesses haben.