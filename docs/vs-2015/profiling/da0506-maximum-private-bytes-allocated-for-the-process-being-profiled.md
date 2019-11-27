---
title: 'DA0506: Maximale private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7452e8394b6397b79c49b9b706db5ba8899351e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291171"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Maximale private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-ID | DA0506 |  
| Kategorie | Ressourcenüberwachung |  
| Profil Erstellungs Methode | Alle |  
| Meldung | Diese Informationen wurden nur für Informationen gesammelt. Vom Leistungsindikator für die Verarbeitung privater Bytes wird der virtuelle Speicher ermittelt, der von dem Prozess belegt wird, für den die Profilerstellung ausgeführt wird. Bei dem gemeldeten Wert handelt es sich um den Maximalwert aus allen Messintervallen.|  
| Regeltyp | Informationen |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 In dieser Meldung wird die maximale Menge an virtuellem Arbeitsspeicher in (privaten) Bytes angegeben, die derzeit vom Prozess belegt sind. Private Bytes stellen virtuelle Speicherorte dar, die durch den Prozess belegt wurden und auf die nur von im Prozess ausgeführten Threads zugegriffen werden kann.  
  
 Für 32-Bit-Prozesse, die auf einem 32-Bit-Computer ausgeführt werden, beträgt die Obergrenze des privaten Teils des Prozessadressbereichs 2 GB. Bei Verwendung des Boot.ini-Schalters [/3 GB](https://go.microsoft.com/fwlink/?LinkId=177831) können für 32-Bit-Prozesse bis zu 3 GB an virtuellem Arbeitsspeicher zur Verfügung gestellt werden. Für einen 32-Bit-Prozess, der auf einem 64-Bit-Computer ausgeführt wird, stehen bis zu 4 GB an privatem virtuellem Arbeitsspeicher zur Verfügung.  
  
 Für einen 64-Bit-Prozess, der auf einem 64-Bit-Computer ausgeführt wird, stehen bis zu 8 TB an privatem virtuellem Arbeitsspeicher zur Verfügung.  
  
 Bei dem gemeldeten Wert handelt es sich um den Maximalwert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.  
  
 Weitere Informationen zu Prozessadressräumen finden Sie unter [Virtual Address Space (Virtueller Adressraum)](https://go.microsoft.com/fwlink/?LinkId=177832) in der Dokumentation zur Speicherverwaltung unter Windows.  
  
## <a name="how-to-use-rule-data"></a>Verwenden von Regeldaten  
 Mithilfe des gemeldeten Werts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Profilerstellungsszenarios nachvollziehen.  
  
 Nähert sich der maximale Wert der privaten Bytes eines Prozesses der architekturbedingten Maximalgröße eines Prozessadressbereichs, können durch ungenügenden Arbeitsspeicher bedingte Ausnahmen auftreten. Weitere Informationen finden Sie unter [Investigating Memory Issues (Untersuchen von Arbeitsspeicherproblemen)](https://go.microsoft.com/fwlink/?LinkID=177833) in den MSDN Magazine-Ausgaben.
