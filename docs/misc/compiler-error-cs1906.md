---
title: "Compilerfehler CS1906 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1906"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1906"
ms.assetid: 1a6abf5c-f673-4256-93ac-313dce50acc0
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1906
Ungültige Option "Option"; Ressourcensichtbarkeit muss entweder "public" oder "private" sein.  
  
 Dieser Fehler kennzeichnet eine ungültige [\/resource \(Ressourcendatei in Ausgabe einbetten\)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)\- oder [\/linkresource \(mit .NET Framework\-Ressource verknüpfen\)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option)\-Befehlszeilenoption. Überprüfen Sie die Syntax der **\/resource**\- oder **\/linkresource**\-Befehlszeilenoption, und stellen Sie sicher, dass der verwendete Zugriffsmodifizierer entweder **public** oder `private` ist.