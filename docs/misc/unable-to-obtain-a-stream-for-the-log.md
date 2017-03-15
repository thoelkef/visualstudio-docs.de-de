---
title: "F&#252;r das Protokoll kann kein Stream abgerufen werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_ExhaustedPossibleStreamNames"
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# F&#252;r das Protokoll kann kein Stream abgerufen werden
Für das Protokoll kann kein Stream abgerufen werden. Die auf \<Name\> basierenden potenziellen Dateinamen werden bereits verwendet.  
  
 Die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>\-Klasse konnte keine neue Protokolldatei erstellen, weil alle auf \<Name\> basierenden potenziellen Protokolldateinamen bereits verwendet werden.  
  
 Eine zu große Anzahl von Protokolldateien kann auf ein Architekturproblem der Anwendung hinweisen. Weitere Informationen finden Sie in der Dokumentation zur <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>\-Klasse.  
  
### So beheben Sie diesen Fehler  
  
1.  Legen Sie die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>\-Eigenschaft auf <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> oder <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> fest, um einen Datumsstempel in den Protokolldateinamen einzufügen.  
  
2.  Archivieren Sie die vorhandenen Protokolle, und entfernen Sie diese vom Computer, damit das <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>\-Objekt neue Protokolle erstellen kann.  
  
## Siehe auch  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>   
 [My.Application.Log\-Objekt](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log Object](/dotnet/visual-basic/language-reference/objects/my-log-object)