---
title: -Upgrade (devenv.exe) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
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
ms.openlocfilehash: 1e8f81e61121fd6779cc0f0ebdbd166bf0c27c6f
ms.contentlocale: de-de
ms.lasthandoff: 05/24/2017

---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Aktualisiert die Projektmappendatei und alle zugehörigen Projektdateien bzw. die angegebene Projektdatei mit den aktuellen , für diese Dateien gültigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Formaten.  
  
## <a name="syntax"></a>Syntax  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>Argumente  
 `SolutionFile`  
 Dies ist erforderlich, sofern Sie eine vollständige Projektmappe und deren Projekte aktualisieren. Der Pfad und Name einer Projektmappendatei. Es reicht aus, nur den Namen der Projektmappendatei oder einen vollständigen Pfad und den Namen der Projektmappendatei einzugeben. Wenn der angegebene Ordner bzw. die Datei noch nicht vorhanden ist, wird der Ordner oder die Datei erstellt.  
  
 `ProjectFile`  
 Dies ist erforderlich, sofern Sie ein einzelnes Projekt aktualisieren. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Es reicht aus, nur den Namen der Projektdatei oder einen vollständigen Pfad und den Namen der Projektdatei einzugeben. Wenn der angegebene Ordner bzw. die Datei noch nicht vorhanden ist, wird der Ordner oder die Datei erstellt.  
  
## <a name="remarks"></a>Hinweise  
 Es werden automatisch Sicherungen und in ein Verzeichnis mit der Bezeichnung "Backup" kopiert, das im aktuellen Verzeichnis erstellt wurde.  
  
 Der Quellcodeverwaltung unterliegende Projektmappen oder Projekte müssen ausgecheckt werden, bevor sie aktualisiert werden können.  
  
 Bei Verwendung des Schalters `/upgrade` wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht gestartet. Die Ergebnisse des Upgrades sind im Upgradebericht für die Entwicklungssprache der Projektmappe oder des Projekts aufgeführt. Informationen zu Fehlern oder zur Verwendung werden nicht zurückgegeben. Weitere Informationen zum Upgraden von Projekten in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finden Sie unter [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird eine Projektmappendatei mit dem Namen "MyProject.sln" im Standardordner für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Projektmappen aktualisiert.  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
