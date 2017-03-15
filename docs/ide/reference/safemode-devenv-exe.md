---
title: "/SafeMode (devenv.exe) | Microsoft Docs"
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
  - "/SafeMode (Devenv-Schalter)"
  - "Devenv, /SafeMode-Schalter"
  - "SafeMode-Schalter"
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Startet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus, wobei nur die Standardumgebung und die Standarddienste geladen werden.  
  
## Syntax  
  
```  
devenv /SafeMode   
```  
  
## Hinweise  
 Dieser Schalter verhindert beim Starten von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das Laden von VSPackages sämtlicher Drittanbieter. Dies gewährleistet eine stabile Ausführung.  
  
## Beschreibung  
 Im folgenden Beispiel wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus gestartet.  
  
## Code  
  
```  
Devenv.exe /SafeMode  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)