---
title: 'CA1021: out-Parameter vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ea5d943212122672b84376b9b3ddf5e72bb0e81f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661999"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: out-Parameter vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über einen `out`-Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Die Übergabe von Typen als Verweis (mit `out` oder `ref`) erfordert die Verwendung von Zeigern, das Verständnis der Unterschiede zwischen Werttypen und Verweis Typen sowie die Behandlung von Methoden mit mehreren Rückgabe Werten. Außerdem wird der Unterschied zwischen `out`-und `ref`-Parametern nicht weitgehend verstanden.

 Wenn ein Verweistyp als Verweis übergeben wird, beabsichtigt die Methode, den-Parameter zu verwenden, um eine andere Instanz des Objekts zurückzugeben. Die Übergabe eines Verweis Typs als Verweis wird auch als Verwendung eines doppelten Zeigers, Zeiger auf einen Zeiger oder doppelte Dereferenzierung bezeichnet. Mit der Standard Aufruf Konvention, die als Wert übergeben wird, erhält ein Parameter, der einen Verweistyp annimmt, bereits einen Zeiger auf das Objekt. Der Zeiger, nicht das Objekt, auf das es verweist, wird als Wert übermittelt. "Pass-by-Value" bedeutet, dass die Methode den Zeiger nicht ändern kann, damit Sie auf eine neue Instanz des Verweis Typs zeigt. Der Inhalt des Objekts, auf das es verweist, kann jedoch geändert werden. Bei den meisten Anwendungen ist dies ausreichend und führt zu dem gewünschten Verhalten.

 Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie den Rückgabewert der-Methode, um dies zu erreichen. Eine Reihe von Methoden, die mit Zeichen folgen arbeiten und eine neue Instanz einer Zeichenfolge zurückgeben, finden Sie in der <xref:System.String?displayProperty=fullName>-Klasse. Wenn dieses Modell verwendet wird, muss der Aufrufer entscheiden, ob das ursprüngliche Objekt beibehalten wird.

 Obwohl Rückgabewerte alltäglich und häufig verwendet werden, sind für die korrekte Anwendung von `out`-und `ref`-Parametern zwischen Entwurfs-und Codierungs Fähigkeiten erforderlich. Bibliotheks Architekten, die für eine allgemeine Zielgruppe entwerfen, sollten nicht erwarten, dass Benutzer mit `out`-oder `ref`-Parametern arbeiten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, der durch einen Werttyp verursacht wird, lassen Sie die Methode das Objekt als Rückgabewert zurückgeben. Wenn die Methode mehrere Werte zurückgeben muss, entwerfen Sie Sie so um, dass eine einzelne Instanz eines Objekts zurückgegeben wird, das die Werte enthält.

 Um einen Verstoß gegen diese Regel zu beheben, der durch einen Verweistyp verursacht wird, stellen Sie sicher, dass das gewünschte Verhalten darin besteht, eine neue Instanz des Verweises zurückzugeben. Wenn dies der Fall ist, sollte die Methode ihren Rückgabewert verwenden, um dies zu tun.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Dieser Entwurf kann jedoch Probleme mit der Benutzerfreundlichkeit verursachen.

## <a name="example"></a>Beispiel
 Die folgende Bibliothek zeigt zwei Implementierungen einer-Klasse, die Antworten auf das Feedback eines Benutzers generiert. Die erste Implementierung (`BadRefAndOut`) zwingt den Bibliotheks Benutzer, drei Rückgabewerte zu verwalten. Die zweite Implementierung (`RedesignedRefAndOut`) vereinfacht die Benutzer Leistung, indem eine Instanz einer Container Klasse (`ReplyData`) zurückgegeben wird, die die Daten als einzelne Einheit verwaltet.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung veranschaulicht die Benutzeroberflächen Darstellung. Der-Rückruf der neu gestalteten Bibliothek (`UseTheSimplifiedClass`-Methode) ist einfacher, und die von der-Methode zurückgegebenen Informationen können problemlos verwaltet werden. Die Ausgabe der beiden Methoden ist identisch.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Beispiel Bibliothek veranschaulicht, wie `ref` Parameter für Verweis Typen verwendet werden, und zeigt eine bessere Möglichkeit, diese Funktionalität zu implementieren.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung ruft jede Methode in der Bibliothek auf, um das Verhalten zu veranschaulichen.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Ändern des durch einen Wert übergebenen Zeigers:** 
**12345** 
**12345** 
**Ändern des Zeigers als Verweis übergeben:** 
**12345** 
**12345 ABCDE** 1**übergeben von Rückgabe Werten: **3**12345 ABCDE**
## <a name="try-pattern-methods"></a>Try-Muster Methoden

### <a name="description"></a>Beschreibung
 Methoden, die das **try \<Something >** -Muster implementieren, z. b. <xref:System.Int32.TryParse%2A?displayProperty=fullName>, führen diese Verletzung nicht aus. Im folgenden Beispiel wird eine Struktur (Werttyp) gezeigt, die die <xref:System.Int32.TryParse%2A?displayProperty=fullName>-Methode implementiert.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1045: Typen nicht als Verweis übergeben](../code-quality/ca1045-do-not-pass-types-by-reference.md)
