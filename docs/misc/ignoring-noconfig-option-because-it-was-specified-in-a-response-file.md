---
title: "Die /noconfig-Option wird ignoriert, da sie in einer Antwortdatei angegeben wurde. | Microsoft Docs"
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
  - "vbc2025"
  - "bc2025"
helpviewer_keywords: 
  - "BC2025"
ms.assetid: 87fb393d-e17f-4e50-8d98-d9dfeba30c3e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die /noconfig-Option wird ignoriert, da sie in einer Antwortdatei angegeben wurde.
Die `/noconfig`\-Option weist den Compiler an, nicht mit der Datei „Vbc.rsp“ zu kompilieren. Da der Compiler die Datei „Vbc.rsp“ jedoch vor allen anderen Antwortdateien verarbeitet, kann er die `/noconfig`\-Option in einer Antwortdatei nicht berücksichtigen.  
  
 **Fehler\-ID:** BC2025  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die `/noconfig`\-Option aus der Antwortdatei.  
  
2.  Geben Sie die `/noconfig`\-Option an, wenn Sie den Befehlszeilencompiler aufrufen.  
  
## Siehe auch  
 [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig)   
 [@ \(Specify Response File\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file)