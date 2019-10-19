---
title: 'CA2124: anfällige-Klausel in äußerem try-Klausel packen | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660244"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 In den Versionen 1,0 und 1,1 des [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] enthält eine öffentliche oder geschützte Methode eine `try` / `catch` / `finally` Block. Der `finally`-Block scheint den Sicherheitszustand zurückzusetzen und ist nicht in einen `finally` Block eingeschlossen.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel findet `try` / `finally` Blöcke im Code, die auf die Versionen 1,0 und 1,1 der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ausgerichtet sind, die anfällig für schädliche Ausnahme Filter in der-Aufrufe sind. Wenn sensible Vorgänge wie der Identitätswechsel im try-Block auftreten und eine Ausnahme ausgelöst wird, kann der Filter vor dem `finally`-Block ausgeführt werden. Für das Beispiel für den Identitätswechsel bedeutet dies, dass der Filter als Benutzer mit Identitätswechsel ausgeführt wird. Filter sind zurzeit nur in Visual Basic implementierbar.

> [!WARNING]
> In den Versionen 2,0 und höher des [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] schützt die Common Language Runtime automatisch eine `try` / `catch` /  `finally` Block von bösartigen Ausnahme filtern, wenn die zurück Setzung direkt innerhalb der Methode auftritt, die den Ausnahme Block enthält.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie die nicht umschließende `try` / `finally` in einem äußeren try-Block ein. Siehe das zweite Beispiel, das folgt. Dadurch wird erzwungen, dass die `finally` vor dem Filtern von Code ausgeführt wird.

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
 Der folgende Pseudo Code zeigt das Muster, das Sie verwenden können, um Ihren Code zu schützen und diese Regel zu erfüllen.

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
