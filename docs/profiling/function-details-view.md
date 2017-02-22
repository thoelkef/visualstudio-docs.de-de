---
title: "Funktionsdetailansicht | Microsoft Docs"
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
  - "vs.performance.view.functiondetails"
helpviewer_keywords: 
  - "Funktionsdetailansicht"
  - "Profilerstellungstools, Funktionsdetailansicht"
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funktionsdetailansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Fenster **Funktionsdetailansicht** werden die folgenden Informationen angezeigt:  
  
-   Das Balkendiagramm **Kostenverteilung** stellt die Beziehungen zwischen einer von Ihnen ausgewählten Funktion und den aufrufenden Funktionen dar, die die ausgewählte Funktion ausgeführt haben, sowie zwischen der ausgewählten Funktion und den Funktionen, die davon aufgerufen wurden.  
  
-   Die Tabelle **Funktionsleistungsdetails**, in der zusammenfassende Profilerstellungsdaten für die angegebene Funktion angezeigt werden.  
  
-   Das Fenster **Funktionscodeansicht**, das den Funktionscode anzeigt, wenn der Code verfügbar ist.  
  
 Das Fenster **Funktionscodeansicht** ist ein separater Bereich.  Standardmäßig werden die zwei Bereiche horizontal geteilt, und das Fenster **Funktionscodeansicht** wird am unteren Rand des Frames positioniert.  
  
-   Um die beiden Bereiche vertikal zu teilen, klicken Sie auf der Symbolleiste auf **Bildschirm vertikal teilen**.  
  
-   Um die relative Größe der Bereiche zu ändern, klicken Sie auf den schattierten Rand zwischen den Frames, und ziehen Sie den Rahmen an eine andere Stelle.  
  
## Balkendiagramm für die Kostenverteilung  
  
### Leistungsmetriken  
 In der Dropdownliste **Leistungsmetrik** können Sie angeben, welche Werte in der Ansicht angezeigt werden.  Die verfügbaren Werte sind von der Profilerstellungsmethode abhängig, die in der Profilerstellungs\-Datendatei verwendet wurde.  Die Namen in Klammern sind die Namen der Zeilen in der Tabelle **Funktionsleistungsdetails**.  
  
### Bar Chart  
 **Aufrufen von Funktionen**  
  
 Die Leiste **Aufrufende Funktionen** zeigt die Funktionen an, die die ausgewählte Funktion aufgerufen haben.  Die Größe des Blocks, der die aufrufende Funktion enthält, steht im Verhältnis zu dem Anteil der aufrufenden Funktion vom Gesamtwert der Leistungsmetrik für die ausgewählte Funktion.  
  
 Sie können auf den Namen einer aufrufenden Funktion, um sie in der Ansicht auszuwählen.  
  
-   Wenn zu viele aufrufende Funktionen zum Aufführen vorhanden sind, werden Funktionen mit dem geringsten Anteil in dem Block **Andere** gesammelt.  Klicken Sie auf **Andere**, um alle aufrufenden und aufgerufenen Funktionen der ausgewählten Funktion im Fenster mit der Ansicht **Aufrufer\/Aufgerufener** anzuzeigen.  Weitere Informationen finden Sie unter [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view.md).  
  
-   Wenn keine aufrufenden Funktionen vorhanden sind oder die Funktion die Einstiegsfunktion eines Threads oder Prozesses ist, wird der Block **Anfang des Stapels** angezeigt.  
  
 **Ausgewählte Funktion**  
  
 Auf der Leiste der ausgewählten Funktion werden die Anteile von aufgerufenen Funktionen und von Code in der ausgewählten Funktion im Verhältnis zur gesamten Leistungsmetrik der ausgewählten Funktion angezeigt.  Die Größe des Blocks, der eine aufgerufene Funktion oder den Funktionsrumpf enthält, steht im Verhältnis zu dem Anteil des Gesamtwerts der Leistungsmetrik für die ausgewählte Funktion.  
  
 Sie können auf den Namen einer aufgerufenen Funktion, um sie in der Ansicht auszuwählen.  
  
-   Der Wert **Gesamt** ist die Leistungsmetrik für die ausgewählte Funktion.  
  
-   Der Block **Funktionsrumpf** stellt den Betrag der Gesamtwerts der Leistungsmetrik dar, die in der direkten Ausführung des Codes im Funktionsrumpf aufgetreten ist.  
  
-   Funktionen, die von der ausgewählten Funktion aufgerufen werden, sind in Blöcken aufgeführt.  Die Größe des ausgewählten Funktionsblocks stellt den Betrag der gesamten Leistungsmetrik für die ausgewählte Funktion dar, die in der aufgerufenen Funktion aufgetreten ist.  
  
