---
title: "WaitStart | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# WaitStart
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die WaitStart\-Option bewirkt, dass der Start\-Unterbefehl "VSPerfCmd.exe" nur zurückgegeben wird, wenn der Profiler initialisiert wurde oder wenn die angegebene Anzahl von Sekunden verstrichen ist.  Standardmäßig wird der Startbefehl sofort beendet.  Wenn der Startunterbefehl zurückgegeben wird, ohne den Profiler zu initialisieren, wird ein Fehler zurückgegeben.  Wenn die Anzahl der Sekunden nicht angegeben wird, wartet der Startbefehl unbegrenzt.  
  
 Die WaitStart\-Option ist in Batchdateien nützlich, um sicherzustellen, dass der Profiler initialisiert wurde.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### Parameter  
 `Seconds`  
 Die Anzahl der Sekunden, die vor der Rückkehr vom Start\-Unterbefehl gewartet wird.  
  
## Erforderliche Optionen  
 Die WaitStart\-Option kann nur mit dem Start\-Unterbefehl verwendet werden.  
  
 **Output:** `filename`  
 Gibt den Ausgabedateinamen an.  
  
## Hinweise  
  
## Beispiel  
 In diesem Batchdateibeispiel wartet der Startbefehl 5 Sekunden lang auf die Initialisierung durch den Profiler.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```