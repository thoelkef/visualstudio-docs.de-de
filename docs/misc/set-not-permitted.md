---
title: "&quot;Set&quot; ist unzul&#228;ssig. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID387"
ms.assetid: 809f6768-7dd7-4632-b4dd-83856edfdb48
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Set&quot; ist unzul&#228;ssig.
Sie haben versucht, eine Eigenschaft zu ändern, deren Einstellungen nicht zur Laufzeit oder nur unter bestimmten Bedingungen festgelegt werden können. Sie haben beispielsweise versucht, die Eigenschafteneinstellungen `Appearance`, `ControlBox`,`MinButton` oder `MaxButton` für das Formular zur Laufzeit zu ändern, oder Sie haben versucht, die Eigenschaft `Visible` für das letzte sichtbare Untermenü in einem übergeordneten Menü auf `False` festzulegen.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Eigenschaft, und ermitteln Sie, unter welchen Bedingungen sie festgelegt werden kann.  
  
## Siehe auch  
 [NICHT IM BUILD: Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](http://msdn.microsoft.com/de-de/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)