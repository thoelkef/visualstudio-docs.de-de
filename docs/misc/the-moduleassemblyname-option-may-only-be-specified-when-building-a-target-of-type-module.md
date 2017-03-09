---
title: "Die Option &#39;/moduleassemblyname&#39; kann nur beim Erstellen eines Ziels vom Typ &#39;Modul&#39; angegeben werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc2030"
  - "vbc2030"
helpviewer_keywords: 
  - "BC2030"
ms.assetid: 2ebc577b-3464-40cc-8788-9fc9d3b4f928
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Option &#39;/moduleassemblyname&#39; kann nur beim Erstellen eines Ziels vom Typ &#39;Modul&#39; angegeben werden.
Dem Visual Basic\-Compiler wurde die `/moduleassemblyname`\-Compileroption übergeben, als die `/target`\-Option auf einen anderen Wert als `module` festgelegt wurde.  
  
 **Fehler\-ID:** BC2030  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die `/moduleassemblyname`\-Compileroption, oder legen Sie die `/target`\-Option auf `module` fest.  
  
## Siehe auch  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/moduleassemblyname](/dotnet/visual-basic/reference/command-line-compiler/moduleassemblyname)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)