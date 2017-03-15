---
title: "Compilerfehler CS2021 | Microsoft Docs"
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
  - "CS2021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2021"
ms.assetid: 8379d77e-6586-4e43-9aab-7cdf3ffecf51
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS2021
Der Dateiname „Datei“ ist zu lang oder ungültig.  
  
 Ein an den C\#\-Compiler übergebener Dateiname darf nicht länger sein als `_MAX_PATH` \(definiert in einer Windows\-Headerdatei\). Der Compiler gibt diesen Fehler in den folgenden Situationen aus:  
  
-   Ein Dateiname \(einschließlich Pfad\) ist länger als `_MAX_PATH`.  
  
-   Der Dateiname enthält ungültige Zeichen.  
  
-   Der Dateiname enthält Platzhalter, obwohl keine Platzhalter zulässig sind \(z. B. in Ressourcendateinamen\).