---
title: -Setup (devenv.exe) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f57de02f0d46a14574ef3f34d47f2f5e4018096b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230619"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Zwingt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dazu, die Ressourcenmetadaten zur Beschreibung von Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages zusammenzuführen.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Hinweise  
 Der Schalter verwendet keine Argumente. Der Befehl `devenv /setup` wird in der Regel als letzter Schritt der Installation angegeben. Bei Verwendung des Schalters `/setup` wird [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]nicht gestartet.  
  
 Sie müssen `devenv` als Administrator ausführen, um die Schalter [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) und [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) verwenden zu können.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt den letzten Schritt der Installation einer Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , die VSPackages enthält.  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)



