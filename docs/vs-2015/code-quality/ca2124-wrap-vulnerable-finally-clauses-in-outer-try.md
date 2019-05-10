---
title: 'CA2124: Versuchen Sie es von anfällige finally Klauseln mit äußerem | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 755cce18afcad3fde621fb5a960cc780906afe51
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385994"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 In den Versionen 1.0 und 1.1 von der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], eine öffentliche oder geschützte Methode enthält einen `try` / `catch` / `finally` Block. Die `finally` Block zum Sicherheitszustand zurückgesetzt wird angezeigt und steht nicht in einem `finally` Block.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel sucht `try` / `finally` , freigegebene Blöcke in Code, Versionen 1.0 und 1.1 des als Ziel, der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , die möglicherweise anfällig für böswillige Ausnahmefilter in der Aufrufliste. Wenn sensibler Vorgänge wie z. B. Identitätswechsel im Try-Block ausgeführt und eine Ausnahme ausgelöst wird, kann der Filter vor dem Ausführen der `finally` Block. Das Impersonation-Beispiel bedeutet dies, dass der Filter dem imitierten Benutzer ausgeführt wird. Filter sind nur in Visual Basic momentan implementierbar.

> [!WARNING]
> **Hinweis** In Version 2.0 oder höher, der die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], schützt, die Laufzeit automatisch eine `try` / `catch` /  `finally` böswillige Ausnahmefilter, verhindern, wenn der zurückgesetzt wird, direkt innerhalb der Methode enthält, die den Ausnahmeblock.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Platzieren Sie die entpackten `try` / `finally` in einem äußeren Try-Block. Finden Sie im zweite Beispiel, das folgende aus. Dies zwingt den `finally` vor Filtercodes ausgeführt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudocodebeispiel

### <a name="description"></a>Beschreibung
 Der folgende Pseudocode veranschaulicht das von dieser Regel erkannte Muster.

### <a name="code"></a>Code

```
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

## <a name="example"></a>Beispiel
 Der folgende Pseudocode zeigt das Muster, Sie verwenden können, schützen Sie Ihren Code, und diese Regel zu erfüllen.

```
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
