---
title: "Compilerfehler CS0003 | Microsoft Docs"
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
  - "CS0003"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0003"
ms.assetid: 6aee4b0e-e24f-47b5-8281-ca4c7ee8a3cf
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0003
Nicht genügend Arbeitsspeicher.  
  
 Der Compiler konnte nicht genügend virtuellen Arbeitsspeicher zuweisen, um die Kompilierung abzuschließen. Schließen Sie alle nicht benötigten Programme, und kompilieren Sie erneut.  
  
 Sie sollten auch die Auslagerungsdatei vergrößern und sicherstellen, dass genügend freier Speicher auf dem Datenträger verfügbar ist.  
  
 Dieser Fehler kann auch auftreten, wenn die Versionen von [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] und C\#\-Compiler nicht übereinstimmen oder mindestens eine Datei, die den C\#\-Compiler unterstützt, beschädigt ist. Installieren Sie Visual Studio erneut.