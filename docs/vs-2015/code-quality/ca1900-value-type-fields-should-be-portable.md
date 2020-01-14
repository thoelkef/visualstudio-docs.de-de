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
ms.openlocfilehash: 23b5705b7ee81e56945050fe63dd2f086894bd08
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917929"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Werttypfelder sollten portabel sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1900: Werttyp Felder sollten portabel sein](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable).

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategorie|Microsoft.Portability|
|Unterbrechende Änderung|Unterbrechung: Wenn das Feld außerhalb der Assembly sichtbar ist.<br /><br /> Nicht unterbrechend: Wenn das Feld außerhalb der Assembly nicht sichtbar ist.|

## <a name="cause"></a>Ursache
 Mit dieser Regel wird überprüft, ob Strukturen, die mit expliziten Layouts deklariert werden, beim Marshalling an nicht verwalteten Code auf 64-Bit-Betriebssystemen korrekt ausgerichtet werden. IA-64 lässt keine nicht ausgerichteten Speicherzugriffe zu, und der Prozess stürzt ab, wenn diese Verletzung nicht korrigiert wird.

## <a name="rule-description"></a>Regelbeschreibung
 Strukturen mit expliziten Layouts, die falsch ausgerichtete Felder enthalten, verursachen Abstürze bei 64-Bit-Betriebssystemen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Alle Felder, die kleiner als 8 Bytes sind, müssen Offsets aufweisen, die ein Vielfaches ihrer Größe aufweisen, und Felder, die 8 Bytes oder mehr umfassen, müssen Offsets aufweisen, die ein Vielfaches von 8 sind. Eine andere Lösung besteht in der Verwendung von `LayoutKind.Sequential` anstelle `LayoutKind.Explicit`, wenn dies angemessen ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Warnung sollte nur unterdrückt werden, wenn Sie fehlerhaft auftritt.