-   Wenn zu viele aufrufende Funktionen zum Aufführen vorhanden sind, werden Funktionen mit dem geringsten Anteil in dem Block **Andere** gesammelt.  Klicken Sie auf **Andere**, um alle aufrufenden und aufgerufenen Funktionen der ausgewählten Funktion im Fenster mit der Ansicht **Aufrufer\/Aufgerufener** anzuzeigen.  Weitere Informationen finden Sie unter [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view.md).  
  
-   Wenn keine aufgerufenen Funktionen vorhanden sind, wird der Block **Ende des Stapels** angezeigt.  
  
## Funktionsleistungsdetails  
 Die Tabelle mit den Funktionsleistungsdetails enthält Zusammenfassungsdaten für die Leistungsmetrik der ausgewählten Funktion.  Sowohl der Wert als auch der Prozentsatz werden angezeigt.  Sie geben die Profilerstellungsdaten an, die in dem Diagramm und der Detailstabelle in der Liste **Leistungsmetrik** angezeigt werden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Exclusive**|-   Der Betrag der Leistungsmetrik, die bei der Ausführung des Funktionsrumpfs aufgetreten ist.|  
|**In Aufrufen**|-   Der Betrag der Leistungsmetrik, die in Funktionen aufgetreten ist, die von der ausgewählten Funktion aufgerufen wurden.|  
|**Inklusive insgesamt**|-   Der Gesamtbetrag des Werts **Exklusiv** und des Werts **In Aufrufen**.|  
  
## Funktionscodeansicht  
 Im Fenster **Funktionscodeansicht** wird eine Liste des verfügbaren Quellcodes angezeigt.  Neben den Quellcodezeilen, die anderen Funktionen aufrufen, enthält eine schattierte Spalte die Leistungsmetrikwerte für die aufgerufene Funktion.  Um den Quellcode zu bearbeiten, klicken Sie auf den Link zu der Quellcodedatei.  
  
## Werte im Balkendiagramm für die Kostenverteilung  
  
### Sampling  
 In der folgenden Tabelle werden die Werte in der Leistungsmetrikliste für die Profilerstellungsdaten erläutert, die mit der Samplingmethode erfasst wurden.  
  
|||  
|-|-|  
|**Inklusive Samplings \(Aufgelistete Samplings\)**|-   Bei einer aufrufenden Funktion die Anzahl von Samplings, die gesammelt wurden, als die ausgewählte Funktion von dieser aufrufenden Funktion aufgerufen wurde.<br />-   Beim Funktionsrumpf die Anzahl von Samples, die gesammelt wurden, als die ausgewählte Funktion ihren eigenen Code ausführte.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Samplings, die gesammelt wurden, als die aufgerufene Funktion aufgrund eines Aufrufs von der ausgewählten Funktion aufgerufen wurde.|  
  
### Instrumentation  
 In der folgenden Tabelle werden die Werte in der Leistungsmetrikliste für die Profilerstellungsdaten erläutert, die mit der Instrumentationsmethode erfasst wurden.  
  
|||  
|-|-|  
|**Verstrichene inklusive Zeit \(Verstrichene Zeit\)**|Die verstrichene Zeit umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br /><br /> -   Bei einer aufrufenden Funktion die verstrichene Zeit für die Ausführung der Instanzen der ausgewählten Funktion, die von der Funktion aufgerufen wurden.  Umfasst auch die Zeit für Funktionen, die von der ausgewählten Funktion aufgerufen wurden.<br />-   Beim **Funktionsrumpf** die Gesamtmenge der verstrichenen Zeit für die Ausführung des Codes der ausgewählten Funktion.  Die Zeit für aufgerufene Funktionen ist nicht eingeschlossen.<br />-   Bei einer aufgerufenen Funktion die verstrichene Zeit für die Ausführung der Instanzen der Funktion, die von der ausgewählten Funktion aufgerufen wurden.  Die Gesamtzeit umfasst die Zeit für Funktionen, die von der Funktion aufgerufen wurden.  Umfasst auch die Zeit für Funktionen, die von der ausgewählten Funktion aufgerufen wurden.|  
|**Inklusive Anwendungszeit \(Anwendungszeit\)**|Die Anwendungszeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br /><br /> -   Bei einer aufrufenden Funktion die Anwendungszeit für die Ausführung der Instanzen der ausgewählten Funktion, die von der Funktion aufgerufen wurden.  Umfasst auch die Zeit für Funktionen, die von der ausgewählten Funktion aufgerufen wurden.<br />-   Beim **Funktionsrumpf** die Gesamtmenge der Anwendungszeit für die Ausführung des Codes der ausgewählten Funktion.  Die Zeit für aufgerufene Funktionen ist nicht eingeschlossen.<br />-   Bei einer aufgerufenen Funktion die Anwendungszeit für die Ausführung der Instanzen der Funktion, die von der ausgewählten Funktion aufgerufen wurden.  Die Gesamtzeit umfasst die Zeit für Funktionen, die von der Funktion aufgerufen wurden.|  
  
