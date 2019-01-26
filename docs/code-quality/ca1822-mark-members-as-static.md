---
title: 'CA1822: Member als statisch markieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 77b256ddaff769263bcc56891ca7c0ad2be30d0c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979698"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Member als statisch markieren.

|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend – Wenn das Element nicht außerhalb der Assembly sichtbar ist müssen unabhängig von der Änderung. Nicht unterbrechend – Wenn Sie das Element auf einen Instanzmember mit ändern Sie einfach die `this` Schlüsselwort.<br /><br /> Unterbrechend – Wenn Sie das Element über ein Instanzmember in einen statischen Member ändern und außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Ein Element, das nicht auf Instanzdaten zugreift, ist nicht als statisch markiert (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Regelbeschreibung
 Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Ausgeben von Aufrufsites wird zur Laufzeit für jeden Aufruf eine Überprüfung, die sicherstellt, dass der aktuelle Objektzeiger ungleich Null ist, verhindert. Dies kann zu eine messbaren Leistungssteigerung für leistungsabhängigen Code erreichen. In einigen Fällen stellt der Fehler auf die aktuelle Objektinstanz ein Problem der Richtigkeit dar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Markieren Sie den Member als statisch (oder im freigegebenen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) oder verwenden Sie "this" / "Me" in der Methode Anforderungstext, falls zutreffend.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel für die zuvor abgelieferten Codes zu unterdrücken, für die die Lösung eine unterbrechende Änderung sein würde.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)