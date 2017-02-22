---
title: "DA0506: Maximale private Bytes, die f&#252;r den Prozess zugeordnet sind, f&#252;r den die Profilerstellung ausgef&#252;hrt wird | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0506"
  - "vs.performance.DA0506"
  - "vs.performance.506"
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0506: Maximale private Bytes, die f&#252;r den Prozess zugeordnet sind, f&#252;r den die Profilerstellung ausgef&#252;hrt wird
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0506|  
|Kategorie \(Category\)|Ressourcenüberwachung|  
|Profilerstellungsmethode|Alle|  
|Meldung|Diese Information wurde lediglich zu Informationszwecken erhoben.  Vom Leistungsindikator für die Verarbeitung privater Bytes wird der virtuelle Speicher ermittelt, der von dem Prozess belegt wird, für den die Profilerstellung ausgeführt wird.  Bei dem gemeldeten Wert handelt es sich um den Maximalwert aus allen Messintervallen.|  
|Regeltyp|Information|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Regelbeschreibung  
 In dieser Meldung wird die maximale Menge an virtuellem Arbeitsspeicher in \(privaten\) Bytes gemeldet, die derzeit vom Prozess belegt sind.  Private Bytes stellen virtuelle Speicherorte dar, die durch den Prozess belegt wurden und auf die nur von im Prozess ausgeführten Threads zugegriffen werden kann.  
  
 Für 32\-Bit\-Prozesse, die auf einem 32\-Bit\-Computer ausgeführt werden, beträgt die Obergrenze des privaten Teils des Prozessadressbereichs 2 GB.  Verwenden des [\/3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini\-Schalters können 32\-Bit\-Prozessen bis zu 3 GB an virtuellem Arbeitsspeicher.  Für einen 32\-Bit\-Prozess, der auf einem 64\-Bit\-Computer ausgeführt wird, stehen bis zu 4 GB an privatem virtuellem Arbeitsspeicher zur Verfügung.  
  
 Für einen 64\-Bit\-Prozess, der auf einem 64\-Bit\-Computer ausgeführt wird, stehen bis zu 8 TB an privatem virtuellem Arbeitsspeicher zur Verfügung.  
  
 Bei dem gemeldeten Wert handelt es sich um den Maximalwert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.  
  
 Weitere Informationen über Prozessadressbereiche, finden Sie unter [Im virtuellen Adressraum](http://go.microsoft.com/fwlink/?LinkId=177832) in der Speicherverwaltungsdokumentation.  
  
## Verwenden von Regeldaten  
 Mithilfe des gemeldeten Werts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Profilerstellungsszenarien nachvollziehen.  
  
 Nähert sich der maximale Wert der privaten Bytes eines Prozesses der architekturbedingten Maximalgröße eines Prozessadressbereichs, können durch ungenügenden Arbeitsspeicher bedingte Ausnahmen auftreten.  Weitere Informationen finden Sie unter [Untersuchungsarbeitsspeicher\-Probleme](http://go.microsoft.com/fwlink/?LinkID=177833) im MSDN\-Magazin.