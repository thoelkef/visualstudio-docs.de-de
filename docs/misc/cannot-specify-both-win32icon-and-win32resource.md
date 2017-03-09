---
title: "„/win32icon“ und „/win32resource“ k&#246;nnen nicht gleichzeitig angegeben werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc2023"
  - "bc2023"
helpviewer_keywords: 
  - "BC2023"
ms.assetid: 60914807-1fde-4fef-9c6f-6f4a62527eed
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „/win32icon“ und „/win32resource“ k&#246;nnen nicht gleichzeitig angegeben werden.
Die Optionen `/win32resource` und `/win32icon` schließen sich gegenseitig aus, da sie beide Symbolinformationen in die Ausgabedatei einfügen.  
  
 **Fehler\-ID:** BC2023  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie nur die `/win32icon`\-Option zum Einfügen einer ICO\-Datei in die Ausgabedatei. Diese ICO\-Datei stellt die Ausgabedatei in Windows\-Explorer dar.  
  
     \- oder \-  
  
-   Verwenden Sie nur die `/win32resource`\-Option zum Einfügen einer Win32\-Ressourcendatei in die Ausgabedatei. Eine Win32\-Ressource kann Versions\- oder Bitmapinformationen \(Symbolinformationen\) enthalten, anhand derer die Anwendung in Windows\-Explorer identifiziert werden kann.  
  
## Siehe auch  
 [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)   
 [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource)