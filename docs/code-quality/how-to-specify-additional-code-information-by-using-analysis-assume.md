---
title: Verwenden von _Analysis_assume für Code Analyse Hinweise
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 9933a013ed4f2df0978fb66e3aff87b4cdc024f9
ms.sourcegitcommit: c6af923c1f485959d751b23ab3f03541013fc4a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925959"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Gewusst wie: Angeben zusätzlicher Code Informationen mithilfe von _Analysis_assume

Sie können Hinweise für das Code Analysetool für C/C++ Code bereitstellen, das den Analyseprozess unterstützt und Warnungen reduziert. Verwenden Sie die folgende Funktion, um zusätzliche Informationen bereitzustellen:

`_Analysis_assume(`  `expr`  `)`

`expr`-beliebiger Ausdruck, der als true ausgewertet wird.

Das Code Analysetool geht davon aus, dass die Bedingung, die durch den Ausdruck dargestellt wird, an der Stelle, an der die Funktion angezeigt wird, true ist, bis der Ausdruck geändert wird, z. b. durch Zuweisung zu einer Variablen.

> [!NOTE]
> `_Analysis_assume` wirkt sich nicht auf die Codeoptimierung aus. Außerhalb des Code Analysetools ist `_Analysis_assume` als No-op definiert.

## <a name="example"></a>Beispiel

Der folgende Code verwendet `_Analysis_assume`, um die Code Analyse Warnung zu korrigieren [C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Siehe auch

- [__assume](/cpp/intrinsics/assume)
