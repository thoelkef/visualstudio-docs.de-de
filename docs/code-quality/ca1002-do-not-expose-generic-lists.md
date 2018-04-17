---
title: 'CA1002: Machen Sie generische Listen nicht | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9aa12ea2d611d2e60e46665368b668e9c578db5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Generische Listen nicht verfügbar machen
|||  
|-|-|  
|TypeName|DoNotExposeGenericLists|  
|CheckId|CA1002|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typ enthält, die extern sichtbaren Members eine <xref:System.Collections.Generic.List%601?displayProperty=fullName> eingeben, gibt eine <xref:System.Collections.Generic.List%601?displayProperty=fullName> Typ oder enthält, dessen Signatur ein <xref:System.Collections.Generic.List%601?displayProperty=fullName> Parameter.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> ist eine generische Auflistung, die für Leistung und nicht Vererbung entwickelt wurde. <xref:System.Collections.Generic.List%601?displayProperty=fullName> enthält keine virtuellen Member, die so ändern Sie das Verhalten von einer geerbten Klasse zu vereinfachen. Die folgenden generischen Auflistungen für die Vererbung entworfen werden und verfügbar gemacht werden sollen, anstelle von <xref:System.Collections.Generic.List%601?displayProperty=fullName>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die <xref:System.Collections.Generic.List%601?displayProperty=fullName> Typ auf einen der generischen Auflistungen, die für die Vererbung entworfen wurde.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, die Assembly, die diese Warnung auslöst keiner wiederverwendbaren Bibliothek werden soll. Beispielsweise wäre es unterdrückt die Warnung in einer Anwendung für die Leistung optimiert, in denen auf ein Leistungsvorteil aus der Verwendung von generische Listen erworben wurde.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)