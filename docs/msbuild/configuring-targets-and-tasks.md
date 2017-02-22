---
title: "Configuring Targets and Tasks | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configuring Targets and Tasks
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können MSBuild\-Ziele und \-Aufgaben so konfigurieren, dass sie prozessextern mit MSBuild ausgeführt werden, damit Sie auf Kontexte abzielen können, die sich von dem unterscheiden, in dem Sie die Ausführung eigentlich vorgesehen haben.  Beispielsweise können Sie auf eine 32\-Bit\-.NET Framework 2.0\-Anwendung abzielen, während der Entwicklungscomputer auf einem 64\-Bit\-.NET Framework 4.5\-Betriebssystem ausgeführt wird.  Sie können auch auf Computer abzielen die mit .NET Framework 4 oder früher ausgeführt werden.  Die Kombination von 32\- oder 64\-Bit und der spezifischen .NET Framework\-Version wird als der *Zielkontext* bezeichnet.  
  
## Installation  
 .NET Framework 4.5 und 4.5.1 ersetzen die Common Language Runtime \(CLR\) und die Ziele, Aufgaben und Tools von .NET Framework 4 , ohne sie umzubenennen.  .NET Framework 4.5.1 wird zusammen mit [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] installiert.  
  
 Wenn Sie MSBuild separat von Visual Studio installieren möchten, können Sie das Installationspaket von der [MSBuild\-Downloadsite](http://go.microsoft.com/fwlink/?LinkId=309745) herunterladen.  Sie müssen außerdem die .NET Framework\-Versionen installieren, die Sie zusätzlich verwenden möchten.  
  
## Ziele und Aufgaben  
 MSBuild führt bestimmte Buildaufgaben prozessextern aus, um auf mehr Kontexte abzuzielen.  Beispielsweise kann ein 32\-Bit\-MSBuild eine Buildaufgabe in einem 64\-Bit\-Prozess ausführen, um auf einen 64\-Bit\-Computer abzuzielen.  Dies wird durch `UsingTask`\-Argumente und `Task`\-Parameter gesteuert.  Die Ziele, die von .NET Framework 4.5 installiert werden, legen diese Argumente und Parameter fest, und es sind keine Änderungen erforderlich, um Anwendungen für die verschiedenen Zielkontexte zu erstellen.  
  
 Wenn Sie eigene Zielkontext erstellen möchten, müssen Sie diese Argumente und Parameter entsprechend festlegen.  In der .NET Framework 4.5\-Datei "Microsoft.Common.targets" und in der Datei "Microsoft.Common.Tasks" finden Sie einige Beispiele.  Informationen dazu, wie Sie eine benutzerdefinierte Aufgabe erstellen, die mehrere Zielkontexte verwenden kann, oder wie vorhandene Aufgaben geändert werden, finden Sie unter [How to: Configure Targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## Siehe auch  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)