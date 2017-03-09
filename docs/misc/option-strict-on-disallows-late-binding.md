---
title: "&quot;Option Strict On&quot; l&#228;sst sp&#228;tes Binden nicht zu | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30574"
  - "vbc30574"
helpviewer_keywords: 
  - "BC30574"
ms.assetid: 9da4b826-2e12-4a5d-9e17-762b0b68fc9b
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Option Strict On&quot; l&#228;sst sp&#228;tes Binden nicht zu
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ermöglicht implizite Konvertierungen eines beliebigen Datentyps in einen anderen Datentyp. Allerdings können Datenverluste auftreten, wenn der Wert von einem Datentyp in einen Datentyp konvertiert wird, der weniger genau ist oder eine kleinere Kapazität aufweist.`Option Strict On` stellt die Benachrichtigung zur Kompilierzeit dieser Typen von Konvertierungen sicher, sodass sie vermieden werden können. Sie können `Option Strict On` nicht mit spätem Binden verwenden.  
  
 Im folgenden Codebeispiel wird spätes Binden verwendet, wodurch dieser Fehler verursacht wird, wenn `Option Strict` auf `On` festgelegt ist.  
  
 [!CODE [VbVbalrOptionStrictError#1](VbVbalrOptionStrictError#1)]  
  
 **Fehler\-ID:** BC30574  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Deklaration des Objekts, um einen expliziten Typ zu verwenden, wie im folgenden Beispiel gezeigt:  
  
     [!CODE [VbVbalrOptionStrictError#2](VbVbalrOptionStrictError#2)]  
  
 \- oder \-  
  
-   Ändern Sie den spät gebundenen Ausdruck, um einen expliziten Typ anzugeben, wie im folgenden Beispiel gezeigt:  
  
     [!CODE [VbVbalrOptionStrictError#3](VbVbalrOptionStrictError#3)]  
  
 \- oder \-  
  
-   Lassen Sie einen bestimmten Typ vom Compiler ableiten, wie im folgenden Beispiel gezeigt:  
  
     [!CODE [VbVbalrOptionStrictError#4](VbVbalrOptionStrictError#4)]  
  
 \- oder \-  
  
-   Deaktivieren Sie `Option Strict` durch Entfernen des darauffolgenden Worts `On` oder durch explizite Angabe von `Off`.  
  
## Siehe auch  
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)