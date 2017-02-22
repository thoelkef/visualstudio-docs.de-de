---
title: "/ResetSettings (devenv.exe) | Microsoft Docs"
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
  - "/ResetSettings (Devenv-Schalter)"
  - "Devenv, /ResetSettings-Schalter"
  - "ResetSettings-Schalter"
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Stellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Standardeinstellungen wieder her und startet die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \- IDE automatisch.  Setzt die Einstellungen optional auf die einer angegebenen VSSETTINGS\-Datei zurück.  
  
 Die Standardeinstellungen werden von dem Profil bestimmt, das ausgewählt war, als [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zuerst gestartet wurde.  
  
## Syntax  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## Argumente  
 `SettingsFile`  
 Der vollständige Pfad und Name der VSSETTINGS\-Datei, die auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] angewendet werden soll.  
  
 Um die allgemeinen Entwicklungseinstellungen wiederherzustellen, verwenden Sie `General`.  
  
## Hinweise  
 Wenn kein `SettingsFile` angegeben ist, werden Sie beim nächsten Start von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aufgefordert, eine Standardauflistung von Einstellungen auswählen.  
  
## Beispiel  
 In der folgenden Befehlszeile werden die in der Datei `MySettings.vssettings` gespeicherten Einstellungen übernommen.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## Siehe auch  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)