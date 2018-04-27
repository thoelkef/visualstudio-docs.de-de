---
title: 'Vorgehensweise: Angeben zusätzlicher Codeinformationen mit _Analysis_assume'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ce8102bbc790019490c4dc2a2ccbfab7d8c33981
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Vorgehensweise: Angeben zusätzlicher Codeinformationen mit _Analysis_assume
Sie können Hinweise an, die das Codeanalysetool für C/C++-Code bereitstellen, die denen des Analysevorgangs und Warnungen zu reduzieren. Um zusätzliche Informationen bereitzustellen, verwenden Sie die folgende Funktion:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -Ein Ausdruck, der davon ausgegangen, dass wird "Wahr" ausgewertet.

 Das Codeanalysetool wird davon ausgegangen, dass die Bedingung, die durch den Ausdruck dargestellt wird, in dem die Funktion angezeigt wird, und "true" bleibt, bis der Ausdruck geändert wird, z. B. durch die Zuweisung zur Variable, Zeitpunkt "true" ist.

> [!NOTE]
>  `_Analysis_assume` Code-Optimierung hat keine Auswirkungen. Außerhalb der Codeanalysetool `_Analysis_assume` als ein ohne-Op definiert ist.

## <a name="example"></a>Beispiel
 Der folgende code verwendet `_Analysis_assume` der codeanalysewarnung zu korrigieren [C6388](../code-quality/c6388.md):

```
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Siehe auch
 [__assume](/cpp/intrinsics/assume)