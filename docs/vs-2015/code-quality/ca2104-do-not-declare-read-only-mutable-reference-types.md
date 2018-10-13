---
title: 'CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren | Microsoft-Dokumentation'
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
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f8e8ce2c8c6ac780dc3233fdac5c668576ac7b35
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279343"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Schreibgeschützte änderbare Referenztypen nicht deklarieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ enthält ein extern sichtbares schreibgeschütztes Feld, bei dem es sich um einen änderbaren Referenztyp handelt.

## <a name="rule-description"></a>Regelbeschreibung
 Ein änderbarer Typ ist ein Typ, dessen Instanzdaten geändert werden können. Die <xref:System.Text.StringBuilder?displayProperty=fullName> Klasse ist ein Beispiel für einen änderbaren Referenztyp. Es enthält Elemente, die den Wert einer Instanz der Klasse ändern können. Ein Beispiel für einen unveränderlichen Referenztyp ist der <xref:System.String?displayProperty=fullName> Klasse. Nach der sie instanziiert wurde, kann ihr Wert niemals ändern.

 Die schreibgeschützten Modifizierer ([Readonly](http://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) in c# [ReadOnly](http://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], und [const](http://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) in C++) auf einem Verweistyp (Zeiger in C++) verhindert, dass das Feld wird ersetzt durch eine andere Instanz des Verweistyps. Allerdings verhindert der Modifizierer der Instanzdaten des Felds nicht, die durch den Verweistyp geändert wird.

 Schreibgeschützte Arrayfelder sind von dieser Regel ausgenommen verursachen jedoch stattdessen einen Verstoß gegen die [CA2105: Arrayfelder sollte nicht schreibgeschützt sein](../code-quality/ca2105-array-fields-should-not-be-read-only.md) Regel.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den schreibgeschützten Modifizierer oder, wenn eine wichtige Änderung akzeptabel ist, ersetzen Sie das Feld mit einem unveränderlichen Typ.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Feldtyp unveränderlich ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Felddeklaration, die bewirkt, einen Verstoß gegen diese Regel dass.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]



