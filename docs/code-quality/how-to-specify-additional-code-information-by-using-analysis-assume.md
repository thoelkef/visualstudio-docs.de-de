---
title: 'Gewusst wie: Angeben zusätzlicher Codeinformationen mit __analysis_assume'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 181f9fb4a1f9f5d653d64fb813b974bad898fe13
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Gewusst wie: Angeben zusätzlicher Codeinformationen mit __analysis_assume
Sie können Hinweise an, die das Codeanalysetool für C/C++-Code bereitstellen, die denen des Analysevorgangs und Warnungen zu reduzieren. Um zusätzliche Informationen bereitzustellen, verwenden Sie die folgende Funktion:

 `__analysis_assume(`  `expr`  `)`

 `expr` -Ein Ausdruck, der davon ausgegangen, dass wird "Wahr" ausgewertet.

 Das Codeanalysetool wird davon ausgegangen, dass die Bedingung, die durch den Ausdruck dargestellt wird, in dem die Funktion angezeigt wird, und "true" bleibt, bis der Ausdruck geändert wird, z. B. durch die Zuweisung zur Variable, Zeitpunkt "true" ist.

> [!NOTE]
>  `__analysis_assume` Code-Optimierung hat keine Auswirkungen. Außerhalb der Codeanalysetool `__analysis_assume` als ein ohne-Op definiert ist.

## <a name="example"></a>Beispiel
 Der folgende code verwendet `__analysis_assume` der codeanalysewarnung zu korrigieren [C6388](../code-quality/c6388.md):

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
  __analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Siehe auch
 [__assume](/cpp/intrinsics/assume)