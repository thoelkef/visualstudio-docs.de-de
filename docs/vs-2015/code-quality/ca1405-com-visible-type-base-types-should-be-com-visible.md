---
title: 'CA1405: COM sichtbare Basistypen sollten COM sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2b107e1aa24b51de3efca8a97972c473f40a3da4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960007"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Einführung in die Klassenschnittstelle](http://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
