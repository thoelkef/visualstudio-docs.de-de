---
title: 'CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008767f7d37e2c088dad58a328b025f81090ad8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232453"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen.

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
In den Versionen 1,0 und 1,1 des .NET Framework enthält eine öffentliche oder geschützte `try` Methode einen / `catch` / `finally` -Block. Der `finally` -Block scheint den Sicherheitszustand zurückzusetzen und ist nicht in `finally` einen-Block eingeschlossen.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel `try` / findetBlöckeimCode,dieaufdieVersionen1,0und1,1des.NETFrameworkausgerichtetsind,dieanfälligfürschädlicheAusnahmeFilterinder`finally` -Aufrufe sind. Wenn sensible Vorgänge wie der Identitätswechsel im try-Block auftreten und eine Ausnahme ausgelöst wird, kann der Filter vor dem `finally` -Block ausgeführt werden. Für das Beispiel für den Identitätswechsel bedeutet dies, dass der Filter als Benutzer mit Identitätswechsel ausgeführt wird. Filter sind zurzeit nur in Visual Basic implementierbar.

> [!NOTE]
> In den Versionen 2,0 und höher des .NET Framework schützt die Common Language Runtime automatisch `try` einen /  / `catch` `finally` -Block vor bösartigen Ausnahme filtern, wenn die zurück Setzung direkt innerhalb der Methode auftritt, die enthält den Exception-Block.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Fügen Sie den nicht `try` umschließenen / `finally` in einen äußeren try-Block ein. Siehe das zweite Beispiel, das folgt. Dadurch wird erzwungen `finally` , dass vor dem Filtern von Code ausgeführt wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudo Codebeispiel

### <a name="description"></a>Beschreibung

Der folgende Pseudocode veranschaulicht das von dieser Regel erkannte Muster.

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

Der folgende Pseudo Code zeigt das Muster, das Sie verwenden können, um Ihren Code zu schützen und diese Regel zu erfüllen.

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```