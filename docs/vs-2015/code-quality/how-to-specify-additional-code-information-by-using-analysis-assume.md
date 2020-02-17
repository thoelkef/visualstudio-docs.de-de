---
title: 'Gewusst wie: Angeben zusätzlicher Code Informationen mithilfe __analysis_assume | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277973"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Gewusst wie: Angeben zusätzlicher Codeinformationen mit __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Hinweise für das Code Analysetool für C/C++ Code bereitstellen, das den Analyseprozess unterstützt und Warnungen reduziert. Verwenden Sie die folgende Funktion, um zusätzliche Informationen bereitzustellen:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`-beliebiger Ausdruck, der als true ausgewertet wird.  
  
 Das Code Analysetool geht davon aus, dass die Bedingung, die durch den Ausdruck dargestellt wird, an der Stelle, an der die Funktion angezeigt wird, true ist, bis der Ausdruck geändert wird, z. b. durch Zuweisung zu einer Variablen.  
  
> [!NOTE]
> `__analysis_assume` wirkt sich nicht auf die Codeoptimierung aus. Außerhalb des Code Analysetools ist `__analysis_assume` als No-op definiert.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code verwendet `__analysis_assume`, um die Code Analyse Warnung zu korrigieren [C6388](../code-quality/c6388.md):  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
