---
title: "Mark | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Mark**\-Option von "VSPerfCmd.exe" fügt die angegebenen Informationen in die Profilerstellungs\-Datendatei ein.  Mark kann in einem separaten VSPerfReport\-Bericht oder der Markierungsberichtsansicht der Profiler\-Benutzeroberfläche aufgeführt sein.  **Mark** kann verwendet werden, um Ausgangs\- und Endpunkte in Berichts\- und Ansichtsfiltern anzugeben.  
  
 Außer der **Mark**\-Option dürfen keine anderen Optionen in der Befehlszeile angegeben werden.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### Parameter  
 `MarkID`  
 Eine benutzerdefinierte ganze Zahl, die als Markierungs\-ID in Profileransichten und \-berichten aufgeführt wird.  `MarkID` muss nicht eindeutig sein.  
  
 `MarkName`  
 \(Optional\) Eine benutzerdefinierte Zeichenfolge, die als Markierungsname in Profileransichten und \-berichten aufgeführt wird.  Wenn das `MarkName`\-Objekt nicht angegeben wird, ist das Feld "Markierungsname" der Markierungsauflistung leer.  Schließen Sie Zeichenfolgen mit Leerzeichen oder Schrägstrichen \("\/"\) in Anführungszeichen ein.  
  
## Beispiel  
 In diesem Beispiel wird eine Markierung mit der ID 123 und dem Namen "TestMark" eingefügt.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)