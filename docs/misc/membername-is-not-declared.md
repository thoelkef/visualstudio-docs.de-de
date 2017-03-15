---
title: "&lt;Membername&gt; wurde nicht deklariert. | Microsoft Docs"
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
  - "vbc30816"
  - "bc30816"
helpviewer_keywords: 
  - "BC30816"
ms.assetid: d6704bed-bb76-47c6-ac28-09608d5e6912
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Membername&gt; wurde nicht deklariert.
„`<membername>` wurde nicht deklariert. Die `Debug`\-Objektfunktion ist in `System.Diagnostics.Debug` in der `System`\-Assembly verfügbar.  
  
 Der angegebene Membername wurde nicht gefunden.  
  
 **Fehler\-ID:** BC30816  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise des Members.  
  
2.  Verwenden Sie eine `Imports`\-Anweisung oder qualifizieren Sie in anderen Namespaces definierte Members vollständig. Die `WriteLine`\-Funktion wird z. B. im `System.Diagnostics.Debug`\-Namespace deklariert.  
  
## Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)