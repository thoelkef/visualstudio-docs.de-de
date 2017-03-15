---
title: "/Log (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Log (Devenv-Schalter)"
  - "Devenv, /Log-Schalter"
  - "Log-Schalter [devenv.exe]"
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Log (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Protokolliert sämtliche Aktivitäten zur Problembehandlung in der Protokolldatei.  Diese Datei wird angezeigt, nachdem Sie `devenv /log` mindestens einmal aufgerufen haben.  Standardmäßig wird folgende Protokolldatei verwendet:  
  
 *%APPDATA%*\\Microsoft\\VisualStudio\\*Version*\\ActivityLog.xml  
  
 wobei *Version* für die Visual Studio\-Version steht.  Sie können jedoch einen anderen Pfad und Dateinamen angeben.  
  
## Syntax  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## Hinweise  
 Dieser Schalter muss am Ende der Befehlszeile nach allen anderen Schaltern angezeigt werden.  
  
 Das Protokoll wird für alle Instanzen von Visual Studio geschrieben, die Sie mit dem \/log\-Schalter aufgerufen haben.  Es werden keine Instanzen von Visual Studio protokolliert, die Sie ohne den Schalter aufgerufen haben.  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)