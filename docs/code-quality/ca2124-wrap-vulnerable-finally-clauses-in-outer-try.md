---
title: 'CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50c03a16af9562df40dc04a431fac157c1321fbb
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860081"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 In Version 1.0 und 1.1 von .NET Framework, eine öffentliche oder geschützte Methode enthält einen `try` / `catch` / `finally` Block. Die `finally` Block zum Sicherheitszustand zurückgesetzt wird angezeigt und steht nicht in einem `finally` Block.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel sucht `try` / `finally` , freigegebene Blöcke in Code, der Versionen 1.0 und 1.1 von .NET Framework, die möglicherweise anfällig für böswillige Ausnahmefilter in der Aufrufliste abzielt. Wenn sensibler Vorgänge wie z. B. Identitätswechsel im Try-Block ausgeführt und eine Ausnahme ausgelöst wird, kann der Filter vor dem Ausführen der `finally` Block. Das Impersonation-Beispiel bedeutet dies, dass der Filter dem imitierten Benutzer ausgeführt wird. Filter sind nur in Visual Basic momentan implementierbar.

> [!NOTE]
> In Version 2.0 und höher von .NET Framework, schützt die Common Language Runtime automatisch eine `try` / `catch` /  `finally` blockieren böswilliger Ausnahmefilter, tritt beim Zurücksetzen das direkt innerhalb der Methode, enthält den Ausnahmeblock.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Platzieren Sie die entpackten `try` / `finally` in einem äußeren Try-Block. Finden Sie im zweite Beispiel, das folgende aus. Dies zwingt den `finally` vor Filtercodes ausgeführt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudocodebeispiel

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

Der folgende Pseudocode zeigt das Muster, Sie verwenden können, schützen Sie Ihren Code, und diese Regel zu erfüllen.

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