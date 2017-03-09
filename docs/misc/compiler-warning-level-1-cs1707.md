---
title: "Compilerwarnung (Stufe 1) CS1707 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1707"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1707"
ms.assetid: 47b6096e-4e4b-4057-b9d7-4a096139267a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1707
Der Delegat "Delegatname" wird wegen neuer Sprachregeln an "Methodenname1" statt an "Methodenname2" gebunden.  
  
 Mit C\# 2.0 werden neue Regeln zum Binden eines Delegaten an eine Methode implementiert. Weitere Informationen werden berücksichtigt, die in der Vergangenheit nicht betrachtet wurden. Diese Warnung gibt an, dass der Delegat jetzt an eine andere Überladung der Methode als bisher gebunden wurde. Sie möchten möglicherweise sicherstellen, dass der Delegat tatsächlich an "Methodenname1" und nicht an "Methodenname2" gebunden werden soll.  
  
 Wie der Compiler die Methode zum Binden eines Delegaten bestimmt, ist ausführlich unter [Verwenden von Varianz bei Delegaten](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md) beschrieben.