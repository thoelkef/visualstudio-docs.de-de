---
title: "&#220;bersicht &#252;ber Leistungssitzungen der Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Leistungssitzung"
  - "Leistungssitzungen"
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# &#220;bersicht &#252;ber Leistungssitzungen der Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser Übersicht werden die Grundlagen der Profilerstellung erläutert.  Entwicklern, die noch nicht viel Erfahrung mit der leistungsbezogenen Arbeit haben, wird vermittelt, wie sie mit den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools schnell produktiv werden und die Leistung ihres Codes optimieren können.  Entwickler, die bereits über Erfahrung mit der Profilerstellung verfügen, können sich einen Überblick über die spezifischen Funktionen und Prozesse der Profilerstellungstools verschaffen.  
  
 Die Profilerstellungstools von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützen Sie dabei, Leistungsprobleme im Quellcode zu identifizieren und die Leistung möglicher Lösungen zu vergleichen.  Die Assistenten und Standardeinstellungen der Profilerstellungstools liefern unmittelbare Einblicke in viele Leistungsprobleme.  Die Funktionen und Optionen der Profilerstellungstools ermöglichen eine exakte Steuerung des Profilerstellungsprozesses.  Diese Kontrolle umfasst das präzise Targeting von Codeabschnitten, die Auflistung von Timinginformationen auf Blockebene und die Aufnahme zusätzlicher Prozessor\- und Systemleistungsdaten in Ihre Daten.  
  
 Die folgenden Schritte bilden den grundlegenden Prozess für die Verwendung der Profilerstellungstools:  
  
1.  Konfigurieren Sie die Leistungssitzung, indem Sie die Auflistungsmethode und die Daten angeben, die Sie auflisten möchten.  
  
2.  Listen Sie Profilerstellungsdaten auf, indem Sie die Anwendung in der Leistungssitzung ausführen.  
  
3.  Analysieren Sie die Daten, um das Leistungsproblem zu identifizieren.  
  
4.  Ändern Sie Code in der integrierten Entwicklungsumgebung \(IDE\) von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], um die Anwendungsleistung des Codes zu verbessern.  
  
5.  Listen Sie Profilerstellungsdaten zum geänderten Code auf, und vergleichen Sie die Profilerstellungsdaten der ursprünglichen und der geänderten Daten.  
  
6.  Generieren Sie einen Bericht, der die Leistungszunahme dokumentiert.  
  
 Um mit den durch die Profilerstellung bereitgestellten Informationen zu arbeiten, sollten Sie über Symbolinformationen für die Binärdateien, für die Sie ein Profil erstellen möchten, und für die Binärdateien des Windows\-Betriebssystems verfügen.  
  
## Konfigurieren der Leistungssitzung  
 Um eine Profilerstellungssitzung zu konfigurieren, wählen Sie die gewünschte Profilerstellungsmethode und die Daten aus, die Sie auflisten möchten.  Der **Leistungs\-Assistent** der Profilerstellungstools führt Sie durch die grundlegende Konfiguration. Auf der Eigenschaftenseite Leistungssitzung können weitere Optionen hinzugefügt werden:  
  
-   Profilerstellungsmethoden beinhalten Sampling, Ablaufverfolgung und Speicherbelegung.  
  
-   Datenwerte umfassen Leistungsindikatoren für Zeit, Prozessor und Betriebssystem sowie Anwendungsereignisse, wie z. B. Seitenfehler und Kernelübergänge.  
  
 Sie können eine Leistungssitzung in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt als Teil der Projektmappe konfigurieren oder über die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE ein Profil für beliebige Binärdateien erstellen.  Sie können Sitzungseigenschaften auf den Eigenschaftenseiten zur Leistungssitzung erstellen, oder Sie können den Profilerstellungs\-Assistenten verwenden.  
  
