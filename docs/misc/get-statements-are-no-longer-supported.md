---
title: "Get-Anweisungen werden nicht mehr unterst&#252;tzt. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30829"
  - "bc30829"
helpviewer_keywords: 
  - "BC30829"
ms.assetid: 8d798357-7efb-4423-9808-8b20777b97ba
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Get-Anweisungen werden nicht mehr unterst&#252;tzt.
`Get`\-Anweisungen werden nicht mehr unterstützt. Datei\-E\/A\-Funktionalität ist im `Microsoft.VisualBasic`\-Namespace verfügbar.  
  
 `Get` wird für Dateivorgänge nicht unterstützt und kann nur in der Syntax von Eigenschaftsprozeduren verwendet werden.  
  
 **Fehler\-ID:** BC30829  
  
### So beheben Sie diesen Fehler  
  
1.  Führen Sie Dateivorgänge mit den Membern der Laufzeitfunktionen `System.IO`, `FileSystemObject` und [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aus.  
  
## Siehe auch  
 [Processing Drives, Directories, and Files](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/index)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [File Access with Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)