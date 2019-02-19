---
title: -Command (devenv.exe) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 317103b514a04ca149940513e4e70c2799037e62
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54775900"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Öffnet die integrierte Entwicklungsumgebung (IDE) von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und führt dann den angegebenen Befehl aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Argumente  
 `CommandName`  
 Erforderlich. Der vollständige Name eines [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Befehls oder dessen Aliasname in doppelten Anführungszeichen. Weitere Informationen zur Syntax von Befehlen und Alias finden Sie unter [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Anmerkungen  
 Nachdem der Startvorgang abgeschlossen wurde, wird der genannte Befehl in der IDE ausgeführt. Bei Verwendung dieses Schalters wird in der IDE beim Start nicht die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Startseite angezeigt.  
  
 Wenn ein Befehl mittels eines Add-Ins verfügbar gemacht wird, können Sie das Add-In mithilfe dieses Schalters von der Befehlszeile aus starten. Weitere Informationen finden Sie unter [Vorgehensweise: Steuern von Add-Ins mit dem Add-In-Manager](http://msdn.microsoft.com/library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestartet und automatisch das Makro "Open Favorite Files" ausgeführt.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
