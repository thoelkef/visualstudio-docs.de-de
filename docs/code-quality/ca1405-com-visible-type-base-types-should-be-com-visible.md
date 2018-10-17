---
title: 'CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: efaac5fc5b5f8784d204c31e537a5279a81e2699
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548280"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|DependsOnFix|

## <a name="cause"></a>Ursache
 Sichtbarer Typ Component Object Model (COM) leitet sich von einem Typ, der nicht für COM sichtbar ist.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn COM sichtbarer Typ Member in einer neuen Version hinzufügt, müssen sie halten Sie sich an strenge Richtlinien, die zu vermeiden, dass der COM-Clients, die auf die aktuelle Version zu binden. Ein Typ, der für COM nicht sichtbar ist wird davon ausgegangen, dass es keine diese COM-Versionsregeln folgen, wenn neue Elemente hinzugefügt. Wenn jedoch eine COM-sichtbar Typ leitet sich von der COM-Typ nicht sichtbar, und stellt eine Schnittstelle für Klassen von <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ClassInterfaceType> (Standardeinstellung), alle öffentlichen Member des Basistyps (es sei denn, sie explizit als COM unsichtbar markiert sind, was wäre redundant) sind für COM verfügbar gemacht Der Basistyp neue Elemente in einer späteren Version hinzugefügt wird, können zur funktionsunfähigkeit von COM-Clients, die auf die Schnittstelle des abgeleiteten Typs binden. Für COM sichtbare Typen sollten nur für COM sichtbare Typen, um das Risiko der Unterbrechung COM-Clients zu reduzieren abgeleitet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die Basistypen für COM sichtbar oder den abgeleiteten Typ für COM nicht sichtbar.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)