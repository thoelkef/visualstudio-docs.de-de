---
title: "CA1400: P / Invoke müssen Einstiegspunkte vorhanden sein | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95e4b0841cfed5ae5ba2428a9a38da2ab43b8527
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Für P/Invoke müssen Einstiegspunkte vorhanden sein
|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|CheckId|CA1400|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine öffentliche oder geschützte Methode wird mit markiert die <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden. Wenn die Regel den Methodennamen nicht finden kann, genau so, wie es angegeben wird, sucht es ANSI- oder Breitzeichenversionen der Methode Breitzeichenformat Namen der Methode mit "A" oder "W". Wenn keine Übereinstimmung gefunden wird, versucht die Regel, die eine Funktion zu suchen, indem Sie das Format des __stdcall (_MyMethod@12, wobei 12 die Länge der Argumente darstellt). Wenn keine Übereinstimmung gefunden wird, und der Name der Methode beginnt mit "#", sucht die Regel für die Funktion als Ordnungszahlverweis anstelle eines Verweises Name angezeigt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Keine Überprüfung der Kompilierzeit ist verfügbar, um sicherzustellen, dass mit markierte Methoden <xref:System.Runtime.InteropServices.DllImportAttribute> befinden sich im nicht verwalteten DLL verwiesen wird. Wenn keine Funktion mit dem angegebenen Namen in der Bibliothek ist, oder die Argumente der Methode nicht der Funktionsargumente entsprechen, löst die common Language Runtime eine Ausnahme aus.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Methode, die die <xref:System.Runtime.InteropServices.DllImportAttribute> Attribut. Stellen Sie sicher, dass die nicht verwaltete Bibliothek vorhanden und befindet sich im selben Verzeichnis wie die Assembly, die die Methode enthält. Ist die Bibliothek vorhanden ist und dass ordnungsgemäß auf die verwiesen wird, stellen Sie sicher, dass die Methodennamen, Rückgabetyp und Argumentsignatur Bibliotheksfunktion übereinstimmen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, wenn die nicht verwaltete Bibliothek im selben Verzeichnis wie die verwaltete Assembly ist, die darauf verweist. Möglicherweise eine Warnung dieser Regel im Fall unterdrückt, in denen die nicht verwaltete Bibliothek nicht gefunden werden konnte.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt. Keine Funktion mit dem Namen `DoSomethingUnmanaged` kernel32.dll auftritt.  
  
 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>