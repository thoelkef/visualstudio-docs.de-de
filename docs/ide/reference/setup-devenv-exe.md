---
title: "-Setup (devenv.exe) | Microsoft Docs"
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
  - "setup (Devenv-Schalter)"
  - "/setup (Devenv-Schalter)"
  - "Devenv, /setup-Schalter"
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zwingt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dazu, die Ressourcenmetadaten zur Beschreibung von Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages zusammenzuführen.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Hinweise  
 Der Schalter verwendet keine Argumente. Der Befehl `devenv /setup` wird in der Regel als letzter Schritt der Installation angegeben. Bei Verwendung des Schalters `/setup` wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nicht gestartet.  
  
 Sie müssen `devenv` als Administrator ausführen, um die Schalter [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) und [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) verwenden zu können.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt den letzten Schritt der Installation einer Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , die VSPackages enthält.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)