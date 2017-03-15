---
title: "Ressourcencompiler: Fehler RC2115 | Microsoft Docs"
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
  - "RC2115"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2115"
ms.assetid: 1b90feb0-f1fb-4f3c-8a9a-c44f9f8dc366
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Ressourcencompiler: Fehler RC2115
Textzeichenfolge oder Ordnungszahl im Steuerelement erwartet  
  
 Das *Textfeld* einer CONTROL\-Anweisung in der **DIALOG**\-Anweisung muss entweder eine Textzeichenfolge oder einen Verweis auf den Steuerelementtyp in Form einer Ordnungszahl enthalten. Wenn Sie eine Ordnungszahl verwenden, achten Sie darauf, eine `#define`\-Anweisung für das Steuerelement zu verwenden.