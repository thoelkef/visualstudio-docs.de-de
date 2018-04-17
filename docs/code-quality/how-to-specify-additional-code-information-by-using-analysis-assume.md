---
title: 'Vorgehensweise: Angeben zusätzlicher Codeinformationen mit __analysis_assume | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f039298e56e33bc80ae1a9f7384a40914c532ff8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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