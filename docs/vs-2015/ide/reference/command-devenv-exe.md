---
title: -Command (devenv.exe) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e4ff0beb638e9cf5ea7a0e5f0f3330300cca6f8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524640"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [-Befehl (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/command-devenv-exe).  
  
  
Öffnet die integrierte Entwicklungsumgebung (IDE) von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und führt dann den angegebenen Befehl aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Argumente  
 `CommandName`  
 Erforderlich. Der vollständige Name eines [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Befehls oder dessen Aliasname in doppelten Anführungszeichen. Weitere Informationen zur Syntax von Befehlen und Alias finden Sie unter [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Hinweise  
 Nachdem der Startvorgang abgeschlossen wurde, wird der genannte Befehl in der IDE ausgeführt. Bei Verwendung dieses Schalters wird in der IDE beim Start nicht die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Startseite angezeigt.  
  
 Wenn ein Befehl mittels eines Add-Ins verfügbar gemacht wird, können Sie das Add-In mithilfe dieses Schalters von der Befehlszeile aus starten. Weitere Informationen finden Sie unter [Vorgehensweise: Steuern von Add-Ins mit dem Add-In-Manager](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestartet und automatisch das Makro "Open Favorite Files" ausgeführt.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)



