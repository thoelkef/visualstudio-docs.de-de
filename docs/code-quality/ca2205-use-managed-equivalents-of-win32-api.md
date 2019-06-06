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
ms.openlocfilehash: 99d53296ad72aef1910a39299be64c7cb03dd49a
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714719"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Verwaltete Entsprechungen der Win32 API verwenden.

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Rufen Sie eine Plattform ist definiert, und eine Methode mit der entsprechenden Funktionalität, die in .NET vorhanden ist.

## <a name="rule-description"></a>Regelbeschreibung

Eine Plattformaufrufmethode wird verwendet, um eine nicht verwaltete DLL-Funktion aufrufen und wird mit definiert die <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> -Attribut, oder die `Declare` -Schlüsselwort in Visual Basic. Ein falsch definierten Plattformaufrufmethode zu Runtime-Ausnahmen führen kann, die aufgrund von Problemen wie z. B. einen falsch geschriebenen Funktion, die fehlerhafte Zuordnung von Datentypen der Parameter und Rückgabetypen Werten und falschen Feld-Spezifikationen wie die Aufrufkonvention und das Zeichen Legen Sie. Falls verfügbar, ist es einfacher und weniger fehleranfällig, rufen Sie die entsprechende verwaltete Methode als zum Definieren und die nicht verwaltete Methode direkt aufzurufen. Aufrufen einer Plattform invoke-Methode kann auch zu Problemen führen, zusätzliche Sicherheit, die berücksichtigt werden müssen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Aufruf an die nicht verwaltete Funktion mit einem Aufruf von seinem verwalteten Gegenwert fest.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel, wenn die vorgeschlagene Ersetzungsmethode nicht die benötigte Funktionalität bietet.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Plattform rufen die Definition einer Methode, die die Regel verletzen. Darüber hinaus die Aufrufe an die Plattform Methode aufrufen und die entsprechende verwaltete Methode werden angezeigt.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1404: GetLastError unmittelbar nach P/Invoke aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Verschieben von P/Invokes in NativeMethods-Klasse](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: P/Invoke-Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P/Invokes dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Geben Sie die Marshalling für P/Invoke-Zeichenfolgenargumente](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)