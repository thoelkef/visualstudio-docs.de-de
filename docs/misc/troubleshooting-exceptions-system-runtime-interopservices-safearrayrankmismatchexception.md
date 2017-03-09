---
title: "Problembehandlung bei Ausnahmen: System.Runtime.InteropServices.SafeArrayRankMismatchException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSafeArrayRankMismatch"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SafeArrayRankMismatchException-Klasse"
ms.assetid: 6c69355c-8bfd-49bb-acad-b4d7236ae2e7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Runtime.InteropServices.SafeArrayRankMismatchException
Eine <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>\-Ausnahme wird ausgelöst, wenn der Rang eines eingehenden SAFEARRAY nicht mit dem Rang übereinstimmt, der in der verwalteten Signatur festgelegt ist.  
  
## Tipps  
 **Stellen Sie sicher, dass das Array die erforderliche Anzahl von Dimensionen aufweist.**  
 Da Rang und Grenzen eines sicheren Arrays über die Typbibliothek nicht bestimmt werden können, wird für den Rang ein Wert von 1 und für die Untergrenze ein Wert von 0 angenommen. Rang und Grenzen müssen in der vom [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) erzeugten verwalteten Signatur definiert werden.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Default Marshaling for Arrays](../Topic/Default%20Marshaling%20for%20Arrays.md)   
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)