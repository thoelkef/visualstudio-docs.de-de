---
title: 'CA2205: Verwaltete Entsprechungen der Win32 API verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0d9ae35155009e43678aca89e388ebac721a5724
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551240"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Verwaltete Entsprechungen der Win32 API verwenden

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Rufen Sie eine Plattform ist definiert, und eine Methode mit der entsprechenden Funktionalität vorhanden ist, der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] -Klassenbibliothek.

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

- [CA1404: GetLastError unmittelbar nach P-Invoke aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: P-Invokes in NativeMethods-Klasse verschieben](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: Für P-Invoke müssen Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P-Invokes dürfen nicht sichtbar sein](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Marshalling für P-Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)