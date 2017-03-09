---
title: "Compilerfehler CS2033 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2033"
ms.assetid: edb5784a-5195-4f72-b73d-d1ec9ed3766e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS2033
Der kurze Dateiname 'Dateiname' kann nicht erstellt werden, wenn bereits ein langer Dateiname mit dem gleichen kurzen Dateinamen vorhanden ist.  
  
 Kompilieren Sie eine beliebige C\#\-Datei mit einem Namen, der länger als acht Zeichen ist. Kompilieren Sie dann eine andere Datei mit der Kurzversion des vorhergehenden Dateinamens, z. B. die ersten sechs Zeichen des Namens plus „~1“. Dieser Fehler wird beim zweiten Kompilierungsvorgang generiert.  
  
 Benennen Sie den kurzen Dateinamen in einen Namen um, der mit dem langen Dateinamen nicht im Konflikt steht, um diesen Fehler zu beheben.