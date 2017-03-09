---
title: "Compilerfehler CS0040 | Microsoft Docs"
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
  - "CS0040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0040"
ms.assetid: 6a600166-0335-4b6d-b050-6821b4624c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0040
Unerwarteter Fehler beim Erstellen der Debuginformationsdatei – "Ursache"  
  
 Dieser Fehler kann bei Verwendung der Compileroption [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) auftreten und gibt an, dass der Compiler nicht in die PDB\-Datei schreiben konnte. Mögliche Lösungen für dieses Problem: Installieren Sie Visual Studio neu, und stellen Sie sicher, dass der Compiler Schreibzugriff auf eine Datei oder ein Verzeichnis hat, oder kompilieren Sie ohne die Option "\/debug".