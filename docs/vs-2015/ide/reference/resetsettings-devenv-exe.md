---
title: -ResetSettings (devenv.exe) | Microsoft-Dokumentation
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
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25697a792b0c48746a1d7840b8091ea718f5cdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512882"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [- ResetSettings (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetsettings-devenv-exe).  
  
  
Stellt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Standardeinstellungen wieder her und startet die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] - IDE automatisch. Setzt die Einstellungen optional auf die einer angegebenen VSSETTINGS-Datei zurück.  
  
 Die Standardeinstellungen werden von dem Profil bestimmt, das ausgewählt war, als [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zuerst gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argumente  
 `SettingsFile`  
 Der vollständige Pfad und Name der VSSETTINGS-Datei, die auf [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] angewendet werden soll.  
  
 Um die allgemeinen Entwicklungseinstellungen wiederherzustellen, verwenden Sie `General`.  
  
## <a name="remarks"></a>Hinweise  
 Wenn kein `SettingsFile` angegeben ist, werden Sie beim nächsten Start von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aufgefordert, eine Standardauflistung von Einstellungen auswählen.  
  
## <a name="example"></a>Beispiel  
 In der folgenden Befehlszeile werden die in der Datei `MySettings.vssettings` gespeicherten Einstellungen übernommen.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)



