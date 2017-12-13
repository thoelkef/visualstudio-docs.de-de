---
title: "/SafeMode („devenv.exe“) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72630bd7c16c3830fecddc34a71b7ea1e4cf382c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Startet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus und lädt nur die Standardumgebung und -dienste  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Hinweise  
 Dieser Schalter verhindert, dass beim Start von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackages von Drittanbietern geladen werden und stellt dadurch eine stabile Ausführung sicher.  
  
## <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im abgesicherter Modus.  
  
## <a name="code"></a>Code  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)