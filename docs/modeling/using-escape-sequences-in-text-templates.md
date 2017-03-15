---
title: "Using Escape Sequences in Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, escape sequences"
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# Using Escape Sequences in Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Escapesequenzen in Textvorlagen verwenden, um Textvorlagentags zu generieren und \(nur in C\#\-Code\) Steuerzeichen und Anführungszeichen mit Escapezeichen zu versehen.  
  
 Um Start\- und Endtags für einen Standardcodeblock in die Ausgabedatei auszugeben, versehen Sie die Tags wie folgt mit Escapezeichen:  
  
```  
\<# ... \#>  
```  
  
 Diese Vorgehensweise kann auch für andere Textvorlagendirektiven\- und Codeblocktags verwendet werden.  
  
 Wenn ein Textblock Zeichenfolgen enthält, die verwendet werden, um Textvorlagentags mit Escapezeichen zu versehen, können Sie die folgenden Escapesequenzen verwenden:  
  
-   Wenn einem Textvorlagentag eine gerade Anzahl von Escapezeichen \(\\\) vorangestellt ist, schließt der Vorlagenparser die Hälfte der Escapezeichen ein, und die Sequenz wird als Textvorlagentag eingeschlossen.  Sind in der Textvorlage z. B. vier Escapezeichen vorhanden, enthält die generierte Datei zwei "\\"\-Zeichen.  
  
-   Wenn dem Textvorlagentag eine ungerade Anzahl von Escapezeichen \(\\\) vorangestellt ist, schließt der Vorlagenparser die Hälfte der "\\"\-Zeichen sowie das Tag selbst \(\<\# oder \#\>\) ein.  Das Tag gilt nicht als Textvorlagentag.  
  
-   Wenn ein Escapezeichen \(\\\) an anderer Stelle in einer Sequenz vorkommt, an der es nicht dazu dient, ein Steuerzeichen oder Anführungszeichen \(nur in C\#\) mit Escapezeichen zu versehen, wird das Zeichen direkt ausgegeben.  
  
## Siehe auch  
 [How to: Generate Templates from Templates By Using Escape Sequences](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)