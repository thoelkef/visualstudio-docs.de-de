---
title: "WithEvents-Variablen m&#252;ssen eine As-Klausel haben. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30412"
  - "bc30412"
helpviewer_keywords: 
  - "BC30412"
ms.assetid: 8c941523-8e5d-4bf0-8a52-772ecd5d5592
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# WithEvents-Variablen m&#252;ssen eine As-Klausel haben.
Sie haben keine `As`\-Klausel mit dem `WithEvents`\-Schlüsselwort angegeben. Deklarieren Sie die Variable als spezifische Klasse, die die Ereignisse auslösen kann.  
  
 **Fehler\-ID:** BC30412  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie die `As`\-Klausel hinzu, die die Klasse angibt, die die Ereignisse auslösen kann.  
  
## Siehe auch  
 [NICHT IM BUILD: WithEvents und die Handles\-Klausel](http://msdn.microsoft.com/de-de/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)