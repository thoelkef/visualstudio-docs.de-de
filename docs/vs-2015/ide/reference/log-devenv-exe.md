---
title: -Log („devenv.exe“) | Microsoft-Dokumentation
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
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bfd6d9ac2493e4caca95538140fb9af78db8e074
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512169"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [-Log (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/log-devenv-exe).  
  
  
Protokolliert sämtliche Aktivitäten zur Problembehandlung in der Protokolldatei. Diese Datei wird angezeigt, nachdem Sie `devenv /log` mindestens einmal aufgerufen haben. Standardmäßig wird folgende Protokolldatei verwendet:  
  
 *%APPDATA%* \Microsoft\VisualStudio\\*Version*\ActivityLog.xml  
  
 wobei *Version* für die Visual Studio-Version steht. Sie können jedoch einen anderen Pfad und Dateinamen angeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Hinweise  
 Dieser Schalter muss am Ende der Befehlszeile nach allen anderen Schaltern angezeigt werden.  
  
 Das Protokoll wird für alle Instanzen von Visual Studio geschrieben, die Sie mit dem /log-Schalter aufgerufen haben. Es werden keine Instanzen von Visual Studio protokolliert, die Sie ohne den Schalter aufgerufen haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)



