---
title: "CA1045: Typen nicht als Verweis übergeben | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7542e21963f272dd10180203a52bee9994de2cdc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Typen nicht als Verweis übergeben
|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ hat einen `ref` Parameter, der ein primitiver Typ, ein Verweistyp oder ein Werttyp ist, akzeptiert ist keiner der integrierten Typen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die Übergabe von Typen als Verweis (mit `out` oder `ref`) erfordert Erfahrung mit Zeigern, Kenntnisse der Unterschiede zwischen Wert- und Verweistypen und zum Behandeln von Methoden mit mehreren Rückgabewerten. Außerdem ist der Unterschied zwischen `out` und `ref` Parameter wird nicht umfassend unterstützt.  
  
 Wenn ein Verweistyp "nach Verweis" übergeben wird, will die Methode ab, den Parameter zu verwenden, um eine andere Instanz des Objekts zurückzugeben. (Einen Verweistyp nach Verweis übergeben wird auch bezeichnet als mithilfe eines Zeigers, double, Zeiger auf einen Zeiger oder eine doppelte Dereferenzierung.) Verwenden die Standardaufrufkonvention, die "als Wert" übergeben wird, empfängt ein Parameter, der einen Verweistyp bereits verwendet, einen Zeiger auf das Objekt. Der Zeiger nicht auf das Objekt, auf den er zeigt, wird als Wert übergeben. Übergeben als Wert bedeutet, die die Methode den Zeiger, damit diese auf eine neue Instanz des Verweises nicht veränderlich eingeben, aber den Inhalt des Objekts, auf den er zeigt, ändern können. Für die meisten Anwendungen reicht es liefert das gewünschte Verhalten.  
  
 Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie den Rückgabewert der Methode, um dies zu erreichen. Finden Sie unter der <xref:System.String?displayProperty=fullName> Klasse für eine Vielzahl von Methoden, mit denen Zeichenfolgen bearbeitet werden und eine neue Instanz einer Zeichenfolge zurückgeben. Durch dieses Modell verwenden, bleibt es an den Aufrufer zu entscheiden, ob das ursprüngliche Objekt beibehalten wird.  
  
 Obwohl Rückgabewerte inzwischen sind und oft verwendet, die richtige Anwendung der `out` und `ref` Parameter erfordert fortgeschrittene Entwurfs- und Fähigkeiten. Entwickler von Bibliotheken Entwurf für eine Breite Zielgruppe keine Benutzer master arbeiten mit erwarten soll `out` oder `ref` Parameter.  
  
> [!NOTE]
>  Beim Arbeiten mit Parametern, die große Strukturen sind, können die zusätzlichen Ressourcen, die erforderlich sind, kopieren Sie diese Strukturen Leistung führen, wenn Sie als Wert übergeben. In diesen Fällen sollten Sie erwägen, mit `ref` oder `out` Parameter.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, die durch einen Werttyp verursacht wird, haben Sie die Methode das Objekt als Rückgabewert zurück. Wenn die Methode mehrere Werte zurückgeben muss, Umgestalten Sie, um eine einzelne Instanz eines Objekts zurückzugeben, die die Werte enthält.  
  
 Um einen Verstoß gegen diese Regel zu beheben, die durch ein Verweistyp verursacht wird, stellen Sie sicher, dass das gewünschte Verhalten ist, um eine neue Instanz des Verweises zurückzugeben. Wenn dies der Fall, sollte die Methode den Rückgabewert verwenden, hierzu.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel; Dieser Entwurf konnte jedoch verwendungsproblemen verursachen.  
  
## <a name="example"></a>Beispiel  
 Die folgende Bibliothek zeigt zwei Implementierungen einer Klasse, die Antworten auf das Feedback des Benutzers generiert. Die erste Implementierung (`BadRefAndOut`) erzwingt, dass Benutzer der Bibliothek, drei Rückgabewerte zu verwalten. Die zweite Implementierung (`RedesignedRefAndOut`) vereinfacht die erforderlichen Erfahrungsgrad des Benutzers durch Rückgabe einer Instanz einer Container-Klasse (`ReplyData`), die die Daten als einzelne Einheit verwaltet.  
  
 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Die folgende Anwendung zeigt die Erfahrung des Benutzers. Der Aufruf der umgestalteten Bibliothek (`UseTheSimplifiedClass` Methode) ist einfacher, und die Informationen, die von der Methode zurückgegeben wird, ist leicht verwaltet. Die Ausgabe der beiden Methoden ist identisch.  
  
 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispielbibliothek wird veranschaulicht, wie `ref` Parameter für Verweistypen werden verwendet, und zeigt eine bessere Möglichkeit, diese Funktionalität zu implementieren.  
  
 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## <a name="example"></a>Beispiel  
 Die folgende Anwendung ruft jede Methode in der Bibliothek, um das Verhalten zeigen.  
  
 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **Zeiger - übergebener Wert ändern:**  
**12345**  
**12345**  
**Ändern von Zeiger - als Verweis übergeben wird:**  
**12345**  
**12345 ABCDE**  
**Übergeben als Wert zurückgibt:**  
**12345 ABCDE**   
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1021: out-Parameter vermeiden](../code-quality/ca1021-avoid-out-parameters.md)