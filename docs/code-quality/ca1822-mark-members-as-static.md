---
title: 'CA1822: Member als statisch markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ebbbbe01f1dd23dfc560e019133dacd3517b388
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253453"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Member als statisch markieren.

|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn der Member außerhalb der Assembly nicht sichtbar ist, unabhängig von der Änderung, die Sie vornehmen. Nicht unterbrechend: Wenn Sie das Element nur mit dem `this` -Schlüsselwort in einen Instanzmember ändern.<br /><br /> Unterbrechen: Wenn Sie den Member von einem Instanzmember in einen statischen Member ändern und dieser außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
Ein Member, der nicht auf Instanzdaten zugreift, ist nicht als statisch [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]gekennzeichnet (Shared in).

## <a name="rule-description"></a>Regelbeschreibung
Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Wenn nicht virtuelle Aufruf Sites ausgegeben werden, wird für jeden Aufruf, der sicherstellt, dass der aktuelle Objekt Zeiger nicht NULL ist, zur Laufzeit eine Überprüfung verhindert. Dies kann zu einer messbaren Leistungssteigerung bei Leistungs sensiblem Code werden. In einigen Fällen stellt der Fehler beim Zugriff auf die aktuelle Objektinstanz ein Problem mit der Richtigkeit dar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Markieren Sie den Member als statisch (oder frei [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]gegeben), oder verwenden Sie "This"/"Me" im Methoden Text, falls zutreffend.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel für den zuvor gelieferten Code zu unterdrücken, dessen Behebung eine Breaking Change wäre.

## <a name="related-rules"></a>Verwandte Regeln
[CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)