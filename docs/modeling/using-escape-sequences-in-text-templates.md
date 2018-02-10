---
title: Verwenden von Escapesequenzen in Textvorlagen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f6ab5346ed82aadea339bc8ee45ac4a3bfb72c65
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="using-escape-sequences-in-text-templates"></a>Verwenden von Escapesequenzen in Textvorlagen
Sie können Escapesequenzen in Textvorlagen zum Generieren von Vorlagen-Tags für Text und (im C#-Code nur) zum Steuerelement Escapezeichen und die Anführungszeichen stehen.  
  
 Um öffnende und schließende Tags für eine standardmäßige Codeblock in die Ausgabedatei drucken, versehen Sie die Tags wie folgt:  
  
```  
\<# ... \#>  
```  
  
 Sie können auch mit anderen Text Vorlage Richtlinie und Code-Block Tags vornehmen.  
  
 Enthält ein TextBlock Zeichenfolgen verwendet, um die Vorlagen-Tags für Text mit Escapezeichen versehen, können Sie die folgenden Escapesequenzen verwenden:  
  
-   Wenn eine Vorlage Texttag eine gerade Anzahl von Escapezeichen vorangestellt wird (\\) Zeichen von der Vorlage Parser wird die Hälfte der Escape-Zeichen und der Folge als Vorlage Texttag enthalten. Z. B. wenn in der Vorlage "Text" vier-Escape-Zeichen vorhanden sind, es werden zwei "\\" Zeichen in der generierten Datei.  
  
-   Wenn die Vorlage Texttag eine ungerade Anzahl von Escapezeichen vorangestellt wird (\\) Zeichen d. h., der Vorlagenparser enthält die Hälfte der der "\\"-Zeichen sowie das Tag selbst (\<# or #>). Das Tag ist nicht als Vorlage Texttag werden.  
  
-   Wenn ein Escapezeichen (\\) Zeichen vorkommt, wird an anderer Stelle in beliebiger Reihenfolge als die, in dem sie ein Steuerzeichen noch ein öffnendes ohne schließendes Anführungszeichen (nur c#) versieht, wird das Zeichen direkt ausgegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)