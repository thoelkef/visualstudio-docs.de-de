---
title: 'CA2111: Zeiger sollten nicht sichtbar sein | Microsoft-Dokumentation'
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
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 512d253a4e6cf4d8c92f7091d96cc747a667a646
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589676"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Zeiger sollten nicht sichtbar sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2111: Zeiger sollten nicht sichtbar sein](https://docs.microsoft.com/visualstudio/code-quality/ca2111-pointers-should-not-be-visible).

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte <xref:System.IntPtr?displayProperty=fullName> oder <xref:System.UIntPtr?displayProperty=fullName> Feld ist nicht schreibgeschützt.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.IntPtr> und <xref:System.UIntPtr> sind Zeigertypen, die für den Zugriff auf nicht verwalteten Speicher. Wenn ein Zeiger nicht privat, intern oder schreibgeschützt ist, kann bösartiger Code den Wert des Zeigers, potenziell den Zugriff auf beliebige Speicherbereiche ermöglichen oder Anwendungs-bzw. Systemfehler verursachen ändern.

 Wenn Sie zum Absichern des Zugriffs auf den Typ, die das Mauszeiger-Feld enthält beabsichtigen, finden Sie unter [CA2112: gesicherte Typen sollten keine Felder verfügbar](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Sichern Sie den Zeiger, durch die somit schreibgeschützt, intern oder privat.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht auf den Wert des Zeigers angewiesen sind.

## <a name="example"></a>Beispiel
 Der folgende Code zeigt, Zeiger, die gegen die Regel eingehalten wird. Beachten Sie, dass die nicht privater Zeiger auch die Regel verletzen [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>



