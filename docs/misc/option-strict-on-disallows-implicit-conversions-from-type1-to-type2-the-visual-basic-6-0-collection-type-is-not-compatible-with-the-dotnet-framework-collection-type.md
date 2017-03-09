---
title: "&quot;Option Strict On&quot; l&#228;sst keine impliziten Konvertierungen von &quot;&lt;Typ1&gt;&quot; in &quot;&lt;Typ2&gt;&quot; zu. Der Visual Basic 6.0-Auflistungstyp ist mit dem .NET Framework-Auflistungstyp nicht kompatibel. | Microsoft Docs"
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
  - "vbc30753"
  - "bc30753"
helpviewer_keywords: 
  - "BC30753"
ms.assetid: 7e1bb22e-a507-483e-bfd6-f3a43e24a232
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Option Strict On&quot; l&#228;sst keine impliziten Konvertierungen von &quot;&lt;Typ1&gt;&quot; in &quot;&lt;Typ2&gt;&quot; zu. Der Visual Basic 6.0-Auflistungstyp ist mit dem .NET Framework-Auflistungstyp nicht kompatibel.
`Option Strict On` lässt keine impliziten Konvertierungen von "`<type1>`" in "`<type2>`" zu. Der Visual Basic 6.0\-Auflistungstyp ist mit dem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Auflistungstyp nicht kompatibel.  
  
 Das Auflistungsobjekt, das in Visual Basic 6.0 verwendet wird, unterscheidet sich von dem Auflistungsobjekt, das in [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] verwendet wird.  
  
 **Fehler\-ID:** BC30753  
  
### So beheben Sie diesen Fehler  
  
-   Konvertieren Sie Auflistungsobjekte explizit mit einem der Schlüsselwörter für die Typkonvertierung. Die Schlüsselwörter [CType\-Funktion](/dotnet/visual-basic/language-reference/functions/ctype-function) und [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator) lösen zur Laufzeit eine Ausnahme aus, wenn die Konvertierung fehlschlägt. Das Schlüsselwort [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator) gibt [Nothing](/dotnet/visual-basic/language-reference/nothing) zurück, wenn die Konvertierung fehlschlägt.  
  
## Siehe auch  
 [CType\-Funktion](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [NICHT IM BUILD: Auflistungen in Visual Basic](http://msdn.microsoft.com/de-de/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)