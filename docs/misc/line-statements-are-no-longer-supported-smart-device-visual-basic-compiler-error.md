---
title: "Line-Anweisungen werden nicht mehr unterst&#252;tzt (Intelligentes Ger&#228;t/Visual Basic-Compilerfehler) | Microsoft Docs"
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
  - "vbc30768"
  - "bc30768"
helpviewer_keywords: 
  - "BC30768"
ms.assetid: e7a17c77-06bb-4d33-966e-addb4f51caaf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Line-Anweisungen werden nicht mehr unterst&#252;tzt (Intelligentes Ger&#228;t/Visual Basic-Compilerfehler)
Die `Line`\-Anweisung wird nicht mehr unterstützt. Die Datei\-E\/A\-Funktionalität ist in der Regel als <xref:Microsoft.VisualBasic.FileSystem.LineInput%2A?displayProperty=fullName> verfügbar, allerdings wird sie von der Zielversion von .NET Compact Framework nicht unterstützt.  
  
 **Fehler\-ID:** BC30768  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie für den Dateizugriff die im <xref:System.IO>\-Namespace definierten Funktionen.  
  
-   Verwenden Sie <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> für Grafikfunktionen.  
  
## Siehe auch  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [File Access with Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)