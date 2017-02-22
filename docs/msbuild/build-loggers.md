---
title: "Build Loggers | Microsoft Docs"
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
  - "MSBuild, writing loggers"
  - "MSBuild, logging"
  - "logging [MSBuild]"
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Build Loggers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe von Protokollierungen können Sie die Buildausgabe anpassen und Meldungen, Fehler oder Warnungen als Antwort auf bestimmte Buildereignisse anzeigen lassen.  Jede Protokollierung wird als .NET\-Klasse implementiert, durch die die in der Assembly Microsoft.Build.Framework.dll definierte <xref:Microsoft.Build.Framework.ILogger>\-Schnittstelle eingerichtet wird.  
  
 Eine Protokollierung kann auf zwei Weisen implementiert werden:  
  
-   Direktes Implementieren der <xref:Microsoft.Build.Framework.ILogger>\-Schnittstelle  
  
-   Ableiten der Klasse von der <xref:Microsoft.Build.Utilities.Logger>\-Hilfsklasse, die in der Assembly Microsoft.Build.Utilities.dll definiert ist.  <xref:Microsoft.Build.Utilities.Logger> implementiert <xref:Microsoft.Build.Framework.ILogger> und stellt Standardimplementierungen einiger <xref:Microsoft.Build.Framework.ILogger>\-Member bereit.  
  
 In diesem Thema wird erläutert, wie Sie eine einfache Protokollierung schreiben, die von <xref:Microsoft.Build.Utilities.Logger> abgeleitet wird und Konsolenmeldungen als Antwort auf bestimmte Buildereignisse anzeigt.  
  
## Registrieren für Ereignisse  
 Der Zweck einer Protokollierung besteht darin, Informationen zum Fortschritt des Buildvorgangs – so wie sie vom Buildmodul übermittelt werden – zu sammeln und diese Informationen in verständlicher Form mitzuteilen.  Alle Protokollierungen müssen die <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>\-Methode überschreiben, in der die Protokollierung für Ereignisse registriert wird.  In diesem Beispiel wird die Protokollierung für die Ereignisse <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> und <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> registriert.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## Reagieren auf Ereignisse  
 Nachdem die Protokollierung für bestimmte Ereignisse registriert wurde, muss sie diese Ereignisse bei deren Auftreten verarbeiten.  Bei dem <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>\-Ereignis und dem <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>\-Ereignis wird von der Protokollierung einfach ein kurzer Satz und der Name der mit dem Ereignis verknüpften Projektdatei geschrieben.  Alle von der Protokollierung ausgegebenen Meldungen werden in das Konsolenfenster geschrieben.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## Werte für den Ausführlichkeitsgrad der Protokollierung, ab denen reagiert wird  
 In einigen Fällen möchten Sie vielleicht nur Informationen aus einem Ereignis protokollieren, wenn der Schalter **\/verbosity** von MSBuild.exe einen bestimmten Wert enthält.  In diesem Beispiel wird eine Meldung vom <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>\-Ereignishandler nur protokolliert, wenn die <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>\-Eigenschaft, die mit dem **\/verbosity**\-Schalter festgelegt wird, gleich <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` ist.  
  
 [!code-cs[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## Festlegen einer Protokollierung  
 Nachdem die Protokollierung in eine Assembly kompiliert wurde, müssen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] anweisen, diese Protokollierung während der Buildvorgänge zu verwenden.  Dies geschieht mit dem **\/logger**\-Schalter von MSBuild.exe.  Weitere Informationen zu den verfügbaren Schaltern für MSBuild.exe finden Sie unter [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
 Durch die folgende Befehlszeile wird das Projekt `MyProject.csproj` erstellt und die in `SimpleLogger.dll` implementierte Protokollierungsklasse verwendet.  Durch den **\/nologo**\-Schalter werden Banner und Copyrightmeldungen ausgeblendet, und durch den **\/noconsolelogger**\-Schalter wird die Protokollierung der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Standardkonsole deaktiviert.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Durch die folgende Befehlszeile wird das Projekt mit derselben Protokollierung, jedoch mit dem `Verbosity`\-Grad `Detailed` erstellt.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## Beispiel  
  
### Beschreibung  
 Das folgende Beispiel enthält den vollständigen Code für die Protokollierung.  
  
### Code  
 [!code-cs[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### Kommentare  
  
## Beispiel  
  
### Beschreibung  
 Im folgenden Beispiel wird die Implementierung einer Protokollierung veranschaulicht, durch die das Protokoll in eine Datei geschrieben und nicht im Konsolenfenster angezeigt wird.  
  
### Code  
 [!code-cs[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
### Kommentare  
  
## Siehe auch  
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)