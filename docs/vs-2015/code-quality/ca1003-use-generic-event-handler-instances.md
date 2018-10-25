---
title: 'CA1003: Generische Ereignishandlerinstanzen verwenden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3c2cf2ad59f7ade337c84f13133bb5181afb615
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929087"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Generische Ereignishandlerinstanzen verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ enthält einen Delegaten, die "void" zurückgibt, deren Signatur enthält zwei Parameter (der erste ist ein Objekt und das zweite ein Typ, der EventArgs zugewiesen werden) und die Ziele der enthaltenden Assembly [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Regelbeschreibung
 Vor dem [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], um benutzerdefinierte Informationen an den Ereignishandler übergeben musste, dass ein neuer Delegat deklariert werden, die eine Klasse, die von abgeleitet wurde angegeben, die <xref:System.EventArgs?displayProperty=fullName> Klasse. Dies ist nicht mehr in "true" [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], eingeführt, die <xref:System.EventHandler%601?displayProperty=fullName> delegieren. Dieser generische Delegat kann jede Klasse, die abgeleitet wird <xref:System.EventArgs> , zusammen mit der Ereignishandler verwendet werden soll.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Delegaten, und Ersetzen Sie die Verwendung durch die <xref:System.EventHandler%601?displayProperty=fullName> delegieren. Wenn der Delegat automatisch von der [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] -Compiler, ändern Sie die Syntax der Deklaration des Ereignisses mit der <xref:System.EventHandler%601?displayProperty=fullName> delegieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Delegat, der gegen die Regel verstößt. In der [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] beispielsweise Kommentare beschrieben, wie Sie das Beispiel, um die Regel erfüllen zu ändern. Für das C#-Beispiel folgt ein Beispiel, das den geänderten Code zeigt.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel entfernt der Delegatdeklaration überein, aus dem vorherigen Beispiel, in der Regel entspricht, und ersetzt die Verwendung in der `ClassThatRaisesEvent` und `ClassThatHandlesEvent` Methoden mithilfe der <xref:System.EventHandler%601?displayProperty=fullName> delegieren.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
 [Generika](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



