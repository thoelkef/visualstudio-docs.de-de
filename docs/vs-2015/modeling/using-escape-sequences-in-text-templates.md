---
title: Verwenden von Escapesequenzen in Textvorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 24e2629001d7c426193059175eab64ea0ab8dacf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513489"
---
# <a name="using-escape-sequences-in-text-templates"></a>Verwenden von Escapesequenzen in Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [mithilfe von Escapesequenzen in Textvorlagen](https://docs.microsoft.com/visualstudio/modeling/using-escape-sequences-in-text-templates).  
  
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
 [Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)



