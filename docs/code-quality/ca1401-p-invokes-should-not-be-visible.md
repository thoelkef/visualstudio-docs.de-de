---
title: 'CA1401: P/Invokes dürfen nicht sichtbar sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e26daf68e0031358605427b310bb7284d43baf1b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922133"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes dürfen nicht sichtbar sein.

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine öffentliche oder geschützte Methode in einem öffentlichen Typ weist das <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> -Attribut auf (auch durch `Declare` das- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Schlüsselwort implementiert).

## <a name="rule-description"></a>Regelbeschreibung
Methoden, die mit dem- <xref:System.Runtime.InteropServices.DllImportAttribute> Attribut markiert sind (oder Methoden, die mit dem `Declare` -Schlüssel [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Wort in definiert werden), verwenden Platt Form Aufruf Dienste für den Zugriff auf nicht verwalteten Code. Solche Methoden sollten nicht verfügbar gemacht werden. Wenn Sie diese Methoden als privat oder intern aufbewahren, stellen Sie sicher, dass die Bibliothek nicht zum verletzen der Sicherheit verwendet werden kann, indem Sie Aufrufern Zugriff auf nicht verwaltete APIs gewähren, die nicht anderweitig aufgerufen werden konnten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene der Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird eine Methode deklariert, die gegen diese Regel verstößt.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]