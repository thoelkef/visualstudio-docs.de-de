---
title: "CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5691abd58801d3be6a543a72b5a1f4ca209d3a17
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren
|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. Die <xref:System.Text.StringBuilder?displayProperty=fullName> Klasse ist ein Beispiel für einen änderbaren Referenztyp. Es enthält Elemente, die den Wert einer Instanz der Klasse ändern können. Ein Beispiel für einen nicht änderbaren Referenztyp ist der <xref:System.String?displayProperty=fullName> Klasse. Nachdem es instanziiert wurde, kann ihr Wert nie ändern.  
  
 Den schreibgeschützten Modifizierer ([Readonly](/dotnet/csharp/language-reference/keywords/readonly) in c# [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], und [const](/cpp/cpp/const-cpp) in C++) auf einen Referenztyp darstellt (Zeiger in C++) verhindert das Feld durch eine andere Instanz des Verweistyps ersetzt. Allerdings verhindert der Modifizierer die Instanzdaten des Felds nicht, die durch den Verweistyp geändert wird.  
  
 Schreibgeschützte Arrayfelder sind von dieser Regel ausgenommen, verursachen jedoch stattdessen einen Verstoß gegen die [CA2105: Arrayfelder soll nicht nur lesen](../code-quality/ca2105-array-fields-should-not-be-read-only.md) Regel.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den schreibgeschützten Modifizierer oder, wenn eine unterbrechende Änderung zulässig ist, ersetzen Sie das Feld durch ein unveränderlicher Typ.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Typ des Felds unveränderlich ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Felddeklaration, die bewirkt, einen Verstoß gegen diese Regel dass.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]