---
title: 'CA1822: Member als statisch markieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 498a3638a02891683aff1b343431418d1a82bab0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Member als statisch markieren
|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der Member nicht außerhalb der Assembly sichtbar ist müssen unabhängig von der Änderung. Nicht unterbrechend – Wenn Sie nur das Element auf ein Instanzmember mit ändern die `this` Schlüsselwort.<br /><br /> Unterbrechend – Wenn Sie das Element über einen Instanzmember in ein statisches Element ändern, und er außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Ein Element, das nicht auf Instanzdaten zugreift, ist nicht als static markiert (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Regelbeschreibung
 Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Ausgeben von Aufrufsites verhindert eine Überprüfung zur Laufzeit für jeden Aufruf, der sicherstellt, dass der aktuelle Objektzeiger ungleich Null ist. Dies kann zu eine messbaren Leistungssteigerung für leistungsabhängigen Code erreichen. In einigen Fällen stellt der Fehler auf die aktuelle Objektinstanz ein Problem auf Richtigkeit.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Markieren Sie den Member als statisch (oder im freigegebenen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) oder verwenden Sie "this" / "Me" in der Methode Anforderungstext, falls zutreffend.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel für zuvor gelieferten Code, für den die Lösung eine unterbrechende Änderung wäre.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)