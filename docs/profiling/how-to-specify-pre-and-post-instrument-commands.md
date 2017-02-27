---
title: "Gewusst wie: Festlegen von Pr&#228;instrumentations- und Postinstrumentationsbefehlen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.instrument"
helpviewer_keywords: 
  - "Profilerstellungstools, Präinstrumentationsereignisse"
  - "Ereignisse [Visual Studio], Präinstrumentation"
  - "Präinstrumentationsereignisse, Leistungstools"
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Gewusst wie: Festlegen von Pr&#228;instrumentations- und Postinstrumentationsbefehlen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Befehle angeben, die vor oder nach dem Instrumentieren der Binärdateien in einer Leistungssitzung ausgeführt werden.  Jeder Befehl, der über die Befehlszeile ausgegeben werden kann, kann als Präinstrumentations\- oder Postinstrumentationsereignis festgelegt werden.  Sie können z. B. in einer Batchdatei Befehle angeben, um das erneute Signieren einer Assembly mit einem Schlüssel für einen starken Namen zu automatisieren. Die Batchdatei wird ausgeführt, nachdem die Binärdateien instrumentiert wurden.  
  
 Sie können Befehle für alle instrumentierten Binärdateien in der Profilerstellung oder für einzelne Binärdateien angeben.  Es kann jedoch nur ein Präinstrumentationsbefehl \(zum Ausführen vor dem Instrumentationsprozess\) und ein Postinstrumentationsbefehl \(zum Ausführen nach dem Instrumentationsprozess\) angegeben werden.  Das gleichzeitige Angeben von Befehlen für alle und von Befehlen für einzelne Binärdateien ist nicht möglich.  Wenn Sie Befehle für alle Binärdateien angeben, werden die Befehle vor oder nach der Instrumentation jeder Binärdatei in der Sitzung ausgeführt.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Das Arbeitsverzeichnis, in dem die Befehle ausgeführt werden, hängt vom Betriebssystem ab, auf dem [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ausgeführt wird, sowie von der Zielplattform der Anwendung, für die das Profil erstellt wird.  
  
 **32\-Bit\-Computer**  
  
 Auf 32\-Bit\-Computern lautet das Standardverzeichnis für die Profilerstellungstools Laufwerk\\Programme\\Microsoft Visual Studio 10.0 \\Team Tools\\Performance Tools.  
  
 **64\-Bit\-Computer**  
  
 Auf 64\-Bit\-Computern geben Sie den Pfad entsprechend der Zielplattform der profilierten Anwendung an:  
  
-   Für 32\-Bit\-Anwendungen lautet das Standarverzeichnis für die Profilerstellungstools wie folgt:  
  
     *Drive*\\ Programme \(x86\)\\Microsoft Visual Studio 10.0\\Team Tools\\Performance Tools  
  
-   Für 64\-Bit\-Anwendungen lautet das Standardverzeichnis für die Profilerstellungstools wie folgt:  
  
     *Drive*\\ Programme \(x86\)\\Microsoft Visual Studio 10.0\\Team Tools\\Performance Tools\\x64  
  
### So geben Sie Präinstrumentationsbefehle an  
  
1.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Wählen Sie im Leistungs\-Explorer den Leistungssitzungsknoten aus, klicken Sie mit der rechten Maustaste, und klicken Sie anschließend auf **Eigenschaften**, um Präinstrumentationsbefehle für alle Binärdateien in einer Leistungssitzung anzugeben.  
  
    -   Klicken Sie in der Liste **Ziele** der Leistungssitzung mit der rechten Maustaste auf den Namen einer Binärdatei, und klicken Sie anschließend auf **Eigenschaften**, um Präinstrumentationsbefehle für die Binärdatei anzugeben.  
  
2.  Klicken Sie auf den **Eigenschaftenseiten** auf **Instrumentation**.  
  
3.  Geben Sie den Befehl in das Textfeld **Befehlszeile** unter **Präinstrumentationsereignisse** ein.  
  
    > [!NOTE]
    >  Sie können neben dem Feld **Befehlszeile** auf die Schaltfläche mit den Auslassungszeichen **\(…\)** klicken, um die entsprechende EXE\-, CMD\- oder BAT\-Datei zu suchen und auszuwählen.  
  
4.  Klicken Sie auf **OK**.  
  
     Um den Befehl zu deaktivieren, ohne ihn zu entfernen, aktivieren Sie das Kontrollkästchen **Aus Instrumentation ausschließen**.  Verwenden Sie zum Ändern von Compiler\- oder Linkereinstellungen die Projekteigenschaftenseiten.  
  
### So geben Sie Postinstrumentationsbefehle an  
  
1.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Um Postinstrumentationsbefehle für alle Binärdateien in einer Leistungssitzung anzugeben, wählen Sie den Leistungssitzungsknoten im **Leistungs\-Explorer** aus, klicken Sie dann mit der rechten Maustaste, und wählen Sie **Eigenschaften** aus.  
  
    -   Um Postinstrumentationsbefehle für eine bestimmte Binärdatei anzugeben, klicken Sie in der Liste **Ziele** der Leistungssitzung mit der rechten Maustaste auf den Namen der Binärdatei, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Eigenschaftenseiten** auf **Instrumentation**.  
  
3.  Geben Sie den Befehl in das Textfeld **Befehlszeile** unter **Postinstrumentationsereignisse** ein.  
  
    > [!NOTE]
    >  Sie können neben dem Feld **Befehlszeile** auf die Schaltfläche mit den Auslassungszeichen **\(…\)** klicken, um die entsprechende EXE\-, CMD\- oder BAT\-Datei zu suchen und auszuwählen.  
  
4.  Klicken Sie auf **OK**.  
  
     Um den Befehl zu deaktivieren, ohne ihn zu entfernen, aktivieren Sie das Kontrollkästchen **Aus Instrumentation ausschließen**.  Verwenden Sie zum Ändern von Compiler\- oder Linkereinstellungen die Projekteigenschaftenseiten.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)