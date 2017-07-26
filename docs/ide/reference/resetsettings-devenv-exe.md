---
title: -ResetSettings (devenv.exe) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 08d285b07d775f3e46bb2f5106ff8140d3058f8f
ms.contentlocale: de-de
ms.lasthandoff: 05/24/2017

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
