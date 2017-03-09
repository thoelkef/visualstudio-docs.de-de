---
title: "&lt;typ1&gt; &#39;&lt;membername&gt;&#39; f&#252;hrt Shadowing f&#252;r einen &#252;berladbaren Member aus, der in Basis-&lt;type&gt; &#39;&lt;klassenname&gt;&#39; deklariert ist | Microsoft Docs"
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
  - "bc40003"
  - "vbc40003"
helpviewer_keywords: 
  - "BC40003"
ms.assetid: 1e0d2061-0ad9-4915-b946-d55cb5d5ee80
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;typ1&gt; &#39;&lt;membername&gt;&#39; f&#252;hrt Shadowing f&#252;r einen &#252;berladbaren Member aus, der in Basis-&lt;type&gt; &#39;&lt;klassenname&gt;&#39; deklariert ist
\<typ1\> '\<membername\>' führt Shadowing für einen überladbaren Member aus, der in Basis\-\<type\> '\<klassenname\>' deklariert ist. Wenn Sie die Basismethode überladen möchten, muss die Methode als 'Overloads' deklariert werden.  
  
 Eine abgeleitete Klasse definiert eine `Function` oder `Sub`\-Prozedur oder eine `Property` mit dem gleichen Namen wie eine in der Basisklasse definierte Prozedur oder Eigenschaft. Da Prozeduren und Eigenschaften überladbare Member sind, kann die abgeleitete Klasse entweder überladen oder Shadowing für den Basisklassenmember ausführen. Der Code der abgeleiteten Klasse gibt jedoch weder [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) noch [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) in der Deklaration an. Bei Abwesenheit beider Schlüsselwörter geht der Compiler von `Shadows` aus.  
  
 Im Sinne eines guten Programmierstils geben Sie entweder `Overloads` oder `Shadows` an. Dadurch wird Ihr Code einfacher zu lesen und zu verstehen.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40003  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie die Basisklassenmethode oder \-eigenschaft überladen möchten, schließen Sie das Schlüsselwort `Overloads` in die Deklaration ein.  
  
-   Wenn Sie Shadowing für die Basisklassenmethode oder \-eigenschaft ausführen möchten, schließen Sie das Schlüsselwort `Shadows` anstelle von `Overloads` ein.  
  
-   Wenn Sie das Basisklassenmember weder überladen noch Shadowing für es ausführen möchten, ändern Sie den Namen des abgeleiteten Klassenmembers.  
  
## Siehe auch  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)