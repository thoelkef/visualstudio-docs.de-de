---
title: "Compilerfehler CS1541 | Microsoft Docs"
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
  - "CS1541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1541"
ms.assetid: db3350fe-6432-4617-8b4a-64bc6cdf83f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1541
Ungültige Verweisoption: 'symbol' – auf Verzeichnisse kann nicht verwiesen werden.  
  
 Der Compiler hat einen Versuch erkannt, ein Verzeichnis anstelle einer bestimmten Datei anzugeben. Wenn Sie beispielsweise die Compileroption [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) verwenden, müssen Sie eine Datei angeben; Sie können kein Verzeichnis angeben.  
  
 Beispielsweise führt das Übergeben von `/reference:c:\` zur Generierung von CS1541.