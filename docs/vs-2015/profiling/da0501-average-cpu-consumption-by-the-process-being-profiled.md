---
title: 'DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7c9b36521c9d4afec0daba945de415477bcd948
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512847"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, dessen Profil erstellt.](https://docs.microsoft.com/visualstudio/profiling/da0501-average-cpu-consumption-by-the-process-being-profiled).  
  
Regel-Id | DA501 |  
| Kategorie | Ressourcenüberwachung |  
| Profilerstellungsmethode | Alle |  
| Nachricht | Die durchschnittliche CPU-Auslastung durch den Prozess, die profilerstellung ausgeführt wird. |  
| Regeltyp | Informationen |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 In dieser Meldung wird der Prozentsatz der Zeit angegeben, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war. Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war. Bei einem Computer mit mehreren Prozessoren kann der Wert 100 Prozent übersteigen.  
  
## <a name="how-to-use-rule-data"></a>Verwenden von Regeldaten  
 Mithilfe des Regelwerts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Testszenarios nachvollziehen.



