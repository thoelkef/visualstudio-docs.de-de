---
title: "CA2104: Schreibgesch&#252;tzte &#228;nderbare Referenztypen nicht deklarieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2104: Schreibgesch&#252;tzte &#228;nderbare Referenztypen nicht deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt.  
  
## Regelbeschreibung  
 Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können.  Die <xref:System.Text.StringBuilder?displayProperty=fullName>\-Klasse ist ein Beispiel für einen änderbaren Referenztyp.  Sie enthält Member, die den Wert einer Instanz der Klasse ändern können.  Ein Beispiel für einen nicht änderbaren Referenztyp ist die <xref:System.String?displayProperty=fullName>\-Klasse.  Nachdem sie instanziiert wurde, kann sich ihr Wert nie ändern.  
  
 Der schreibgeschützte Modifizierer \([readonly](/dotnet/csharp/language-reference/keywords/readonly) in C\#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] und [const](/visual-cpp/cpp/const-cpp) in C\+\+\) in einem Feld mit einem Verweistyp \(Zeiger in C\+\+\) verhindert, dass das Feld durch eine andere Instanz des Verweistyps ersetzt wird.  Der Modifizierer verhindert jedoch nicht, dass die Instanzdaten des Felds durch den Verweistyp geändert werden.  
  
 Schreibgeschützte Arrayfelder sind von dieser Regel ausgenommen, verursachen jedoch stattdessen einen Verstoß gegen die Regel [CA2105: Arrayfelder dürfen nicht schreibgeschützt sein](../code-quality/ca2105-array-fields-should-not-be-read-only.md).  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Schreibschutzmodifizierer. Falls eine unterbrechende Änderung vertretbar ist, können Sie das Feld auch durch einen nicht änderbaren Typ ersetzen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Feldtyp unveränderlich ist.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Felddeklaration, die einen Verstoß gegen diese Regel verursacht.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]