## Auflisten von Profilerstellungsdaten  
 Sie starten die Auflistung von Profilerstellungsdaten im **Leistungs\-Explorer**.  Sie können die Profilerstellung anhalten und wieder aufnehmen, um die Menge der aufgelisteten Daten einzuschränken.  Sie können auch an einen Prozess anfügen, der bereits ausgeführt wird.  
  
 Sobald die Anwendung gestartet wird, wird das Fenster **Steuerung der Datensammlung** in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE angezeigt.  Im Fenster **Steuerung der Datenauflistung** können Sie Profile für bestimmte Teile Ihrer Anwendung erstellen, indem Sie den Auflistungsprozess anhalten und wieder aufnehmen.  Außerdem können Sie das Fenster **Steuerung der Datenauflistung** verwenden, um Markierungen in die aufgelisteten Daten einzufügen.  Markierungen sind benutzerdefinierte Datenpunkte, die in Profilansichten angezeigt werden und zum Filtern der Profilerstellungsdaten verwendet werden können.  
  
 Wenn die Zielanwendung heruntergefahren wird, wird von den Profilerstellungstools eine Profilerstellungs\-Datendatei \(VSP\-Datei\) generiert, und in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE wird der Zusammenfassungsbericht angezeigt.  
  
## Analysieren der Daten und Identifizieren von Leistungsproblemen  
 Wenn Sie eine Profilerstellung beenden, werden die Daten analysiert, und in den Fenstern der Ansicht **Leistungsbericht** der Profilerstellungstools wird eine Zusammenfassung angezeigt.  Profilerstellungsdaten werden für die Aufrufliste und einzelne Funktionen der Zielanwendung aufgelistet.  Berichtsansichten zeigen Leistungsanalysen für Datenbereiche der Prozesse, Threads, Module, Funktionen und Quellcodezeilen der Anwendung an.  Profilerstellungsdatenwerte für eine Funktion beinhalten Folgendes:  
  
-   Die Gesamtzeit, die in der Funktion und in untergeordneten Funktionen aufgewendet wurde, die von der Funktion aufgerufen wurden \(inklusive Werte\)  
  
-   Die Zeit, die für die Ausführung nur des Codes in der Funktion aufgewendet wurde \(exklusive Werte\).  
  
 Mit über zwölf verschiedenen Ansichten können Sie die Profilerstellungsdaten äußerst effizient analysieren.  Mit Ansichtsanpassungen können Sie die Daten filtern und sortieren, um die Funktionen zu suchen, die möglicherweise zu Leistungsproblemen führen.  Durch das Filtern des langsamsten Pfads werden die aktivsten Pfade in Aufrufstruktur\- und Modulansichten sofort hervorgehoben.  
  
## Ändern des Anwendungscodes  
 Wenn Sie ein oder mehrere relevante Leistungsproblem isoliert haben, können Sie den Code mit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE ändern und anschließend Profilerstellungsdaten für Ihre Änderungen auflisten.  
  
## Erneutes Auflisten von Profilerstellungsdaten und Vergleichen der Daten zwischen den Profilerstellungsausführungen  
 Die Vergleichsberichtansicht der Profilerstellungstools zeigt die Unterschiede im Hinblick auf Modul\-, Funktions\- oder Zeilenleistung zwischen zwei ausgewählten Profilerstellungsdatendateien an.  Sie können die Profilerstellungsdatenwerte angeben, die Sie vergleichen möchten, und Sie können zwischen der Vergleichsansicht und Ansichten der einzelnen Dateien wechseln.  
  
## Generieren eines Berichts mit den Ergebnissen  
 Sie können Zeilen aus jeder Leistungsberichtansicht in E\-Mails und Kalkulationstabellen einfügen, und Sie können Berichte generieren, die die Daten für eine oder mehrere Ansichten enthalten.  
  
## Siehe auch  
 [Übersichten](../profiling/overviews-performance-tools.md)   
 [Exemplarische Vorgehensweise: Profilerstellung für Anwendungen](../profiling/walkthrough-identifying-performance-problems.md)