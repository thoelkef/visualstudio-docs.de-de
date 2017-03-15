---
title: "Gewusst wie: Ausw&#228;hlen von Samplingereignissen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.sampling"
helpviewer_keywords: 
  - "Taktzyklen (Beispielereignis)"
  - "Samplingereignisse, Auswählen"
  - "Profilerstellungstools, Samplingereignisse"
  - "Seitenfehler (Beispielereignis)"
  - "Systemaufrufe (Beispielereignis)"
  - "Leistungsindikatoren (Beispielereignis)"
  - "Leistungstools, Samplingereignisse"
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: Ausw&#228;hlen von Samplingereignissen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Standardmäßig werden von den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools Leistungsdaten in einem Intervall gesammelt, das in Prozessorzyklen angegeben wird, die vom überwachten Prozess verwendet werden.  Die Standardanzahl von Zyklen in einem Intervall beträgt 10.000.000, das ungefähr 0,01 Sekunden auf einem 1 Handhabung\- am Bodencomputer ist.  Sie können die Anzahl der Zyklen pro Intervall ändern, und Sie können das Samplingereignis ändern.  Die folgenden Samplingereignisse sind verfügbar:  
  
-   Taktzyklen – bei Problemen im Zusammenhang mit der CPU.  
  
-   Seitenfehler – bei Problemen im Zusammenhang mit dem Arbeitsspeicher.  
  
-   Systemaufrufe – bei E\/A\-Problemen.  
  
-   Leistungsindikator – CPU\-Leistungsindikatoren bei Leistungsproblemen in den unteren Ausführungsebenen.  
  
> [!IMPORTANT]
>  Wenn Sie .NET\-Arbeitsspeicherdaten \(Belegungen und\/oder Objektlebensdauern\) mithilfe der Samplingmethode sammeln, werden alle vom Benutzer angegebenen Samplingereignisse ignoriert, und die entsprechenden Speicherbelegungen und\/oder Garbage Collection\-Ereignisse werden zum Sammeln von Daten verwendet.  
  
### So wählen Sie ein Samplingereignis aus  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaft **Sampling**.  
  
3.  Wählen Sie in der Dropdownliste **Samplingereignis** das Samplingereignis aus, das Sie für die Profilerstellung der Anwendung verwenden möchten.  
  
    > [!NOTE]
    >  Die Indikatoren unter **Verfügbare Leistungsindikatoren** sind nur aktiviert, wenn Sie in der Dropdownliste **Samplingereignis** die Option **Leistungsindikator** auswählen.  
  
4.  Wenn Sie **Leistungsindikator** auswählen, wählen Sie einen bestimmten CPU\-Indikator aus dem Strukturansicht\-Steuerelement **Verfügbare Leistungsindikatoren** aus.  
  
    -   Leistungsindikatoren im Knoten **Portable Ereignisse** sind auf allen Typen von Prozessoren verfügbar.  
  
    -   Leistungsindikatoren im Knoten **Plattformereignisse** sind für den Prozessor auf dem aktuellen Computer spezifisch und könnten auf anderen Typen von Prozessoren nicht verfügbar sein.  
  
5.  Wenn Sie ein Samplingereignis auswählen, wird ein Standardwert für das Samplingintervall im Textfeld **Samplingintervall** angezeigt.  Gegebenenfalls können Sie den gewünschten Wert in das Textfeld eingeben.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Gewusst wie: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)   
 [CPU\- und Windows\-Indikatoren](../profiling/cpu-and-windows-counters.md)   
 [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)