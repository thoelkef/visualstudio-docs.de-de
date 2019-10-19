---
title: 'CA1822: Member als statisch markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a571be6b713cd59ca290906e9398b78c8c021ba8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661169"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Member als statisch markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1822: Markieren](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static)von Membern als statisch.

|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|CheckId|CA1822|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn der Member außerhalb der Assembly nicht sichtbar ist, unabhängig von der Änderung, die Sie vornehmen.<br /><br /> Nicht unterbrechend: Wenn Sie das Element nur mit dem `this`-Schlüsselwort in einen Instanzmember ändern.<br /><br /> Unterbrechen: Wenn Sie den Member von einem Instanzmember in einen statischen Member ändern und dieser außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Ein Member, der nicht auf Instanzdaten zugreift, ist nicht als statisch gekennzeichnet (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] freigegeben).

## <a name="rule-description"></a>Regelbeschreibung
 Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus. Durch das Ausgeben von nicht virtuellen-Aufrufsites wird für jeden-Befehl, der sicherstellt, dass der aktuelle Objekt Zeiger nicht NULL ist, zur Laufzeit eine Überprüfung verhindert. Dies kann zu einer messbaren Leistungssteigerung bei Leistungs sensiblem Code werden. In einigen Fällen stellt der Fehler beim Zugriff auf die aktuelle Objektinstanz ein Problem mit der Richtigkeit dar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Markieren Sie den Member als statisch (oder in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] freigegeben), oder verwenden Sie "This"/"Me" im Methoden Text, falls zutreffend.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel für den zuvor gelieferten Code zu unterdrücken, dessen Behebung eine Breaking Change wäre.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
