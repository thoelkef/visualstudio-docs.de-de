---
title: "Registerkarte &quot;Speicherplatz&quot;, Dialogfeld &quot;Prozesseigenschaften&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Prozesseigenschaften für Windows NT"
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Registerkarte &quot;Speicherplatz&quot;, Dialogfeld &quot;Prozesseigenschaften&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Speicherplatz**, um den Adressbereich eines Prozesses zu untersuchen.  Um das Dialogfeld [Prozesseigenschaften](../debugger/process-properties-dialog-box.md) anzuzeigen, verschieben Sie den Fokus auf ein [Prozessansichtsfenster](../debugger/processes-view.md).  Wählen Sie in der Struktur einen Prozessknoten und dann **Eigenschaften** im Menü **Ansicht** aus.  
  
 Auf der Registerkarte **Speicherplatz** sind die folgenden Einstellungen verfügbar:  
  
|Eintrag|Beschreibung|  
|-------------|------------------|  
|**Anzeigen, wenn markiert als**|Verwenden Sie dieses Listenfeld, um die Kategorie des Speichers \(Image, zugeordnet, reserviert oder nicht zugewiesen\) auszuwählen.|  
|**Ausführbare Bytes**|Die Summe des gesamten von dem Prozess verwendeten Adressbereichs für die ausgewählte Kategorie.  Der ausführbare Arbeitsspeicher ist der Arbeitsspeicher, der von Programmen ausgeführt werden kann, er ist jedoch schreib\- und lesegeschützt.|  
|**Ausführb. Bytes \(schreibgeschützt\)**|Die Summe des gesamten verwendeten Adressbereichs für die ausgewählte Kategorie mit schreibgeschützten Eigenschaften, die von dem Prozess verwendet werden.  Schreibgeschützter ausführbarer Arbeitsspeicher kann ausgeführt und gelesen werden.|  
|**Ausführb. Bytes \(lesen\/schreiben\)**|Die Summe des gesamten verwendeten Adressbereichs für die ausgewählte Kategorie mit Eigenschaften mit Lese\-\/Schreibzugriff, die von dem Prozess verwendet werden.  Ausführbarer Arbeitsspeicher mit Lese\-\/Schreibzugriff kann von Programmen ausgeführt sowie gelesen und geändert werden.|  
|**Ausführb. Bytes \(schreiben\/kopieren\)**|Die Summe des gesamten Adressbereichs für die ausgewählte Kategorie, der von Programmen ausgeführt sowie gelesen und geschrieben werden kann.  Dieser Typ des Schutzes wird verwendet, wenn Arbeitsspeicher für Prozesse freigegeben werden muss.  Wenn die an der Freigabe beteiligten Prozesse den Arbeitsspeicher nur lesen, verwenden sie alle den gleichen Arbeitsspeicher.  Wenn ein an der Freigabe beteiligter Prozess Schreibzugriff wünscht, wird für den Prozess eine Kopie des Arbeitsspeichers erstellt.|  
|**Bytes \(kein Zugriff\)**|Die Summe des gesamten Adressbereichs für die ausgewählte Kategorie, der verhindert, dass er von einem Prozess verwendet wird.  Bei versuchtem Lese\- oder Schreibzugriff wird eine Zugriffsverletzung generiert.|  
|**Bytes \(schreibgeschützt\)**|Die Summe des gesamten Adressbereichs für die ausgewählte Kategorie, der ausgeführt und gelesen werden kann.|  
|**Bytes \(lesen\/schreiben\)**|Die Summe des gesamten Adressbereichs für die ausgewählte Kategorie, der Lesen und Schreiben zulässt.|  
|**Bytes \(schreiben\/kopieren\)**|Die Summe des gesamten Adressbereichs für die ausgewählte Kategorie, der die Freigabe von Arbeitsspeicher für Lesezugriff, jedoch nicht für Schreibzugriff zulässt.  Wenn Prozesse diesen Arbeitsspeicher lesen, können sie den gleichen Arbeitsspeicher gemeinsam nutzen.  Wenn ein an der Freigabe beteiligter Prozess jedoch Lese\-\/Schreibzugriff auf den freigegebenen Arbeitsspeicher wünscht, wird eine Kopie dieses Arbeitsspeichers für den Schreibzugriff erstellt.|