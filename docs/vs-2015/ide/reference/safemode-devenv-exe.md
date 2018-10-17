---
title: /SafeMode („devenv.exe“) | Microsoft-Dokumentation
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
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b785a3e43726522f6e6cc6ce99dec4bf3815c81d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230075"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Startet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] im abgesicherten Modus und lädt nur die Standardumgebung und -dienste  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Hinweise  
 Dieser Schalter verhindert, dass beim Start von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackages von Drittanbietern geladen werden und stellt dadurch eine stabile Ausführung sicher.  
  
## <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] im abgesicherter Modus.  
  
## <a name="code"></a>Code  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)



