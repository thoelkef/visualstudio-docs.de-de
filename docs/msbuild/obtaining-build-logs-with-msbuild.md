---
title: "Erhalten von Buildprotokollen mit MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, Protokollieren"
  - "Protokollieren [MSBuild]"
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 27
caps.handback.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Erhalten von Buildprotokollen mit MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit Schalter mit MSBuild verwenden, können Sie angeben, wie viel Builddaten Sie wiederholen möchten und ob Sie Builddaten zu einer oder mehreren Dateien speichern möchten.  Sie können eine benutzerdefinierte Protokollierung auch angeben, um Builddaten zu sammeln.  Informationen zum MSBuild\-Befehlszeilenschalter, die dieses Thema nicht umfasst, finden Sie unter [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Wenn Sie Projekte erstellen, indem Sie die Visual Studio\-IDE verwenden, können Sie diese Builds beheben, indem Sie Buildprotokolle überprüfen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## Festlegen des Detailgrad  
 Wenn Sie ein Projekt erstellen, indem Sie MSBuild verwenden, ohne ein Detailgrad anzugeben, werden die folgenden Informationen im Ausgabeprotokoll:  
  
-   Fehler, Warnungen und Meldungen, die kategorisiert werden, wie äußerst wichtig.  
  
-   Einige Statusereignisse.  
  
-   Eine Zusammenfassung des Build.  
  
 Mit dem \- Schalter **\/verbosity** \(**\/v**\) verwenden, können Sie steuern, wie viele Daten im Ausgabeprotokoll angezeigt werden.  Für die Problembehandlung verwenden Sie eine Ausführlichkeitsgrad entweder von `detailed` \(`d`\) oder von `diagnostic` \(`diag`\), die die meisten Informationen bietet.  
  
 Der Buildprozess ist möglicherweise beim Festlegen **\/verbosity** zu `detailed` und sogar langsamer beim Festlegen **\/verbosity** zu `diagnostic` langsamer.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## Speichern des Buildprotokolls in eine Datei  
 Sie können den \- Schalter **\/fileLogger** \(**fl**\) verwenden, um Builddaten in eine Datei zu speichern.  Im folgenden Beispiel werden Builddaten in eine Datei, die `msbuild.log` genannt wird.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Im folgenden Beispiel wird die Protokolldatei `MyProjectOutput.log` genannt, und die Ausführlichkeit der Protokollausgabe wird zu `diagnostic` festgelegt.  Sie geben diese beiden Einstellungen an, indem Sie den \- Schalter **\/filelogparameters** \(`flp`\) verwenden.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Weitere Informationen finden Sie unter [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Das Protokoll speichern Ausgabe in mehreren Dateien  
 Im folgenden Beispiel werden `JustWarnings.log``JustErrors.log``msbuild1.log` das gesamte Protokoll, nur die Fehler und nur die Warnungen.  Im Beispiel wird Dateinummern für alle drei Dateien.  Die Dateinummern werden direkt hinter den **\/fl** und **\/flp** Schaltern angegeben \(beispielsweise, `/fl1` und `/flp1`\).  
  
 Die Schalter **\/filelogparameters** \(`flp`\) für Dateien 2 und 3 geben, was jede Datei zu benennen und was an, in jeder Datei einzufügen.  Kein Name wird für Datei 1 angegeben, sodass wird der Standardname von `msbuild1.log` verwendet.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Weitere Informationen finden Sie unter [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Verwenden einer benutzerdefinierten Protokollierung  
 Sie können eine eigene Protokollierung schreiben, indem Sie einen verwalteten Typ erstellen, durch den die <xref:Microsoft.Build.Framework.ILogger>\-Schnittstelle implementiert wird.  Sie können eine benutzerdefinierte Protokollierung, beispielsweise, um Buildfehler per E\-Mail zu versenden, in einer Datenbank zu protokollieren, oder sie in einer XML\-Datei zu protokollieren.  Weitere Informationen finden Sie unter [Build Loggers](../msbuild/build-loggers.md).  
  
 In der MSBuild\-Befehlszeile geben Sie die benutzerdefinierte Protokollierung an, indem Sie den **\/logger** Schalter verwenden.  Sie können den **\/noconsolelogger** Schalter auch verwenden, um die Protokollierung der Standardkonsole zu deaktivieren.  
  
## Siehe auch  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Build Loggers](../msbuild/build-loggers.md)   
 [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Creating Forwarding Loggers](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)