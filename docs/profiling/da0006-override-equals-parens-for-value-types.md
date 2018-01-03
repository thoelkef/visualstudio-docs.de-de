---
title: "DA0006: Equals() für Werttypen überschreiben | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7b8b821075221486dce02876a2abe8cc3aed27ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Ein Beispiel für die Implementierung von Equals und Gleichheitsoperatoren finden Sie in der Regel für die Codeanalyse [CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md).