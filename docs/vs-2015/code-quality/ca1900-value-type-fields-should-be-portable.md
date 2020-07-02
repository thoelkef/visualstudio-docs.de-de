---
title: 'CA1900: Werttyp Felder sollten portabel sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ece4788a277bfc4d16568d4014f9eae2ed4de33
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545274"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Werttypfelder sollten portabel sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1900: Werttyp Felder sollten portabel sein](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable).

|Element|Wert|
|-|-|
|TypName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategorie|Microsoft. Portabilität|
|Unterbrechende Änderung|Unterbrechung: Wenn das Feld außerhalb der Assembly sichtbar ist.<br /><br /> Nicht unterbrechend: Wenn das Feld außerhalb der Assembly nicht sichtbar ist.|

## <a name="cause"></a>Ursache
 Mit dieser Regel wird überprüft, ob Strukturen, die mit expliziten Layouts deklariert werden, beim Marshalling an nicht verwalteten Code auf 64-Bit-Betriebssystemen korrekt ausgerichtet werden. IA-64 lässt keine nicht ausgerichteten Speicherzugriffe zu, und der Prozess stürzt ab, wenn diese Verletzung nicht korrigiert wird.

## <a name="rule-description"></a>Beschreibung der Regel
 Strukturen mit expliziten Layouts, die falsch ausgerichtete Felder enthalten, verursachen Abstürze bei 64-Bit-Betriebssystemen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Alle Felder, die kleiner als 8 Bytes sind, müssen Offsets aufweisen, die ein Vielfaches ihrer Größe aufweisen, und Felder, die 8 Bytes oder mehr umfassen, müssen Offsets aufweisen, die ein Vielfaches von 8 sind. Eine andere Lösung ist `LayoutKind.Sequential` `LayoutKind.Explicit` , wenn vernünftig, anstelle von zu verwenden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Warnung sollte nur unterdrückt werden, wenn Sie fehlerhaft auftritt.
