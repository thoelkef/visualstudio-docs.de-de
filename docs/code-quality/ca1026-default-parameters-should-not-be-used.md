---
title: "CA1026: Standardparameter sollten nicht verwendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1026"
  - "DefaultParametersShouldNotBeUsed"
helpviewer_keywords: 
  - "CA1026"
  - "DefaultParametersShouldNotBeUsed"
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1026: Standardparameter sollten nicht verwendet werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein extern sichtbarer Typ enthält eine extern sichtbare Methode, die einen Standardparameter verwendet.  
  
## Regelbeschreibung  
 Methoden, die Standardparameter verwenden, sind nach der Common Language Specification \(CLS\) zulässig. Die CLS lässt jedoch zu, dass die Werte, die diesen Parametern zugewiesen sind, von Compilern ignoriert werden.  In Code, der für Compiler geschrieben wurde, die Standardparameterwerte ignorieren, müssen Argumente für jeden Standardparameter explizit bereitgestellt werden.  Damit das gewünschte Verhalten in verschiedenen Programmiersprachen erhalten bleibt, müssen Methoden, die Standardparameter verwenden, durch Methodenüberladungen ersetzt werden, von denen die Standardparameter bereitgestellt werden.  
  
 Beim Zugriff auf verwalteten Code werden die Werte von Standardparametern für Managed Extensions für C\+\+ vom Compiler ignoriert.  Der Visual Basic\-Compiler unterstützt Methoden, die über Standardparameter verfügen, die das [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)\-Schlüsselwort verwenden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die Methode, die Standardparameter verwendet, durch Methodenüberladungen, die Standardparameter bereitstellen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Methode, die Standardparameter verwendet, sowie die überladenen Methoden, die eine entsprechende Funktionalität bereitstellen.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## Verwandte Regeln  
 [CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## Siehe auch  
 [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)