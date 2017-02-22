---
title: "Status | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Status
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Status**\-Option von VSPerfCmd.exe zeigt Informationen zum Status des Profilers und allen Prozessen an, die zurzeit profiliert werden.  
  
 Außer der **Status**\-Option dürfen keine anderen Optionen in der Befehlszeile angegeben werden.  Der Profiler muss mit der **Start**\-Option von VSPerfCmd.exe initialisiert werden, bevor ein Status angezeigt werden kann.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### Parameter  
 Kein  
  
## Hinweise  
 Die **Status**\-Option zeigt die folgenden Zustandsinformationen für den Profiler an.  
  
 **Output File Name**  
 Der Pfad und Dateiname der aktuellen Profilerdatendatei.  
  
 **Collection Mode**  
 SAMPLE oder TRACE  
  
 **Maximum Processes**  
 Die maximale Anzahl von Prozessen, die gleichzeitig profiliert werden können, und die Anzahl von gerade aktiven Prozessen.  
  
 **Maximum Threads**  
 Die maximale Anzahl der Threads, die gleichzeitig profiliert werden können.  
  
 **Number of Buffers**  
 Die Anzahl von Speicherpuffern, die für das Schreiben von Profilerstellungsdaten vorgesehen sind.  
  
 **Size of Buffers**  
 Die Größe eines Speicherpuffers in Byte.  
  
 Die **Status**\-Option zeigt die folgenden Zustandsinformationen für jeden Prozess an, der gerade profiliert wird.  
  
 **Process**  
 Der Name des profilierten Prozesses.  
  
 **Process ID**  
 Der Systembezeichner des Prozesses.  
  
 **Num Threads**  
 Die Anzahl der gleichzeitig ausgeführten Threads.  
  
 **Start\/Stop Count**  
 Die primäre interne Profileranzahl zum Steuern der Datenauflistung für diesen Prozess.  Die Anzahl muss gleich eins sein, damit Daten erfasst werden.  Die Start\/Stop\-Anzahl kann durch die Profiler\-APIs und die VSPerfCmd\-Optionen **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** und **ThreadOff** geändert werden.  
  
 **Suspend\/Resume Count**  
 Die sekundäre interne Profileranzahl zum Steuern der Datenauflistung für diesen Prozess.  Die Anzahl muss kleiner oder gleich 0 \(null\) sein, damit Daten erfasst werden.  Die **Suspend\/Resume**\-Anzahl kann nur von den Profiler\-APIs bearbeitet werden.  
  
 **Users with access rights to monitor**  
 Führt die Namen der Benutzer auf, die Zugriff auf den Profiler haben.  Zusätzlichen Benutzern kann Zugriff über die **Admin**\-Option von VSPerfCmd.exe gewährt werden.  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)