---
title: "CA1806: Methodenergebnisse nicht ignorieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806: Methodenergebnisse nicht ignorieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Diese Warnung kann unterschiedliche Gründe haben:  
  
-   Es wurde ein neues Objekt erstellt, jedoch nie verwendet.  
  
-   Es wird eine Methode aufgerufen, die eine neue Zeichenfolge erstellt und zurückgibt, allerdings wird die neue Zeichenfolge nie verwendet.  
  
-   Eine COM\- oder P\/Invoke\-Methode, die ein HRESULT oder einen Fehlercode zurückgibt, das oder der nie verwendet wird.  Regelbeschreibung  
  
 Die unnötige Objekterstellung und die zugeordnete Garbage Collection des nicht verwendeten Objekts beeinträchtigen die Leistung.  
  
 Zeichenfolgen sind nicht veränderlich, und bestimmte Methoden, z. B. String.ToUpper, geben eine neue Instanz einer Zeichenfolge zurück, statt die Instanz der Zeichenfolge in der aufrufenden Methode zu ändern.  
  
 Wenn HRESULT oder der Fehlercode ignoriert werden, kann dies zu unerwartetem Verhalten in Fehlerbedingungen oder Situationen führen, in denen nur geringe Ressourcen verfügbar sind.  
  
## Behandeln von Verstößen  
 Wenn Methode A eine neue Instanz von Objekt B erstellt, das nie verwendet wird, übergeben Sie die Instanz als Argument an eine andere Methode, oder weisen Sie die Instanz einer Variablen zu.  Wenn die Objekterstellung nicht erforderlich ist, entfernen Sie das it. – oder –  
  
 Wenn die Methode A Methode B aufruft, jedoch nicht die neue, von Methode B zurückgegebene Zeichenfolgeninstanz verwendet.  Übergeben Sie die Instanz als Argument an eine andere Methode, weisen Sie die Instanz einer Variablen zu.  Wenn der Aufruf nicht erforderlich ist, können Sie diesen auch entfernen.  
  
 \- oder \-  
  
 Wenn Methode A Methode B aufruft, jedoch nicht das HRESULT oder den Fehlercode verwendet, das oder der von der Methode zurückgegeben wird.  Verwenden Sie das Ergebnis in einer Bedingungsanweisung, weisen Sie das Ergebnis einer Variablen zu, oder übergeben Sie es als Argument an eine andere Methode.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, mit der Objekterstellung wird ein bestimmter Zweck verfolgt.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Klasse, die das Ergebnis des Aufrufs von String.Trim ignoriert.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## Beispiel  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem das Ergebnis von String.Trim der Variablen, für die die Methode aufgerufen wurde, erneut zugeordnet wird.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode veranschaulicht, die kein von ihr erstelltes Objekt verwendet.  
  
> [!NOTE]
>  Dieser Verstoß kann nicht in Visual Basic reproduziert werden.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## Beispiel  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem die unnötige Erstellung eines Objekts entfernt wird.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Methode, die den von der systemeigenen GetShortPathName\-Methode zurückgegebenen Fehlercode ignoriert.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem der Fehlercode überprüft wird und eine Ausnahme ausgelöst wird, wenn der Aufruf fehlschlägt.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]