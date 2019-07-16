---
title: 'CA1400: P / Invoke-Einstiegspunkte an müssen vorhanden sein. | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0e5696689d0aa40f4af2e11970c81b47737a3d80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200375"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Für P/Invoke müssen Einstiegspunkte vorhanden sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode wird markiert, mit der <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden. Wenn die Regel der Name der Methode nicht finden kann, genau, wie sie angegeben ist, sucht es ANSI- oder Breitzeichen-Versionen der Methode Breitzeichenformat der Name der Methode mit "A" oder "W". Wenn keine Übereinstimmung gefunden wird, wird die Regel versucht, eine Funktion zu ermitteln, indem Sie mit das Format des __stdcall (_MyMethod@12, wobei 12 die Länge der Argumente darstellt). Wenn keine Übereinstimmung gefunden wird, und der Name der Methode beginnt mit "#", sucht die Regel für die Funktion, als Ordnungszahlverweis statt einem Namensverweis auf.

## <a name="rule-description"></a>Regelbeschreibung
 Keine kompilierzeitüberprüfung ist verfügbar, um sicherzustellen, dass Methoden, die mit markierten Felder <xref:System.Runtime.InteropServices.DllImportAttribute> befinden sich in der auf die verwiesen wird, nicht verwalteten DLL. Wenn keine Funktion, die dem angegebenen Namen in der Bibliothek ist, oder die Argumente an die Methode die Funktionsargumente nicht übereinstimmen, löst die common Language Runtime eine Ausnahme aus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Methode, wurden die <xref:System.Runtime.InteropServices.DllImportAttribute> Attribut. Stellen Sie sicher, dass die nicht verwaltete Bibliothek vorhanden und befindet sich im selben Verzeichnis wie die Assembly, die die Methode enthält. Ist die Bibliothek vorhanden und ordnungsgemäß auf die verwiesen wird, stellen Sie sicher, dass die Methodennamen, Rückgabetyp und Argumentsignatur die Bibliotheksfunktion übereinstimmen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, wenn die nicht verwaltete Bibliothek im gleichen Verzeichnis wie die verwaltete Assembly ist, auf die verwiesen, wird. Möglicherweise eine Warnung dieser Regel im Fall unterdrückt, die nicht verwaltete Bibliothek nicht gefunden werden kann.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. Keine Funktion mit dem Namen `DoSomethingUnmanaged` tritt in "Kernel32.dll".

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
