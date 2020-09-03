---
title: 'DA0006: Equals() für Werttypen überschreiben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaba2f099f2a4d04574acd5bcdd2ba8f8f44b4ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852365"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Equals() für Werttypen überschreiben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-ID | DA0006 |  
| Kategorie |. .NET Framework-Verwendung |  
| Profiiling-Methoden | Stichprobenentnahme |  
| Meldung | Überschreiben Gleichheits-und Gleichheits Operator für Werttypen. |  
| Messge-Typ | Warnung |  
  
## <a name="cause"></a>Ursache  
 Aufrufe der Equals-Methode oder der Gleichheitsoperatoren eines öffentlichen Werttyps machen einen großen Teil der Profilerstellungsdaten aus. Implementieren Sie ggf. eine effizientere Methode.  
  
## <a name="rule-description"></a>Beschreibung der Regel  
 Bei Werttypen wird die <xref:System.Reflection>-Bibliothek von der geerbten Implementierung von Equals verwendet und der Inhalt aller Felder im Typ verglichen. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren oder sie als Schlüssel für Hashtabellen verwenden, sollte der Werttyp Equals implementieren. Wenn Ihre Programmiersprache Operatorüberladung unterstützt, sollten Sie ebenso eine Implementierung der Gleichheits- und Ungleichheitsoperatoren bereitstellen.  
  
 Weitere Informationen zum Überschreiben von Equals und Gleichheitsoperatoren finden Sie unter [Guidelines for Implementing Equals and the Equality Operator (==) (Richtlinien für die Implementierung von Equals und Gleichheitsoperator (==))](https://msdn.microsoft.com/library/7h9bszxx.aspx).  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Ein Beispiel für die Implementierung von Equals und Gleichheitsoperatoren finden Sie in der Regel für die Codeanalyse [CA1815: Override equals and operator equals on value types (CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben)](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md).
