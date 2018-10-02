---
title: 'CA2130: Sicherheitskritische Konstanten sollten transparent sein | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a74d6fe3c0507914fa4bd9723a53579db230c467
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589596"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Sicherheitskritische Konstanten sollten transparent sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2130: sicherheitskritische Konstanten sollten transparent sein](https://docs.microsoft.com/visualstudio/code-quality/ca2130-security-critical-constants-should-be-transparent).

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein konstantes Feld oder ein Enumerationsmember ist mit markiert die <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Regelbeschreibung
 Transparenzerzwingung wird nicht für konstante Werte erzwungen, da Compiler konstante Werte inline verwenden, damit zur Laufzeit keine Suche erforderlich ist. Konstante Felder sollten sicherheitstransparent sein, damit Codebearbeiter nicht davon ausgehen, dass dieser transparente Code nicht auf die Konstante zugreifen kann.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das SecurityCritical-Attribut aus dem Feld oder einen Wert ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In den folgenden Beispielen wird der Enum-Wert `EnumWithCriticalValues.CriticalEnumValue` und die Konstante `CriticalConstant` diese Warnung auslösen. Um die Probleme zu beheben, entfernen Sie die [`SecurityCritical`]-Attribut diese transparent zu gestalten.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]



