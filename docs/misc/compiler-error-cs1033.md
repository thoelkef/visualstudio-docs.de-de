---
title: "Compilerfehler CS1033 | Microsoft Docs"
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
  - "CS1033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1033"
ms.assetid: eb0f4001-84a6-4918-a648-cf710d038de7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1033
Die Quelldatei hat das Limit von 16.707.565 Zeilen überschritten, die in der PDB dargestellt werden können. Die Debuginformationen sind falsch.  
  
 Eine Quellcodedatei hat die maximal zulässige Anzahl von Zeilen überschritten, die der Compiler verarbeiten kann. Erstellen Sie zwei oder mehr Quellcodedateien aus der ursprünglichen Datei, um diesen Fehler zu beheben. Die maximale Anzahl von Zeilen beträgt 268.435.454. Wenn Sie **\/debug** verwenden, führt die Verwendung von mehr als 16.707.566 Zeilen zu beschädigten Debuginformationen.