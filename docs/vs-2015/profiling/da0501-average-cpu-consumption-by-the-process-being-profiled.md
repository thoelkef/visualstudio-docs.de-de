---
title: 'DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird. | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155772"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-ID | DA501 |  
| Kategorie | Ressourcenüberwachung |  
| Profil Erstellungs Methode | Alle |  
| Meldung | Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.  
| Regeltyp | Informationen |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="rule-description"></a>Beschreibung der Regel  
 In dieser Meldung wird der Prozentsatz der Zeit angegeben, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war. Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war. Bei einem Computer mit mehreren Prozessoren kann der Wert 100 Prozent übersteigen.  
  
## <a name="how-to-use-rule-data"></a>Verwenden von Regeldaten  
 Mithilfe des Regelwerts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Testszenarios nachvollziehen.
