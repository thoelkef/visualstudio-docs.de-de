---
title: 'CA1400: P-aufrufende Einstiegspunkte müssen vorhanden sein | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 15b63e49f89e17db631772c48765cc610f47ed29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548303"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Für P/Invoke müssen Einstiegspunkte vorhanden sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode wird mit dem gekennzeichnet <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden. Wenn die Regel den Methodennamen nicht genau so finden kann, wie er angegeben ist, sucht er nach ANSI-oder breit Zeichen Versionen der-Methode, indem er mit "A" oder "W" dem Methodennamen genügt. Wenn keine Entsprechung gefunden wird, versucht die Regel, eine Funktion mit dem __stdcall Namensformat ( _MyMethod@12 , wobei 12 die Länge der Argumente darstellt) zu suchen. Wenn keine Entsprechung gefunden wird und der Methodenname mit "#" beginnt, sucht die Regel nach der Funktion als Ordinalverweis anstelle eines Namens Verweises.

## <a name="rule-description"></a>Beschreibung der Regel
 Es ist keine Kompilierzeit Überprüfung verfügbar, um sicherzustellen, dass mit markierte Methoden <xref:System.Runtime.InteropServices.DllImportAttribute> in der nicht verwalteten DLL gefunden werden, auf die verwiesen wird. Wenn sich keine Funktion mit dem angegebenen Namen in der Bibliothek befindet oder die Argumente der Methode nicht mit den Funktions Argumenten identisch sind, löst der Common Language Runtime eine Ausnahme aus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Methode, die über das- <xref:System.Runtime.InteropServices.DllImportAttribute> Attribut verfügt. Stellen Sie sicher, dass die nicht verwaltete Bibliothek vorhanden ist und sich im selben Verzeichnis befindet wie die Assembly, die die Methode enthält. Wenn die Bibliothek vorhanden ist und ordnungsgemäß referenziert ist, überprüfen Sie, ob der Methodenname, der Rückgabetyp und die Argument Signatur der Bibliotheksfunktion entsprechen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, wenn sich die nicht verwaltete Bibliothek im selben Verzeichnis befindet wie die verwaltete Assembly, die darauf verweist. Es ist möglicherweise sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die nicht verwaltete Bibliothek nicht gefunden wurde.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. In kernel32.dll wird keine Funktion mit dem Namen angezeigt `DoSomethingUnmanaged` .

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
