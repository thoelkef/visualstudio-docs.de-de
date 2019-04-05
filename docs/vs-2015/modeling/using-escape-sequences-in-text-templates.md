---
title: Verwenden von Escapesequenzen in Textvorlagen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: aecd53f9321108d429c732cc8b802ee5dfc8a99c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947102"
---
# <a name="using-escape-sequences-in-text-templates"></a>Verwenden von Escapesequenzen in Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Können Sie Escapesequenzen in Textvorlagen generieren Sie Text in Template Tags und (in c# nur Code)-Steuerelement-Escape-Zeichen und Anführungszeichen.  
  
 Um öffnende und schließende Tags für einen standard-Codeblock in die Ausgabedatei drucken, mit Escapezeichen versehen Sie die Tags wie folgt:  
  
```  
\<# ... \#>  
```  
  
 Sie können auch mit anderen Text-Vorlage Richtlinie und Code-Block Tags vornehmen.  
  
 Enthält ein TextBlock Zeichenfolgen, die Text-in Template Tags als Escapezeichen verwendet, können Sie die folgenden Escapesequenzen verwenden:  
  
-   Wenn Sie eine Vorlage Texttag eine gerade Anzahl von Escapezeichen vorangestellt ist (\\) Zeichen von der Vorlage Parser wird die Hälfte der Escape-Zeichen und die Sequenz als Text Template-Tag enthalten. Z. B. wenn vier Escape-Zeichen in der Textvorlage vorhanden sind, stehen zwei "\\" Zeichen in der generierten Datei.  
  
-   Wenn eine ungerade Anzahl von Escapezeichen Vorlagentags Text vorangestellt ist (\\) Zeichen der Vorlagenparser umfasst die Hälfte der der "\\"-Zeichen sowie das Tag selbst (\<# oder #>). Das Tag ist nicht als Text Template-Tag werden.  
  
-   Wenn ein Escapezeichen (\\) Zeichen wird angezeigt, an anderer Stelle in beliebiger Reihenfolge als die, in dem sie ein Steuerzeichen noch ein öffnendes ohne schließendes Anführungszeichen (nur c#) versieht, wird das Zeichen direkt ausgegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
