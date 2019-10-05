---
title: 'CA1400: Für P/Invoke müssen Einstiegspunkte vorhanden sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5503f00995a4720207ea0ea9c29201d379e70adb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234902"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Für P/Invoke müssen Einstiegspunkte vorhanden sein.

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine öffentliche oder geschützte Methode wird mit dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>gekennzeichnet. Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden. Wenn die Regel den Methodennamen nicht genau so finden kann, wie er angegeben ist, sucht er nach ANSI-oder breit Zeichen Versionen der-Methode, indem er mit "A" oder "W" dem Methodennamen genügt. Wenn keine Entsprechung gefunden wird, versucht die Regel, eine Funktion mit dem Format "__stdcall Name"_MyMethod@12zu suchen (, wobei "12" die Länge der Argumente darstellt). Wenn keine Entsprechung gefunden wird und der Methodenname mit "#" beginnt, sucht die Regel nach der Funktion als Ordinalverweis anstelle eines Namens Verweises.

## <a name="rule-description"></a>Regelbeschreibung
Es ist keine Kompilierzeit Überprüfung verfügbar, um sicherzustellen, dass mit <xref:System.Runtime.InteropServices.DllImportAttribute> markierte Methoden in der nicht verwalteten DLL gefunden werden, auf die verwiesen wird. Wenn sich keine Funktion mit dem angegebenen Namen in der Bibliothek befindet oder die Argumente der Methode nicht mit den Funktions Argumenten identisch sind, löst der Common Language Runtime eine Ausnahme aus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Methode, <xref:System.Runtime.InteropServices.DllImportAttribute> die über das-Attribut verfügt. Stellen Sie sicher, dass die nicht verwaltete Bibliothek vorhanden ist und sich im selben Verzeichnis befindet wie die Assembly, die die Methode enthält. Wenn die Bibliothek vorhanden ist und ordnungsgemäß referenziert ist, überprüfen Sie, ob der Methodenname, der Rückgabetyp und die Argument Signatur der Bibliotheksfunktion entsprechen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel, wenn sich die nicht verwaltete Bibliothek im selben Verzeichnis befindet wie die verwaltete Assembly, die darauf verweist. Es ist möglicherweise sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die nicht verwaltete Bibliothek nicht gefunden wurde.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. In Kernel32. dll tritt `DoSomethingUnmanaged` keine Funktion mit dem Namen auf.

[!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>