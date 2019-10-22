---
title: 'DA0006: Equals() für Werttypen überschreiben | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cb4ac65442d9dbcb384ee3765f6fa827e3fa5d8
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306159"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Equals() für Werttypen überschreiben

|||
|-|-|
|Regel-ID|DA0006|
|Kategorie|.NET Framework-Verwendung|
|Profilerstellungsmethoden|Sampling|
|Meldung|Equals und Gleichheitsoperator für Werttypen überschreiben|
|Nachrichtentyp|Warnung|

## <a name="cause"></a>Ursache
 Aufrufe der Equals-Methode oder der Gleichheitsoperatoren eines öffentlichen Werttyps machen einen großen Teil der Profilerstellungsdaten aus. Implementieren Sie ggf. eine effizientere Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Bei Werttypen wird die <xref:System.Reflection>-Bibliothek von der geerbten Implementierung von Equals verwendet und der Inhalt aller Felder im Typ verglichen. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren oder sie als Schlüssel für Hashtabellen verwenden, sollte der Werttyp Equals implementieren. Wenn Ihre Programmiersprache Operatorüberladung unterstützt, sollten Sie ebenso eine Implementierung der Gleichheits- und Ungleichheitsoperatoren bereitstellen.

 Weitere Informationen zum Überschreiben von Equals und Gleichheitsoperatoren finden Sie unter [Guidelines for Implementing Equals and the Equality Operator (==) (Richtlinien für die Implementierung von Equals und Gleichheitsoperator (==))](http://go.microsoft.com/fwlink/?LinkId=177818).

## <a name="how-to-investigate-a-warning"></a>Vorgehensweise zur Überprüfung einer Warnung
 Ein Beispiel für die Implementierung von Equals und Gleichheitsoperatoren finden Sie in der Regel für die Codeanalyse [CA1815: Override equals and operator equals on value types (CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben)](../code-quality/ca1815.md).