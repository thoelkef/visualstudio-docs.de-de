---
title: "/DebugExe (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/DebugExe [devenv.exe]"
  - "DebugExe-Schalter"
  - "Devenv, /DebugExe-Schalter"
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet die angegebene ausführbare Datei, die gedebuggt werden soll.  
  
## Syntax  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## Argumente  
 `ExecutableFile`  
 Erforderlich.  Der Pfad und Dateiname einer EXE\-Datei.  
  
 Wenn die EXE\-Datei nicht gefunden wird oder nicht vorhanden ist, wird keine Warnung bzw. Fehlermeldung angezeigt, und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird ordnungsgemäß gestartet.  
  
## Hinweise  
 Alle Zeichenfolgen, die dem `ExecutableFile`\-Parameter folgen, werden als Argumente an diese Datei übergeben.  
  
## Beispiel  
 Im folgenden Beispiel wird die Datei `MyApplication.exe` zum Debuggen geöffnet.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)