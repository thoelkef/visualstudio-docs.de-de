---
title: 'CA2205: Verwaltete Entsprechungen der Win32 API verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ad26dcbbbef5a34796ca0aa134653c3c9df5d763
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253259"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Verwaltete Entsprechungen der Win32 API verwenden.

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Platt Form Aufruf Methode ist definiert, und eine Methode mit der entsprechenden Funktionalität ist in .net vorhanden.

## <a name="rule-description"></a>Regelbeschreibung

Eine Platt Form Aufruf Methode wird verwendet, um eine nicht verwaltete DLL-Funktion aufzurufen, <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> und wird mithilfe des `Declare` -Attributs oder des-Schlüssel Worts in Visual Basic definiert. Eine falsch definierte Platt Form Aufruf Methode kann aufgrund von Problemen, wie z. b. einer falsch benannten Funktion, fehlerhafter Zuordnung von Parameter-und Rückgabewert Datentypen und falscher Feld Spezifikationen, wie z. b. der Aufruf Konvention und des Zeichens, zu Lauf Zeit Ausnahmen führen. Set. Falls verfügbar, ist es einfacher und weniger fehleranfällig, die entsprechende verwaltete Methode aufzurufen, als die nicht verwaltete Methode direkt zu definieren und aufzurufen. Das Aufrufen einer Platt Form Aufruf Methode kann auch zu zusätzlichen Sicherheitsproblemen führen, die behoben werden müssen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den-Befehl für die nicht verwaltete Funktion durch einen-Aufrufwert.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrückt eine Warnung aus dieser Regel, wenn die vorgeschlagene Ersetzungs Methode nicht die erforderliche Funktionalität bereitstellt.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Platt Form Aufruf Methoden Definition, die gegen die Regel verstößt. Außerdem werden die Aufrufe der Platt Form Aufruf Methode und der entsprechenden verwalteten Methode angezeigt.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1404: GetLastError unmittelbar nach P/aufrufen aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Verschieben von P/aufrufen in die NativeMethods-Klasse](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: P/aufrufende Einstiegspunkte müssen vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P/Aufrufe dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Marshalling für P/Aufruf-Zeichen folgen Argumente angeben](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)