---
title: "Compilerfehler CS2020 | Microsoft Docs"
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
  - "CS2020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2020"
ms.assetid: b2db7a05-5965-4a9b-86c3-0c4792b29a6c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS2020
Nur die erste Gruppe von Eingabedateien kann ein anderes Ziel als 'module' erstellen.  
  
 Bei einer Kompilierung mit mehreren Ausgabedateien muss die erste Ausgabedatei mit [\/target:exe](../Topic/-target:exe%20\(C%23%20Compiler%20Options\).md), [\/target:winexe](../Topic/-target:winexe%20\(C%23%20Compiler%20Options\).md) oder [\/target:library](../Topic/-target:library%20\(C%23%20Compiler%20Options\).md) erstellt werden. Alle nachfolgenden Ausgabedateien müssen mit [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) erstellt werden.