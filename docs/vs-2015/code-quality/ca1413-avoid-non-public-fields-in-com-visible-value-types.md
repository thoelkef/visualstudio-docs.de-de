---
title: 'CA1413: nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7d66c2c52b6ee7f7d1d2fbbd461ca8c1251ce13d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652701"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Kategorie|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Werttyp, der speziell für Component Object Model (com) als sichtbar gekennzeichnet ist, deklariert ein nicht öffentliches Instanzfeld.

## <a name="rule-description"></a>Regelbeschreibung
 Nicht öffentliche Instanzenfelder von COM-sichtbaren Werttypen sind für COM-Clients sichtbar. Überprüfen Sie den Inhalt des Felds auf Informationen, die nicht verfügbar gemacht werden sollen oder die einen unbeabsichtigten Entwurf oder sicherheitseffekt haben.

 Standardmäßig sind alle öffentlichen Werttypen für com sichtbar. Um falsch positive Ergebnisse zu reduzieren, erfordert diese Regel jedoch, dass die COM-Sichtbarkeit des Typs explizit angegeben wird. Die enthaltende Assembly muss mit dem <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> als `false` markiert werden, und der Typ muss mit dem <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf `true` festgelegt sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben und das Feld ausgeblendet zu lassen, ändern Sie den Werttyp in einen Verweistyp, oder entfernen Sie das <xref:System.Runtime.InteropServices.ComVisibleAttribute> Attribut aus dem Typ.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die öffentliche verfügbar machung des Felds akzeptabel ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Siehe auch
 Interoperabilität [mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [qualifizieren von .NET-Typen für die Interoperation](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
