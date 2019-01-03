---
title: 'Vorgehensweise: Angeben zusätzlicher Codeinformationen mit „__Analysis_assume“'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 17e25ace1da6cad9fcdc129b6c6f517c39c9c103
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845077"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Vorgehensweise: Angeben zusätzlicher Codeinformationen mit „__Analysis_assume“
Sie können Hinweise an, die das Codeanalysetool für C/C++-Code angeben, die den Analyse zu unterstützen und Warnungen zu reduzieren. Um zusätzliche Informationen bereitzustellen, verwenden Sie die folgende Funktion:

 `_Analysis_assume(`  `expr`  `)`

 `expr` -Ein Ausdruck, der davon ausgegangen wird, auf "true" ausgewertet.

 Das Codeanalysetool wird davon ausgegangen, dass die Bedingung, die durch den Ausdruck dargestellt wird "true", an dem Punkt ist, in dem die Funktion angezeigt wird, und "true" bleibt, bis der Ausdruck geändert wird, z. B. durch die Zuweisung zur Variable.

> [!NOTE]
>  `_Analysis_assume` codeoptimierung hat keine Auswirkungen. Außerhalb der Codeanalysetools `_Analysis_assume` als keine Aktion definiert ist.

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