### .NET\-Arbeitsspeicher  
 In der folgenden Tabelle werden die Werte in der Leistungsmetrikliste für die Profilerstellungsdaten erläutert, die mit der Methode zur .NET\-Arbeitsspeicherprofilerstellung erfasst wurden.  
  
|||  
|-|-|  
|**Inklusive Zuordnungen \(Zuordnungen\)**|-   Bei einer aufrufenden Funktion die Anzahl von Objekten, die von den Instanzen der ausgewählten Funktion zugeordnet wurden, die von dieser Funktion aufgerufen wurden.  Diese Zahl umfasst auch Objekte, die von Funktionen zugeordnet wurden, die von der aufgerufenen Funktionen aufgerufen wurden.<br />-   Beim **Funktionsrumpf** die Anzahl von Objekten, die durch die ausgewählte Funktion zugeordnet wurden, als diese ihren eigenen Code ausführte.  In Funktionen zugeordnete Objekte, die von der ausgewählten Funktion aufgerufen wurden, sind nicht eingeschlossen.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den Instanzen der Funktion zugeordnet wurden, die von der ausgewählten Funktion aufgerufen wurden.  Diese Zahl umfasst auch Objekte, die von Funktionen zugeordnet wurden, die von der Funktion aufgerufen wurden.|  
|**Inklusive Bytes \(Bytes\)**|-   Bei einer aufrufenden Funktion die Anzahl von Bytes, die von den Instanzen der ausgewählten Funktion zugeordnet wurden, die von dieser Funktion aufgerufen wurden.  Diese Zahl umfasst auch Bytes, die von Funktionen zugeordnet wurden, die von der ausgewählten Funktion aufgerufen wurden.<br />-   Beim **Funktionsrumpf** die Gesamtzahl von Bytes, die durch die ausgewählte Funktion zugeordnet wurden, als diese ihren eigenen Code ausführte.  In Funktionen zugeordnete Bytes, die von der ausgewählten Funktion aufgerufen wurden, sind nicht eingeschlossen.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den Instanzen der Funktion zugeordnet wurden, die von der ausgewählten Funktion aufgerufen wurden.  Diese Zahl umfasst auch Bytes, die von Funktionen zugeordnet wurden, die von der Funktion aufgerufen wurden.|  
  
### Parallelität  
 In der folgenden Tabelle werden die Werte in der Leistungsmetrikliste für die Profilerstellungsdaten erläutert, die mit der Parallelitätsmethode erfasst wurden.  
  
|||  
|-|-|  
|**Inklusive Konflikte \(Konflikte\)**|-   Bei einer aufrufenden Funktion die Anzahl von Ressourcenkonfliktereignissen, die in den Instanzen der ausgewählten Funktion aufgetreten sind, die von der Funktion aufgerufen wurden.  Diese Zahl schließt Konfliktereignisse in Funktionen ein, die von der ausgewählten Funktion aufgerufen wurden.<br />-   Beim **Funktionsrumpf** die Gesamtzahl von Konfliktereignissen, die aufgetreten sind, als die Funktion eigenen Code ausführte.  Konflikte, die in Funktionen auftreten, die von der ausgewählten Funktion aufgerufen wurden, sind nicht eingeschlossen.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Konfliktereignissen, die in den Instanzen der Funktion aufgetreten sind, die von der ausgewählten Funktion aufgerufen wurden.  Diese Zahl schließt Konfliktereignisse ein, die in Funktionen aufgetreten sind, die von der ausgewählten Funktion aufgerufen wurden.|  
|**Inklusive blockierte Zeit \(Blockierte Zeit\)**|-   Bei einer aufrufenden Funktion die Zeit für Ressourcenkonfliktereignisse für die Instanzen der ausgewählten Funktion, die von der Funktion aufgerufen wurden.  Die Zeit umfasst die blockierte Zeit in Funktionen, die von der ausgewählten Funktion aufgerufen wurden.<br />-   Beim **Funktionsrumpf** die Gesamtzeit für Konfliktereignisse, die aufgetreten sind, als die Funktion eigenen Code ausführte.  Konflikte in Funktionen, die von der ausgewählten Funktion aufgerufen wurden, sind nicht eingeschlossen.<br />-   Bei einer aufgerufenen Funktion die Zeit für Ressourcenkonfliktereignisse für die Instanzen der Funktion, die von der ausgewählten Funktion aufgerufen wurden.  Die Zeit umfasst die blockierte Zeit in Funktionen, die von der Funktion aufgerufen wurden.|