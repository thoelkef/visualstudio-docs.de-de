---
title: 'CA2205: verwaltete Entsprechungen der Win32-API verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 931b1e5099bf221fefc7a8f4a19524d2531a4418
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609486"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Verwaltete Entsprechungen der Win32 API verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Platt Form Aufruf Methode ist definiert, und in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Klassenbibliothek ist eine Methode mit der entsprechenden Funktionalität vorhanden.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Platt Form Aufruf Methode wird verwendet, um eine nicht verwaltete DLL-Funktion aufzurufen, und wird mithilfe des <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>-Attributs oder des Schlüssel Worts `Declare` in Visual Basic definiert. Eine fälschlicherweise definierte Platt Form Aufruf Methode kann aufgrund von Problemen, wie z. b. einer falsch benannten Funktion, fehlerhafter Zuordnung von Parameter-und Rückgabewert Datentypen und falscher Feld Spezifikationen, wie z. b. der Aufruf Konvention und des Zeichens, zu Lauf Zeit Ausnahmen führen Set. Falls verfügbar, ist es in der Regel einfacher und weniger fehleranfällig, die entsprechende verwaltete Methode aufzurufen, als die nicht verwaltete Methode direkt zu definieren und aufzurufen. Das Aufrufen einer Platt Form Aufruf Methode kann auch zu zusätzlichen Sicherheitsproblemen führen, die behoben werden müssen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den-Befehl für die nicht verwaltete Funktion durch einen-Aufrufwert.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn die vorgeschlagene Ersetzungs Methode nicht die erforderliche Funktionalität bereitstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Platt Form Aufruf Methoden Definition, die gegen die Regel verstößt. Außerdem werden die Aufrufe der Platt Form Aufruf Methode und der entsprechenden verwalteten Methode angezeigt.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1404: GetLastError unmittelbar nach P-Invoke aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: P-Invokes in NativeMethods-Klasse verschieben](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Für P-Invoke müssen Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P-Invokes dürfen nicht sichtbar sein](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Marshalling für P-Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
