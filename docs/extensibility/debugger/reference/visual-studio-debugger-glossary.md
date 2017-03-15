---
title: "Glossar f&#252;r Visual Studio-Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Glossar [SDK-Debuggen]"
  - "Debuggen [Debugging-SDK]-Glossar"
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Glossar f&#252;r Visual Studio-Debugger
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Im Folgenden werden die Ausdrücke, die in [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK verwendet werden.  
  
## Ausdrücke  
 gebundener Haltepunkt  
 Eine Abstraktion für einen Haltepunkt im Code festgelegt werden.  Es gibt eine 1:1\-Beziehung zwischen einem gebundenen Haltepunkt und eine Haltepunktanweisung im Codestream.  Wenn Code entladen wird, möglicherweise aufheben gebundenen Haltepunkte.  
  
 Kausalität  
 Bietet die Möglichkeit, einen logischen Ausführungsthread über mehrere physische Threads, Prozessen und Computern nachzuverfolgen, und die Aufrufliste dieses logischen Threads an einen beliebigen angegebenen Zeitpunkt in der Lebensdauer dieses Threads erneut zu erstellen.  
  
 Kontext des Codes  
 Stellt eine Abstraktion einer Position im Code bereit, mit dem das Debugmodul bekannt ist.  Für die meisten von architekturen ist ein Code in einem Kontext eine Adresse Anweisungsstream des Programms.  Für nicht traditionele Sprachen, in denen Code möglicherweise nicht von Anweisungen dargestellte Code wird ein Kontext von andere Möglichkeit dargestellt.  
  
 Codepfad  
 Stellt einen Zeitpunkt der Ausführung im Code dar, in dem eine Verzweigung ausgeführt wird, oder ein Funktionsaufruf erfolgt.  Eine Stapelüberwachung ist im Wesentlichen eine Liste der Funktionsaufruf codepfaden.  
  
 Modul \(Debug\) DE  
 Eine Komponente, die das Debuggen einer Architektur der Common Language Runtime zulässig.  Ein Debuggen Modul funktioniert in Verbindung mit den Interpreter oder dem Betriebssystem und stellt Debugdienste wie Haltepunkte Execution Control und Ausdrucksauswertung.  
  
 Dokumentenkontext  
 Stellt eine Abstraktion einer Position in einer Quelldatei Dokument bereit, mit dem das Debugmodul bekannt ist.  Für die meisten Sprachen ist ein Dokumentenkontext eine Position in einer Quelldatei.  Für nicht traditionele Sprachen für die die Quelldatei möglicherweise nicht um Text handelt, wird ein Dokumentenkontext möglicherweise auf eine andere weise dargestellt.  Siehe auch *die Zeilenposition*.  
  
 Position Dokumenten  
 Stellt eine Abstraktion einer Position in einer Quelldatei, die die IDE bekannt ist.  Für die meisten Sprachen ist eine Position des Dokuments eine Position in einer Quelldatei.  Für nicht traditionele Sprachen würde eine Position des Dokuments möglicherweise auf andere Weise dargestellt.  Siehe auch *Dokumentenkontext*.  
  
 breakpoint Fehler  
 Eine Abstraktion zur Beschreibung eines Fehlers bei einem anstehenden Haltepunkt.  Ein Fehler breakpoint beschreibt möglicherweise einen Fehler im Speicherort des ausstehenden Haltepunkten des Ausdrucks, der dem anstehenden Haltepunkt zugeordnet sind, oder andere Informationen, die den anstehenden Haltepunkt an der Bindung an einem Speicherort des Codes verhindert.  
  
 Kontext Auswertungs  
 Stellt eine Abstraktion eines Programmierung Kontexts für die Ausdrucksauswertung zur Verfügung.  In der Regel ist ein Auswertungs Elementkontext ein Bereich.  Bei der Ausdrucksauswertung in einem Ausdruckskontext der Fall ist, stellt der Ausdruckskontext Bereichs steuern, die den Punkt der Build übereinstimmen.  Beispielsweise stellt ein Ausdruckskontext, der in einem Stapelrahmen erstellt wird, den Kontext für die Auswertung von lokalen Variablen, Methodenparameter, von Klassenmembern \(falls zutreffend\) und globalen Variablen bereit.  
  
 abgefangene Ausnahme  
 Eine Ausnahme, die von einem Debug\- Modul abgefangen wird, auch wenn kein Mechanismus für die Ausnahmenbehandlung im aktuellen Stapelrahmen vorhanden ist.  
  
 JustMyCode  
 Das Konzept des Debuggens nur von Code, der einem Benutzer und dem Ignorieren zwischen allen Code wie System gehört, das Code\-gleichmäßig ist, wenn Quellcode für den Systemcode verfügbar ist.  
  
 anstehender Haltepunkt  
 Stellt eine Abstraktion für Haltepunkte vor, während und nach dem Code bereit sowie eine Methode, Haltepunkte zu virtualisieren geladen wurde.  Ein anstehender Haltepunkt:  
  
-   Enthält alle Informationen, die benötigt werden, um einen Haltepunkt in den Code in einem oder mehreren Programmen zu binden.  
  
-   Mai\-Bindung mehreren speicherorten Code in einem oder mehreren Programmen.  
  
-   Bindet sich nie auf den Code.  
  
 Jedes Mal, wenn Code bei jedem alle ausstehenden Haltepunkte in einem Programm überprüft werden, um festzustellen, ob sie gebunden werden können.  Ein anstehender Haltepunkt wird gesagt, um alle gebundenen Haltepunkte enthalten, an den es gebunden wird.  
  
 Prozess  
 Ein physischer Win32\-Prozess.  Ein Prozess kann mehrere Anwendungen enthalten.  Siehe auch *Programm*.  
  
 Programm  
 Ein einzelner Namespace, der innerhalb einer bestimmten Architektur der Laufzeit.  Siehe auch *Prozess*.  
  
 Multithreaded Manager der Sitzung \(SDM\)  
 Verwaltet eine beliebige Anzahl von Debugsymbolinformationen auf Module, die eine beliebige Anzahl von Programmen in mehreren Prozessen auf beliebig vielen Computern zu debuggen.  Auf der grundlegenden Ebene ist das Debuggen von Mehrfachkoppler ein SDM Module.  Darüber hinaus stellt das SDM eine einheitliche Sicht der Debugsitzung zur IDE bereit.  
  
 Stapelrahmen  
 Stellt den Zustand der Berechnung bei bestimmten Rahmen und einem bestimmten dar, die geschachtelter Funktionsaufrufe Ebene befinden.  
  
 Thread  
 Der allgemeine Konzept des Stapel\-basierten betriebs Befehlsausführungs in mindestens einem Programm.  
  
 warnender Haltepunkt  
 Eine Abstraktion zur Beschreibung einer Warnung in einem anstehenden Haltepunkt.  Ein warnender Haltepunkt beschreibt einen Grund, warum der ausstehenden Haltepunkt noch nicht an einem Speicherort des Codes gebunden ist.  Dies ist möglicherweise, dass der Code noch nicht geladen wurden für den Speicherort der vom ausstehenden Haltepunkt beschriebene oder aus einem anderen Grund.  
  
## Siehe auch  
 [Visual Studio\-Debugger\-Erweiterbarkeit](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)