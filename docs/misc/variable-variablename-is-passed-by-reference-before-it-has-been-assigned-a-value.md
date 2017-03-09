---
title: "Die Variable &#39;&lt;Variablenname&gt;&#39; wurde als Verweis &#252;bergeben, bevor ihr ein Wert zugewiesen wurde | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42030"
  - "BC42030"
helpviewer_keywords: 
  - "BC42030"
ms.assetid: 8f1aae99-f032-4fdf-b6dc-3360cc5b94de
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Variable &#39;&lt;Variablenname&gt;&#39; wurde als Verweis &#252;bergeben, bevor ihr ein Wert zugewiesen wurde
Die Variable '\<Variablenname\>' wurde als Verweis übergeben, bevor ihr ein Wert zugewiesen wurde. Zur Laufzeit kann eine NULL\-Verweisausnahme auftreten.  
  
 Ein Prozeduraufruf übergibt eine Variable als Argument an einen `ByRef`\-Parameter, bevor der Variablen ein Wert zugewiesen wird.  
  
 Wenn einer Variablen nie ein Wert zugewiesen wurde, enthält sie den Standardwert für ihren Datentyp. Bei Verweisdatentypen ist dieser Standardwert [Nothing](/dotnet/visual-basic/language-reference/nothing). Das Lesen einer Verweisvariablen, die den Wert `Nothing` aufweist, kann unter bestimmten Umständen zu einer <xref:System.NullReferenceException> führen.  
  
 Beim Übergeben eines Arguments an eine Prozedur `ByRef` wird die Variable, die dem Argument zugrunde liegt, für mögliche Änderungen durch die Prozedur verfügbar gemacht.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42030  
  
### So beheben Sie diesen Fehler  
  
-   Wenn die Prozedur einer Variablen einen Wert mithilfe des `ByRef`\-Arguments zuweisen soll und es keine Rolle spielt, ob die Variable bereits einen Wert enthält, ist keine Aktion erforderlich.  
  
-   Wenn die Logik in der Prozedur das Argument ausliest, bevor sie ihm einen Wert zuweist, und die Variable einen Werttyp besitzt, stellen Sie sicher, dass die Prozedurlogik nicht davon abhängt, ob die Variable ihren Standardwert oder einen anderen Wert enthält.  
  
-   Wenn die Logik in der Prozedur das Argument ausliest, bevor ihm ein Wert zugewiesen wird, und es sich bei der Variablen um einen Verweistyp handelt, stellen Sie sicher, dass die Prozedurlogik den Wert `Nothing` verarbeiten kann. Beispielsweise kann sie ein [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) zum Abfangen einer <xref:System.NullReferenceException> verwenden.  
  
## Siehe auch  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Variablendeklaration](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Problembehandlung bei Variablen](/dotnet/visual-basic/programming-guide/language-features/variables/troubleshooting-variables)