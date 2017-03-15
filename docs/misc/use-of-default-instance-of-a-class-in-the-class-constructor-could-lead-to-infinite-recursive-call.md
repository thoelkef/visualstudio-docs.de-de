---
title: "Die Verwendung der Standardinstanz einer Klasse im Klassenkonstruktor kann zu einem unendlichen rekursiven Aufruf f&#252;hren. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Verwendung der Standardinstanz einer Klasse im Klassenkonstruktor kann zu einem unendlichen rekursiven Aufruf f&#252;hren.
Eine Standardinstanz einer Klasse wurde im Konstruktor der Klasse verwendet. Dies kann zu einem unendlichen rekursiven Aufruf, auch bekannt als Endlosschleife, führen.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Standardinstanz aus dem Klassenkonstruktor.  
  
## Siehe auch  
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)