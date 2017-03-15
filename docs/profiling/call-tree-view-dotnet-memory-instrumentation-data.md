---
title: "Aufrufstrukturansicht - .NET-Speicherinstrumentationsdaten im Profiler | Microsoft Docs"
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
  - "Aufrufstrukturansicht"
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aufrufstrukturansicht - .NET-Speicherinstrumentationsdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Aufrufstrukturansicht für Profilerstellungsdaten zur .NET\-Speicherbelegung, die mit der Instrumentationsmethode erfasst wurden, werden die Funktionsausführungspfade angezeigt, die in der profilierten Anwendung durchlaufen wurden.  Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente.  Jeder Funktionsknoten führt alle von diesem Knoten aufgerufenen Funktionen und die Daten zur .NET\-Speicherbelegung und Zeitsteuerung dieser Funktion auf.  
  
 Die Werte in der Aufrufstrukturansicht beziehen sich auf die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden.  Prozentwerte werden berechnet, indem der Funktionsinstanzwert mit der Gesamtzahl oder der Größe der Zuordnungen während der Profilerstellung verglichen wird.  
  
## Hervorheben des langsamsten Ausführungspfads  
 Die Ansicht der Aufrufstruktur kann erweitert werden und den Ausführungspfad des Prozesses oder der Funktion hervorheben, die die größten oder die meisten Speicherobjekte erstellt hat.  Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf den den Prozess oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  
  
## Festlegen des Stammknotens der Aufrufstruktur  
 Jeder Prozess in der Profilerstellungsausführung wird als Stammknoten angezeigt.  Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.  
  
 Durch Festlegen des Stammknotens verhindern Sie, dass alle anderen Einträge außer der Teilstruktur des ausgewählten Knotens in der Ansicht angezeigt werden.  Sie können den Stammknoten auf den Knoten zurücksetzen, den Sie angezeigt haben. Klicken Sie mit der rechten Maustaste in das Fenster mit der Aufrufstrukturansicht, und wählen Sie **Stamm zurücksetzen** aus.  
  
## Allgemein  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Function Name**|Der Name der Funktion.|  
|**Function Address**|Die Adresse der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Number of Calls**|Die Gesamtzahl der Aufrufe der Funktion.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Name, der dem Prozess zugewiesen wird.|  
|**Time Exclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion.  Der zusätzliche Testaufwand wurde bei allen exklusiven Zeiten subtrahiert.|  
|**Time Inclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen.  Der zusätzliche Testaufwand wurde bei allen inklusiven Zeiten subtrahiert.|  
|**Typ**|Der Kontext der Funktion:<br /><br /> -   **0** – die aktuelle Funktion<br />-   **1** – eine Funktion, die die aktuelle Funktion aufruft<br />-   **2** – eine Funktion, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Name der Stammfunktion**|Der Name der aktuellen Funktion.  Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
  
## .NET\-Arbeitsspeicherwerte  
 Die inklusiven .NET\-Arbeitsspeicherwerte einer Funktion geben die Anzahl \(Zuordnungen\) und die Größe \(Bytes\) der Objekte an, die von der Funktion und den von der Funktion aufgerufenen Funktionen erstellt wurden.  
  
 Die exklusiven Arbeitsspeicherwerte geben die Anzahl und die Größe der Objekte an, die von Code im Funktionsrumpf und nicht von den von der Funktion aufgerufenen Funktionen erstellt wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Inclusive Allocations**|Die Anzahl der Objekte, die von den Instanzen dieser Funktion zugeordnet wurden, die von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurden.  Diese Zahl schließt in untergeordneten Funktionen vorgenommene Zuordnungen ein.|  
|**Inklusive Zuordnungen in %**|Der Prozentsatz aller während der Profilerstellung erstellten Objekte, bei denen es sich um inklusive Zuordnungen der Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden, handelt.|  
|**Exclusive Allocations**|Die Anzahl der Objekte, die von den Instanzen dieser Funktion zugeordnet wurden, die von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurden.  Diese Zahl schließt keine in untergeordneten Funktionen erfolgten Zuweisungen ein.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller während der Profilerstellung erstellten Objekte, bei denen es sich um exklusive Zuordnungen der Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden, handelt.|  
  
## Werte für verstrichene inklusive Zeit  
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat.  Der Wert umfasst die Zeit für Funktionen, die von der Funktion aufgerufen wurden, und die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Inclusive Time**|Die insgesamt verstrichene inklusive Zeit für alle Aufrufe dieser Funktion, bei denen die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit bei der Profilerstellung, die innerhalb der insgesamt verstrichenen inklusiven Zeit dieser Funktion auf die Funktion entfällt, während diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|  
|**Durchschnittl. verstrichene inklusive Zeit**|Die durchschnittlich verstrichene inklusive Zeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Maximal verstrichene inklusive Zeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
  
## Werte für verstrichene exklusive Zeit  
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle in der Aufrufliste ausgeführt wurde.  Die Zeit beinhaltet die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  Auch die Zeit, die in von der Funktion aufgerufenen Funktionen aufgewendet wurde, wird jedoch nicht berücksichtigt.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Exclusive Time**|Die insgesamt verstrichene exklusive Zeit für alle Aufrufe dieser Funktion, bei denen die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der insgesamt verstrichenen exklusiven Zeit bei der Profilerstellung, die innerhalb der insgesamt verstrichenen exklusiven Zeit dieser Funktion auf die Funktion entfällt, während diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|  
|**Durchschnittl. verstrichene exklusive Zeit**|Die durchschnittlich verstrichene exklusive Zeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Maximal verstrichene exklusive Zeit**|Die maximal verstrichene exklusive Zeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
  
## Werte für inklusive Anwendungszeit  
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  Die Zeit beinhaltet Zeit, die in von der Funktion aufgerufenen untergeordneten Funktionen aufgewendet wurde.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Inclusive Time**|Die gesamte inklusive Anwendungszeit für alle Aufrufe dieser Funktion, bei denen die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Inklusive Anwendungszeit in %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit bei der Profilerstellung, die innerhalb der gesamten inklusiven Anwendungszeit dieser Funktion auf die Funktion entfällt, während diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|  
|**Durchschnittl. inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
  
## Werte für exklusive Anwendungszeit  
 Anwendungsexklusive Werte geben die Zeit an, die in der Funktion verbracht wurde, ohne die Zeit, die in untergeordneten Funktionen verbracht wurde, die von der Funktion aufgerufen wurden.  Die Zeit berücksichtigt außerdem keine Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Exclusive Time**|Die gesamte exklusive Anwendungszeit für alle Aufrufe dieser Funktion, bei denen die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Exklusive Anwendungszeit in %**|Der Prozentsatz der insgesamt verstrichenen exklusiven Zeit bei der Profilerstellung, die innerhalb der gesamten exklusiven Anwendungszeit dieser Funktion auf die Funktion entfällt, während diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|  
|**Durchschnittl. exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|  
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit für einen Aufruf dieser Funktion, bei dem die Funktion von der übergeordneten Funktion in der Aufrufliste aufgerufen wurde.|