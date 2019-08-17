---
title: 'CA1003: Generische Ereignishandlerinstanzen verwenden.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a1ef4258d1b095395be34c7004e3f783b973897d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547876"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Generische Ereignishandlerinstanzen verwenden.

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ enthält einen Delegaten, der "void" zurückgibt und dessen Signatur zwei Parameter enthält (das erste Objekt und das zweite einen Typ, der EventArgs zugewiesen werden kann), und die enthaltende Assembly als Ziel .net.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Vor .net musste ein neuer Delegat deklariert werden, der eine von der <xref:System.EventArgs?displayProperty=fullName> -Klasse abgeleitete Klasse angibt, um benutzerdefinierte Informationen an den-Ereignishandler zu übergeben. In .NET ermöglicht der generische <xref:System.EventHandler%601?displayProperty=fullName> -Delegat, dass jede von <xref:System.EventArgs> abgeleitete Klasse mit dem-Ereignishandler verwendet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den-Delegaten, und ersetzen <xref:System.EventHandler%601?displayProperty=fullName> Sie dessen Verwendung mithilfe des-Delegaten.

Wenn der Delegat automatisch vom Visual Basic-Compiler generiert wird, ändern Sie die Syntax der Ereignis Deklaration, <xref:System.EventHandler%601?displayProperty=fullName> um den Delegaten zu verwenden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Delegaten, der gegen die Regel verstößt. Im Visual Basic Beispiel wird beschrieben, wie Sie das Beispiel ändern, um die Regel zu erfüllen. Im C# Beispiel folgt ein Beispiel, das den geänderten Code anzeigt.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Der folgende Code Ausschnitt entfernt die Delegatdeklaration aus dem vorherigen Beispiel, die die Regel erfüllt. Er ersetzt seine Verwendung in den `ClassThatRaisesEvent` Methoden `ClassThatHandlesEvent` und mithilfe des <xref:System.EventHandler%601?displayProperty=fullName> -Delegaten.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1005: Übermäßige Parameter für generische Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Sammlungen sollten eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Generische Typen in Element Signaturen nicht Schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Generische Methoden sollten Typparameter bereitstellen.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Generika ggf. verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch

- [Generika](/dotnet/csharp/programming-guide/generics/index)