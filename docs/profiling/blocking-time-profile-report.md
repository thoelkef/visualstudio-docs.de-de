---
title: "Blockierungszeit-Profilbericht | Microsoft Docs"
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
  - "vs.cv.threads.report.blocking"
helpviewer_keywords: 
  - "Nebenläufigkeitsschnellansicht, Blockierungszeit-Profilbericht"
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Blockierungszeit-Profilbericht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Profilberichte enthalten aggregierte Blockierungszeitdaten für spezifische Aufruflisten bereit, die zu jeder blockierenden Kategorie spezifisch sind \(wie "E\/A" oder "Synchronisierung"\).  Die VorkaufListendateien die Prozesse, die benannt, der aktuelle Prozess zusammen mit der Nummer des Vorkaufs wird als Beispiel.  Um der blockierende Profilbericht erstellen, blockierende API\-Aufrufe gesammelt und in einer Aufruflistenstruktur zusammengefasst Aufruflisten.  Daten, die in diesen Berichten angezeigt wird, sind vom aktuellen Zeitraum, von ausgeblendeten Threads sowie von den beiden folgenden anwendbaren Filtern, die möglicherweise angewendet werden:  
  
-   Wenn Nur eigenen Code ausgewählt ist, werden nur Stapelrahmen, die Benutzercode enthalten, und eine Ebene unter dem Benutzercode dargestellt.  
  
-   Wenn der Wert für Rauschunterdrückung festgelegt ist, werden sortierte Stapel mit einer geringeren als der angegebenen Frequenz übersprungen.  
  
 Erweitern Sie hier beliebigen Aufrufstruktureintrag, um zur Codezeile zu suchen, auf die die Blockierungszeit entfällt.  Um die Zeile der Quelle für einen Eintrag, auf ihrem Kontextmenü zu suchen, wählen Sie **Quelle anzeigen** aus.  Um die Codezeile zu suchen, auf die dieses Kontextmenü aufgerufen wurden, wählen Sie **Aufrufsites anzeigen** aus.  Wenn nur eine Aufrufsite vorhanden ist, wird der Befehl an der markierten Codezeile für die Aufrufsite hergestellt.  Wenn mehrere Aufrufsites vorhanden sind, wird der Befehl ein Dialogfeld, in dem ein Eintrag auswählen können und dann die Schaltfläche **Zu Quelle wechseln** auswählen, um zur hervorgehobenen Aufrufsite zu wechseln.  Es ist häufig nützlich, den Quellcode für die Aufrufsite anzuzeigen, die den meisten Instanzen, die meiste Zeit oder beide hat.  
  
## Spalten des Blockierungszeitberichts  
 Die folgende Tabelle enthält die Spalten für die einzelnen Blockierungszeitberichte:  
  
|Spaltenname|**Beschreibung**|  
|-----------------|----------------------|  
|Name|Der Name der Funktion für die einzelnen Ebenen der Aufrufliste.|  
|Instanzen|Die Anzahl von Instanzen des blockierenden Aufrufs für den sichtbaren Zeitraum.|  
|Inklusive Blockierungszeit|Die gesamte Blockierungszeit, die für alle Stapel, die bis zu dieser Ebene der Aufruflistenstruktur erfolgt.  Die inklusive Zahl ist die Summe der exklusiven Blockierungszeit für diese Funktion und der exklusiven Blockierungszeit für alle untergeordneten Knoten.|  
|Exklusive Blockierungszeit|Die gesamte Blockierungszeit, die aufgewendet wird, in dem diese Funktion die niedrigste Ebene der Aufrufliste ist.  Ein eindeutiger Aufruflisteneintrag mit einer hohen exklusiven Blockierungszeit ist möglicherweise eine relevante Funktion.|  
|API\-\/Warte\-Kategorie|Wird nur für Funktionen auf der niedrigsten Ebene der Aufrufliste angezeigt.  Wenn die Signatur des blockierenden Aufrufs erkannt wird, wird der Name der blockierenden API bereitgestellt.  Wenn die Signatur nicht erkannt wird, werden die Informationen, die vom Kernel gemeldeten wird, bereitgestellt.|  
|Details|Der vollqualifizierte Name der Funktion.  Darin eingeschlossen ist, sofern verfügbar.|  
  
### Synchronisierung  
 Der Synchronisierungsbericht enthält die Aufrufe, die Segmente mit einer Blockierung der Synchronisierung zur Folge hatten. Darüber hinaus werden auch die aggregierten Blockierungszeiten der einzelnen Aufruflisten angezeigt.  Weitere Informationen finden Sie unter [Synchronisierungszeit](../profiling/synchronization-time.md)  
  
### Sleep  
 Der Standbymodusbericht enthält die Aufrufe, durch die aufgrund von Zeit im Standbymodus Blockierungszeit angefallen ist. Darüber hinaus werden auch die aggregierten Blockierungszeiten der einzelnen Aufruflisten angezeigt.  Weitere Informationen finden Sie unter [Standbyzeit](../profiling/sleep-time.md).  
  
### E\/A  
 Der E\/A\-Bericht enthält die Aufrufe, die Segmente mit einer Blockierung der E\/A zur Folge hatten. Darüber hinaus werden auch die aggregierten Blockierungszeiten der einzelnen Aufruflisten angezeigt.  Weitere Informationen finden Sie unter [E\/A\-Zeit \(Threadansicht\)](../profiling/i-o-time-threads-view.md).  
  
### Speicherverwaltung  
 Der Speicherverwaltungsbericht enthält die Aufrufe, die Segmente mit einer Blockierung von Speicherverwaltungsvorgängen zur Folge hatten. Darüber hinaus werden auch die aggregierten Blockierungszeiten der einzelnen Aufruflisten angezeigt.  Weitere Informationen finden Sie unter [Speicherverwaltungszeit](../profiling/memory-management-time.md).  
  
### Vorzeitige Entfernung  
 Die VorkaufListendateien die Prozesse, die den aktuellen Prozess sowie die Anzahl der Instanzen benannt.  Sie können einen Prozess erweitern, um die speziellen Threads anzuzeigen, die Threads in aktuellem Prozess ersetzten und detailliert von Vorkaufinstanzen pro Thread anzuzeigen.  Dieser blockierende Bericht ist weniger von praktischem Wert als die anderen, da die vorzeitige Entfernung in der Regel den Prozess vom Betriebssystem und wird, nicht durch ein Problem im Code.  Weitere Informationen finden Sie unter [Zeit für die vorzeitige Entfernung](../profiling/preemption-time.md).  
  
### Benutzeroberflächenverarbeitung  
 Der Bericht zur Benutzeroberflächenverarbeitung enthält die Aufrufe, deren blockierenden Segmente für eine Blockierung der Benutzeroberflächenverarbeitung verantwortlich sind, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten.  Weitere Informationen finden Sie unter [Benutzeroberflächenverarbeitungszeit](../profiling/ui-processing-time.md).  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)