---
title: 'CA2111: Zeiger sollten nicht sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0d5546c6f6a2f5dbd0c6063f4a1dfd40ce1d7bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658734"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Zeiger sollten nicht sichtbar sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentliches oder geschütztes <xref:System.IntPtr?displayProperty=fullName> oder <xref:System.UIntPtr?displayProperty=fullName> Feld ist nicht schreibgeschützt.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.IntPtr> und <xref:System.UIntPtr> sind Zeiger Typen, die für den Zugriff auf nicht verwalteten Speicher verwendet werden. Wenn ein Zeiger nicht privat, intern oder schreibgeschützt ist, kann bösartiger Code den Wert des Zeigers ändern und möglicherweise den Zugriff auf beliebige Speicherorte im Arbeitsspeicher erlauben oder Anwendungs-oder Systemfehler verursachen.

 Wenn Sie den Zugriff auf den Typ, der das Zeiger Feld enthält, sichern möchten, finden Sie unter [CA2112: gesicherte Typen sollten keine Felder](../code-quality/ca2112-secured-types-should-not-expose-fields.md)verfügbar machen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Sichern Sie den Zeiger, indem Sie ihn als schreibgeschützt, intern oder privat festlegen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn Sie sich nicht auf den Wert des Zeigers verlassen.

## <a name="example"></a>Beispiel
 Der folgende Code zeigt Zeiger, die die Regel verletzen und erfüllen. Beachten Sie, dass die nicht privaten Zeiger auch gegen die Regel [CA1051 verstoßen: sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
