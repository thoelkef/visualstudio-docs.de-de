---
title: -ResetSettings (devenv.exe) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 52d01cfc3ae6a453330c2dda5da137f449ff5cbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
Stellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Standardeinstellungen wieder her und startet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] - IDE automatisch. Setzt die Einstellungen optional auf die einer angegebenen VSSETTINGS-Datei zurück.  
  
 Die Standardeinstellungen werden von dem Profil bestimmt, das ausgewählt war, als [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zuerst gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argumente  
 `SettingsFile`  
 Der vollständige Pfad und Name der VSSETTINGS-Datei, die auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] angewendet werden soll.  
  
 Um die allgemeinen Entwicklungseinstellungen wiederherzustellen, verwenden Sie `General`.  
  
## <a name="remarks"></a>Hinweise  
 Wenn kein `SettingsFile` angegeben ist, werden Sie beim nächsten Start von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aufgefordert, eine Standardauflistung von Einstellungen auswählen.  
  
## <a name="example"></a>Beispiel  
 In der folgenden Befehlszeile werden die in der Datei `MySettings.vssettings` gespeicherten Einstellungen übernommen.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)