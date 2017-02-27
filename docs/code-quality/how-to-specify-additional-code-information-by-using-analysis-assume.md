---
title: "Gewusst wie: Angeben zus&#228;tzlicher Codeinformationen mit __analysis_assume | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__analysis_assume"
helpviewer_keywords: 
  - "__analysis_assume"
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Gewusst wie: Angeben zus&#228;tzlicher Codeinformationen mit __analysis_assume
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können dem Codeanalysetool für C\/C\+\+\-Code Hinweise zur Verfügung stellen, durch die der Analyseprozess unterstützt und Warnungen reduziert werden.  Um zusätzliche Informationen bereitzustellen, verwenden Sie die folgende Funktion:  
  
 `__analysis_assume(`   `expr`   `)`  
  
 `expr` – beliebiger Ausdruck, von dem angenommen wird, dass er true ergibt.  
  
 Das Codeanalysetool geht davon aus, dass die durch den Ausdruck angegebene Bedingung an dem Punkt, an dem die Funktion auftritt, true ergibt und so lange gültig bleibt, bis der Ausdruck, beispielsweise durch die Zuweisung zu einer Variablen, geändert wird.  
  
> [!NOTE]
>  `__analysis_assume` hat keine Auswirkungen auf die Codeoptimierung.  Außerhalb des Codeanalysetools wird durch `__analysis_assume` keine Aktion ausgeführt.  
  
## Beispiel  
 Im folgenden Code wird `__analysis_assume` verwendet, um die Codeanalysewarnung [C6388](../code-quality/c6388.md) zu korrigieren:  
  
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
  
## Siehe auch  
 [\_\_assume](/visual-cpp/intrinsics/assume)