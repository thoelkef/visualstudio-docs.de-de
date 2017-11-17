---
title: 'CA2205: Verwenden Sie verwaltete Entsprechungen der Win32-API | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cbdc02843d0a2982a129dafd5948a4c1ab287427
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Verwaltete Entsprechungen der Win32 API verwenden
|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein Plattformaufruf Methode definiert ist, und eine Methode mit entsprechender Funktionalität vorhanden ist, der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] -Klassenbibliothek.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein Plattformaufruf-Methode wird verwendet, um eine nicht verwaltete DLL-Funktion aufrufen und mithilfe der <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> -Attribut, oder die `Declare` -Schlüsselwort in Visual Basic. Falsch definierten Plattformaufrufmethode zu Runtime-Ausnahmen führen kann, die aufgrund von Verbindungsproblemen, wie z. B. einen falsch geschriebenen Funktion, die fehlerhafte Zuordnung von Parameter- und Rückgabetypen von Datentypen mit Werten und falschen Feld Spezifikationen, z. B. die Aufrufkonvention und das Zeichen festgelegt. Falls verfügbar, ist es im Allgemeinen einfacher und weniger fehleranfällig, rufen Sie die entsprechende verwaltete Methode als zum Definieren und die nicht verwaltete Methode direkt aufzurufen. Aufrufen einer Plattformaufrufs invoke-Methode kann ebenfalls dazu führen, um zusätzliche Sicherheitsprobleme, die behoben werden müssen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Aufruf an die nicht verwaltete Funktion durch einen Aufruf in den entsprechenden verwalteten ein.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn die vorgeschlagene Ersetzungsmethode nicht die erforderliche Funktionalität bereitstellt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Plattform rufen Sie die Definition der Methode, die die Regel verletzt. Darüber hinaus die Aufrufe an die Plattform invoke-Methode und die entsprechende verwaltete Methode werden angezeigt.  
  
 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [: Ca1404 GetLastError unmittelbar nach P/Invoke aufrufen](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: Move P/Invokes in NativeMethods-Klasse](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: P/Invoke müssen Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invokes dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [: Ca2101 Marshalling für P/Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)