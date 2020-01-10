---
title: 'CA1065: keine Ausnahmen an unerwarteten Speicherorten Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2df740abf25344253627b614fdbd80dce86c7bfa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847470"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode, von der das Auslösen von Ausnahmen nicht erwartet wird, löst eine Ausnahme aus.

## <a name="rule-description"></a>Regelbeschreibung
 Methoden, für die keine Ausnahmen ausgelöst werden, können wie folgt kategorisiert werden:

- Get-Methoden der Eigenschaft

- Ereigniszugriffsmethoden

- Gleichheits Methoden

- GetHashCode-Methoden

- Methoden mit dem Methoden Satz

- Statische Konstruktoren

- Finalizer

- Verwerfen von Methoden

- Gleichheitsoperatoren

- Implizite Umwandlungs Operatoren

  In den folgenden Abschnitten werden diese Methoden Typen erörtert.

### <a name="property-get-methods"></a>Get-Methoden der Eigenschaft
 Eigenschaften sind im Grunde intelligente Felder. Daher sollten Sie sich so weit wie möglich wie ein Feld Verhalten. Felder lösen keine Ausnahmen aus, und keine Eigenschaften. Wenn Sie über eine Eigenschaft verfügen, die eine Ausnahme auslöst, sollten Sie eine Methode erstellen.

 Die folgenden Ausnahmen können von einer Get-Methode der Eigenschaft ausgelöst werden:

- <xref:System.InvalidOperationException?displayProperty=fullName> und alle Ableitungen (einschließlich <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> und alle Ableitungen

- <xref:System.ArgumentException?displayProperty=fullName> (nur aus indiziertem Get)

- <xref:System.Collections.Generic.KeyNotFoundException> (nur aus indiziertem Get)

### <a name="event-accessor-methods"></a>Ereigniszugriffsmethoden
 Ereignisaccessoren sollten einfache Vorgänge sein, die keine Ausnahmen auslösen. Ein Ereignis sollte keine Ausnahme auslösen, wenn Sie versuchen, einen Ereignishandler hinzuzufügen oder zu entfernen.

 Die folgenden Ausnahmen können von einem Ereignis accesor ausgelöst werden:

- <xref:System.InvalidOperationException?displayProperty=fullName> und alle Ableitungen (einschließlich <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> und alle Ableitungen

- <xref:System.ArgumentException> und Ableitungen

### <a name="equals-methods"></a>Gleichheits Methoden
 Die folgenden **Gleichheits** Methoden sollten keine Ausnahmen auslösen:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- ["M:IEquatable.ist"](https://msdn2.microsoft.com/library/ms131190(VS.80).aspx)

  Eine **Gleichheits** Methode sollte `true` oder `false` zurückgeben, anstatt eine Ausnahme auszulösen. Wenn z. b. auf gleich zwei nicht übereinstimmende Typen folgt, sollte nur `false` zurückgegeben werden, anstatt eine <xref:System.ArgumentException>auszulösen.

### <a name="gethashcode-methods"></a>GetHashCode-Methoden
 Die folgenden **GetHashCode** -Methoden sollten normalerweise keine Ausnahmen auslösen:

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode(T)](https://msdn2.microsoft.com/library/system.collections.iequalitycomparer.gethashcode.aspx)

  **GetHashCode** sollte immer einen Wert zurückgeben. Andernfalls können Sie Elemente in der Hash Tabelle verlieren.

  Die Versionen von **GetHashCode** , die ein Argument annehmen, können eine <xref:System.ArgumentException>auslösen. **Object. GetHashCode** sollte jedoch nie eine Ausnahme auslösen.

### <a name="tostring-methods"></a>Methoden mit dem Methoden Satz
 Der Debugger verwendet <xref:System.Object.ToString%2A?displayProperty=fullName>, um Informationen zu Objekten im Zeichen folgen Format anzuzeigen. Daher sollte die Objekt **Zeichenfolge** den Status eines Objekts nicht ändern und keine Ausnahmen auslösen.

### <a name="static-constructors"></a>Statische Konstruktoren
 Das Auslösen von Ausnahmen von einem statischen Konstruktor bewirkt, dass der Typ in der aktuellen Anwendungsdomäne unbrauchbar ist. Sie sollten einen sehr guten Grund (z. b. ein Sicherheitsproblem) zum Auslösen einer Ausnahme von einem statischen Konstruktor haben.

### <a name="finalizers"></a>Finalizer
 Das Auslösen einer Ausnahme von einem Finalizer bewirkt, dass die CLR schnell ausfällt, was den Prozess aufreißt. Daher sollte das Auslösen von Ausnahmen in einem Finalizer immer vermieden werden.

### <a name="dispose-methods"></a>Verwerfen von Methoden
 Eine <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Methode sollte keine Ausnahme auslösen. "Verwerfen" wird häufig als Teil der Bereinigungs Logik in einer `finally`-Klausel aufgerufen. Daher zwingt das explizite Auslösen einer Ausnahme von verwerfen den Benutzer, eine Ausnahmebehandlung in der `finally`-Klausel hinzuzufügen.

 Der verwerfen **(false)** -Codepfad sollte nie Ausnahmen auslösen, da dies fast immer von einem Finalizer aufgerufen wird.

### <a name="equality-operators--"></a>Gleichheits Operatoren (= =,! =)
 Gleichheits Operatoren sollten wie Gleichheits Methoden entweder `true` oder `false` zurückgeben und sollten keine Ausnahmen auslösen.

### <a name="implicit-cast-operators"></a>Implizite Umwandlungs Operatoren
 Da der Benutzer häufig nicht weiß, dass ein impliziter Umwandlungs Operator aufgerufen wurde, ist eine Ausnahme, die vom impliziten Umwandlungs Operator ausgelöst wurde, völlig unerwartet. Daher sollten keine Ausnahmen von impliziten Umwandlungs Operatoren ausgelöst werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie für Eigenschaften Getter die Logik, sodass keine Ausnahme mehr ausgelöst werden muss, oder ändern Sie die-Eigenschaft in eine-Methode.

 Ändern Sie für alle anderen zuvor aufgelisteten Methoden Typen die Logik so, dass Sie keine Ausnahme mehr auslösen muss.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Verletzung durch eine Ausnahme Deklaration anstelle einer ausgelösten Ausnahme verursacht wurde.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Siehe auch
 [Entwurfswarnungen](../code-quality/design-warnings.md)
