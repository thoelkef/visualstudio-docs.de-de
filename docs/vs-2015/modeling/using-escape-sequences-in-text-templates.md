---
title: Verwenden von Escapesequenzen in Text Vorlagen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a45aa36ddce57141a7e1e851f7f0766b77015ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659423"
---
# <a name="using-escape-sequences-in-text-templates"></a>Verwenden von Escapesequenzen in Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Escapesequenzen in Textvorlagen verwenden, um Textvorlagen Tags zu C# generieren, und (nur im Code), um Steuerzeichen und Anführungszeichen zu versehen.

 Um öffnende und schließende Tags für einen standardmäßigen Codeblock in der Ausgabedatei zu drucken, versehen Sie die Tags wie folgt:

```
\<# ... \#>
```

 Dies können Sie mit anderen Textvorlagen Direktiven und Code Block Tags tun.

 Wenn ein TextBlock Zeichen folgen enthält, die zum Escapezeichen von Textvorlagen Tags verwendet werden, können Sie die folgenden Escapesequenzen verwenden:

- Wenn einem Text Template-Tag eine gerade Anzahl von Escapezeichen (\\) vorangestellt ist, enthält der Vorlagen Parser die Hälfte der Escapezeichen und schließt die Sequenz als Textvorlagen-Tag ein. Wenn die Textvorlage beispielsweise vier Escapezeichen enthält, werden in der generierten Datei zwei "\\"-Zeichen angezeigt.

- Wenn dem Text Template-Tag eine ungerade Anzahl von Escapezeichen (\\) vorangestellt ist, enthält der Vorlagen Parser die Hälfte der "\\"-Zeichen sowie das Tag selbst (\< # oder # >). Das-Tag wird nicht als Textvorlagen-Tag betrachtet.

- Wenn ein Escapezeichen (\\) an einer anderen Stelle in einer anderen Sequenz als ein Escapezeichen für ein Steuerzeichen oder C# ein Anführungszeichen (nur in) angezeigt wird, wird das Zeichen direkt ausgegeben.

## <a name="see-also"></a>Siehe auch
 [Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
