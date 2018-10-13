---
title: 'DA0505: Durchschnittliche private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c851015c9f811fc6a15f7b6c2ca037a6a30af113
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187426"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Durchschnittliche private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-Id | DA0505 |  
| Kategorie | Resource Manager |  
| Profilerstellungsmethode | Alle |  
| Nachricht | Diese Informationen war nur zu Informationszwecken gesammelt. Vom Leistungsindikator für die Verarbeitung privater Bytes wird der virtuelle Speicher ermittelt, der von dem Prozess belegt wird, für den die Profilerstellung ausgeführt wird. Dem gemeldeten Wert handelt den berechneten Durchschnittswert aus allen Messintervallen. |  
| Regeltyp | Informationen |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 In dieser Meldung wird die durchschnittliche Menge an virtuellem Arbeitsspeicher in (privaten) Bytes angegeben, die derzeit vom Prozess belegt sind. Private Bytes stellen virtuelle Speicherorte dar, die durch den Prozess belegt wurden und auf die nur von im Prozess ausgeführten Threads zugegriffen werden kann.  
  
 Für 32-Bit-Prozesse, die auf einem 32-Bit-Computer ausgeführt werden, beträgt die Obergrenze des privaten Teils des Prozessadressbereichs 2 GB. Bei Verwendung des Boot.ini-Schalters [/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) können für 32-Bit-Prozesse bis zu 3 GB an virtuellem Arbeitsspeicher zur Verfügung gestellt werden. Für einen 32-Bit-Prozess, der auf einem 64-Bit-Computer ausgeführt wird, stehen bis zu 4 GB an privatem virtuellem Arbeitsspeicher zur Verfügung.  
  
 Für einen 64-Bit-Prozess, der auf einem 64-Bit-Computer ausgeführt wird, stehen bis zu 8 TB an privatem virtuellem Arbeitsspeicher zur Verfügung.  
  
 Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.  
  
 Weitere Informationen zu Prozessadressräumen finden Sie unter [Virtual Address Space (Virtueller Adressraum)](http://go.microsoft.com/fwlink/?LinkId=177832) in der Dokumentation zur Speicherverwaltung unter Windows.  
  
## <a name="how-to-use-rule-data"></a>Verwenden von Regeldaten  
 Mithilfe des gemeldeten Werts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Profilerstellungsszenarios nachvollziehen.



