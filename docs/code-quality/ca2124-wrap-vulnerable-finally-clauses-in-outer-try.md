---
title: "CA2124: Anfällige finally Klauseln mit äußerem versuchen Sie es | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f4d30a07ed0930d5165629f7c4b468d7e5146613
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen
|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 In den Versionen 1.0 und 1.1 von der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], eine öffentliche oder geschützte Methode enthält einen `try` / `catch` / `finally` Block. Die `finally` Block wird der Sicherheitszustand zurückgesetzt angezeigt und steht nicht in einem `finally` Block.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel sucht `try` / `finally` Blöcke in Code, der Versionen 1.0 und 1.1 von abzielt die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , die möglicherweise anfällig für böswillige Ausnahmefilter in der Aufrufliste vorhanden. Wenn sicherheitsrelevante Vorgänge wie z. B. Identitätswechsel in Try-Blocks auftreten, und eine Ausnahme ausgelöst wird, kann der Filter vor dem Ausführen der `finally` Block. Für das Impersonation-Beispiel bedeutet dies, dass der Filter als die Identität eines Benutzers ausgeführt werden würde. Filter sind derzeit nur in Visual Basic implementiert.  
  
> [!WARNING]
>  **Hinweis** In Version 2.0 oder höher, der die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], die Common Language Runtime automatisch schützt eine `try` / `catch` /  `finally` Blockieren von böswilligen Ausnahmefilter, erfolgt das Zurücksetzen direkt innerhalb der Methode, die vom Ausnahmeblock enthält.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Platzieren Sie die entpackte `try` / `finally` in einem äußeren Try-Block. Finden Sie im zweiten Beispiel, das folgt. Dies zwingt den `finally` ausgeführt wird, bevor die Filtercode.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="pseudo-code-example"></a>Pseudocodebeispiel  
  
### <a name="description"></a>Beschreibung  
 Der folgende Pseudocode veranschaulicht das von dieser Regel erkannte Muster.  
  
### <a name="code"></a>Code  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## <a name="example"></a>Beispiel  
 Der folgende Pseudocode zeigt das Muster, die Sie verwenden können, um Ihren Code zu schützen und diese Regel zu erfüllen.  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```