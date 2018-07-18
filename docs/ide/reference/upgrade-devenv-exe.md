---
title: -Upgrade („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25fe5a4e75ddf349210a936f47d99c94ec70c240
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704706"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Aktualisiert die Projektmappendatei und alle zugehörigen Projektdateien bzw. die angegebene Projektdatei mit den aktuellen , für diese Dateien gültigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Formaten.

## <a name="syntax"></a>Syntax

```cmd
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

```cmd
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)