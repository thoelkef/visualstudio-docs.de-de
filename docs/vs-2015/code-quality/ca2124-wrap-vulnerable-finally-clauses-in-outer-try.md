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
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544299"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Anfällige finally-Klauseln mit äußerem try-Block umschließen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 In den Versionen 1,0 und 1,1 von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] enthält eine öffentliche oder geschützte Methode einen- `try` / `catch` / `finally` Block. Der `finally` -Block scheint den Sicherheitszustand zurückzusetzen und ist nicht in einen- `finally` Block eingeschlossen.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel `try` / `finally` findet Blöcke im Code, die auf die Versionen 1,0 und 1,1 des ausgerichtet sind [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , die anfällig für schädliche Ausnahme Filter in der-Aufrufe sind. Wenn sensible Vorgänge wie der Identitätswechsel im try-Block auftreten und eine Ausnahme ausgelöst wird, kann der Filter vor dem-Block ausgeführt werden `finally` . Für das Beispiel für den Identitätswechsel bedeutet dies, dass der Filter als Benutzer mit Identitätswechsel ausgeführt wird. Filter sind zurzeit nur in Visual Basic implementierbar.

> [!WARNING]
> In den Versionen 2,0 und höher von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] schützt die Common Language Runtime automatisch einen- `try` / `catch` /  `finally` Block vor bösartigen Ausnahme filtern, wenn die zurück Setzung direkt innerhalb der Methode auftritt, die den Ausnahme Block enthält.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie den nicht umschließenen `try` / `finally` in einen äußeren try-Block ein. Siehe das zweite Beispiel, das folgt. Dadurch wird erzwungen `finally` , dass vor dem Filtern von Code ausgeführt wird.

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
