---
title: 'Vorgehensweise: Angeben zusätzlicher Codeinformationen mit __analysis_assume | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 608ae6383f95122d5e4b85658b12d454dec24d4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202539"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Gewusst wie: Angeben zusätzlicher Codeinformationen mit __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Hinweise an, die das Codeanalysetool für C/C++-Code angeben, die den Analyse zu unterstützen und Warnungen zu reduzieren. Um zusätzliche Informationen bereitzustellen, verwenden Sie die folgende Funktion:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -Ein Ausdruck, der davon ausgegangen wird, auf "true" ausgewertet.  
  
 Das Codeanalysetool wird davon ausgegangen, dass die Bedingung, die durch den Ausdruck dargestellt wird "true", an dem Punkt ist, in dem die Funktion angezeigt wird, und "true" bleibt, bis der Ausdruck geändert wird, z. B. durch die Zuweisung zur Variable.  
  
> [!NOTE]
>  `__analysis_assume` codeoptimierung hat keine Auswirkungen. Außerhalb der Codeanalysetools `__analysis_assume` als keine Aktion definiert ist.  
  
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
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)



