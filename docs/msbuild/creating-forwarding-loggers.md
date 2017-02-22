---
title: "Creating Forwarding Loggers | Microsoft Docs"
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
  - "MSBuild, forwarding loggers"
  - "MSBuild, logging"
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Creating Forwarding Loggers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch Weiterleitungsprotokollierungen lässt sich die Protokollierungseffizienz erhöhen, da Sie die beim Erstellen von Projekten auf einem Mehrprozessorsystem zu überwachenden Ereignisse auswählen können.  Indem Sie Weiterleitungsprotokollierungen aktivieren, können Sie verhindern, dass unerwünschte Ereignisse die zentrale Protokollierung überlasten, die Erstellung verlangsamen und das Protokoll unübersichtlich machen.  
  
 Zum Erstellen einer Weiterleitungsprotokollierung können Sie entweder die <xref:Microsoft.Build.Framework.IForwardingLogger>\-Schnittstelle implementieren und anschließend deren Methoden manuell implementieren, oder Sie können die <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>\-Klasse und deren vorkonfigurierten Methoden verwenden.  \(Letzteres genügt für die meisten Anwendungen.\)  
  
## Registrieren von Ereignissen und Reagieren auf Ereignisse  
 Eine Weiterleitungsprotokollierung sammelt Informationen über Buildereignisse aus den Berichten des sekundären Buildmoduls. Hierbei handelt es sich um einen Arbeitsprozess, der während der Builderstellung vom Hauptbuildprozess auf einem Multiprozessorsystem erstellt wird.  Anschließend wählt die Weiterleitungsprotokollierung basierend auf den von Ihnen angegebenen Anweisungen die Ereignisse aus, die an die zentrale Protokollierung weitergeleitet werden sollen.  
  
 Sie müssen Weiterleitungsprotokollierungen registrieren, damit die zu überwachenden Ereignisse verarbeitet werden können.  Um die Protokollierungen für Ereignisse zu registrieren, müssen die Protokollierungen die <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>\-Methode überschreiben.  Diese Methode umfasst den optionalen Parameter `nodecount`, der auf die Anzahl der Prozessoren im System festgelegt werden kann.  \(Der Standardwert ist 1.\)  
  
 Beispiele für Ereignisse, die überwacht werden können: <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> und <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 In einer Multiprozessorumgebung werden Ereignismeldungen mit großer Wahrscheinlichkeit nicht in ihrer Reihenfolge empfangen.  Sie müssen die Ereignisse daher mit dem Ereignishandler der Weiterleitungsprotokollierung auswerten und die Weiterleitungsprotokollierung so programmieren, dass sie die gewünschten Ereignisse an den Redirectordienst zum Weiterleiten an die zentrale Protokollierung übergibt.  Hierzu können Sie die <xref:Microsoft.Build.Framework.BuildEventContext>\-Klasse verwenden, die an jede Meldung angehängt ist, um so die weiterzuleitenden Ereignisse zu ermitteln. Anschließend können die Namen der Ereignisse an die <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>\-Klasse \(oder eine Unterklasse hiervon \) übergeben werden.  Wenn Sie diese Methode verwenden, ist keine weitere spezifische Codierung zum Weiterleiten von Ereignissen erforderlich.  
  
## Angeben einer Weiterleitungsprotokollierung  
 Nachdem die Weiterleitungsprotokollierung in eine Assembly kompiliert wurde, müssen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] anweisen, diese während der Builderstellung zu verwenden.  Verwenden Sie hierzu die Schalter `/FileLogger`, `/FileLoggerParameters` und `/DistributedFileLogger` zusammen mit MSBuild.exe.  Der `/FileLogger`\-Schalter weist MSBuild.exe an, dass die Protokollierung direkt angefügt wird. Der `/DistributedFileLogger`\-Schalter bedeutet, dass pro Knoten eine Protokolldatei verwendet wird.  Verwenden Sie zum Festlegen von Parametern für die Weiterleitungsprotokollierung den `/FileLoggerParameters`\-Schalter.  Weitere Informationen über diese und andere MSBuild.exe\-Schalter finden Sie unter [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Multiprozessorfähige Protokollierungen  
 Wenn Sie auf einem Mehrprozessorsystem ein Projekt erstellen, werden die Buildmeldungen der einzelnen Prozessoren nicht automatisch in einer einheitlichen Folge zusammengefasst.  Stattdessen müssen Sie mit der <xref:Microsoft.Build.Framework.BuildEventContext>\-Klasse, die an jede Meldung angehängt ist, eine Priorität für die Meldungsgruppierung festlegen.  Weitere Informationen zum Erstellen von Projekten in einem Mehrprozessorsystem finden Sie unter [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## Siehe auch  
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Build Loggers](../msbuild/build-loggers.md)   
 [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md)