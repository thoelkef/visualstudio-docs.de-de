---
title: "CA2124: Anf&#228;llige finally-Klauseln mit &#228;u&#223;erem try-Block umschlie&#223;en | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2124: Anf&#228;llige finally-Klauseln mit &#228;u&#223;erem try-Block umschlie&#223;en
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 In den Versionen 1.0 und 1.1 von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] enthält eine öffentliche oder geschützte Methode einen `try`\/`catch`\/`finally`\-Block.  Durch den `finally`\-Block, der nicht in einen `finally`\-Block eingeschlossen ist, wird anscheinend der Sicherheitszustand zurückgesetzt.  
  
## Regelbeschreibung  
 Diese Regel sucht in Code, der auf die Versionen 1.0 und 1.1 von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] abzielt, `try`\/`finally`\-Blöcke, die für böswillige Ausnahmefilter in der Aufrufliste anfällig sein könnten.  Wenn vertrauliche Vorgänge wie ein Identitätswechsel im try\-Block stattfinden und eine Ausnahme ausgelöst wird, kann der Filter vor dem `finally`\-Block ausgeführt werden.  Bei dem Beispiel mit Identitätswechsel bedeutet dies, dass der Filter als Benutzer ausgeführt wird, für den ein Identitätswechsel vorgenommen wurde.  Filter können derzeit nur in Visual Basic implementiert werden.  
  
> [!WARNING]
>  **Hinweis**  In Version 2.0 und höher von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] schützt die Laufzeit einen `try`\/`catch`\/`finally`\-Block automatisch vor böswilligen Ausnahmefiltern, wenn die Rücksetzung direkt innerhalb der Methode auftritt, die den Ausnahmeblock enthält.  
  
## Behandeln von Verstößen  
 Fügen Sie den allein stehenden `try`\/`finally`\-Block in einen äußeren try\-Block ein.  Vergleichen Sie das folgende zweite Beispiel.  Dabei wird `finally` zwangsweise vor dem Filtercode ausgeführt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel für Pseudocode  
  
### **Beschreibung**  
 Mit dem folgenden Pseudocode wird das von dieser Regel erkannte Muster veranschaulicht.  
  
### Code  
  
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
  
## Beispiel  
 Im folgenden Pseudocode wird das Muster dargestellt, das Sie verwenden können, um den Code zu schützen und diese Regel zu erfüllen.  
  
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