---
title: "/ResetSkipPkgs (devenv.exe) | Microsoft Docs"
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
  - "/ResetSkipPkgs (Devenv-Schalter)"
  - "Devenv, /ResetSkipPkgs-Schalter"
  - "ResetSkipPkgs-Schalter"
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Entfernt alle Optionen zum Überspringen des Ladevorgangs, die VSPackages von Benutzern hinzugefügt wurden, um das Laden problematischer VSPackages zu vermeiden. Anschließend wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestartet.  
  
## Syntax  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## Hinweise  
 Wenn ein SkipLoading\-Tag vorhanden ist, wird das Laden von VSPackages deaktiviert. Wenn das Tag gelöscht wird, können wieder VSPackages geladen werden.  
  
## Beispiel  
 Im folgenden Beispiel werden alle SkipLoading\-Tags gelöscht.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)