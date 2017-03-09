---
title: "Compilerwarnung (Stufe 1) CS1697 | Microsoft Docs"
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
  - "CS1697"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1697"
ms.assetid: 0cd931b7-f358-4ff0-b441-27668645d7d5
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1697
Für "file name" wurden verschiedene Prüfsummenwerte angegeben  
  
 Sie haben mehr als eine Prüfsumme für eine bestimmte Datei angegeben. Der Debugger verwendet den Prüfsummenwert, um zu bestimmen, welche Datei zu debuggen ist, wenn mehr als eine Datei in einem Projekt mit dem gleichen Namen vorhanden ist. Die meisten Benutzer sehen diesen Fehler nicht; aber wenn Sie eine Anwendung schreiben, die Code generiert, wird er möglicherweise angezeigt. Um diesen Fehler zu beheben, stellen Sie sicher, dass Sie die Prüfsumme nur einmal für jede Codedatei generieren.