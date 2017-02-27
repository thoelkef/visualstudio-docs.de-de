---
title: "TargetCLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# TargetCLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **TargetCLR**\-Option gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn mehr als eine CLR\-Version in eine Anwendung geladen wird.  
  
 Standardmäßig verwendet die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools die erste CLR\-Version, die von der Anwendung geladen wird.  
  
## Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### Parameter  
 `ClrVersion`  
 Die Versionsnummer der CLR.  Verwenden Sie das folgende Versionsformat: **vN.N.NNNNN**.  
  
## Erforderliche Optionen  
 Die **TargetCLR**\-Option kann nur in Verbindung mit der **Launch** \- oder der **Attach**\-Option verwendet werden.  
  
 **Launch:** `AppName`  
 Startet die angegebene Anwendung und beginnt mit der Profilerstellung.  
  
 **Attach:** `PID`  
 Startet mit der Profilerstellung für den angegebenen Prozess.  
  
## Beispiel  
 In diesem Beispiel wird die TargetCLR\-Option verwendet, um sicherzustellen, dass für die CLR\-Version 4.0.11003 ein Profil erstellt wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```