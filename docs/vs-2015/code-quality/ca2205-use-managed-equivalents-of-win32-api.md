---
title: 'CA2205: Verwaltete Entsprechungen der Win32-API | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ba23b176ed4f2120f4675611567955bdaf652153
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907468"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Verwaltete Entsprechungen der Win32 API verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Rufen Sie eine Plattform ist definiert, und eine Methode mit der entsprechenden Funktionalität vorhanden ist, der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] -Klassenbibliothek.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Plattformaufrufmethode wird verwendet, um eine nicht verwaltete DLL-Funktion aufrufen und wird mit definiert die <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> -Attribut, oder die `Declare` -Schlüsselwort in Visual Basic. Ein falsch definierten Plattformaufrufmethode zu Runtime-Ausnahmen führen kann, die aufgrund von Problemen wie z. B. einen falsch geschriebenen Funktion, die fehlerhafte Zuordnung von Datentypen der Parameter und Rückgabetypen Werten und falschen Feld-Spezifikationen wie die Aufrufkonvention und das Zeichen Legen Sie. Falls verfügbar, ist es in der Regel einfacher und weniger fehleranfällig, rufen Sie die entsprechende verwaltete Methode als zum Definieren und die nicht verwaltete Methode direkt aufzurufen. Aufrufen einer Plattform invoke-Methode kann auch zu Problemen führen, zusätzliche Sicherheit, die berücksichtigt werden müssen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Aufruf an die nicht verwaltete Funktion mit einem Aufruf von seinem verwalteten Gegenwert fest.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, wenn die vorgeschlagene Ersetzungsmethode nicht die benötigte Funktionalität bietet.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Plattform rufen die Definition einer Methode, die die Regel verletzen. Darüber hinaus die Aufrufe an die Plattform Methode aufrufen und die entsprechende verwaltete Methode werden angezeigt.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1404: GetLastError unmittelbar nach P-Invoke aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: P-Invokes in NativeMethods-Klasse verschieben](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Für P-Invoke müssen Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P-Invokes dürfen nicht sichtbar sein](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Marshalling für P-Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)



