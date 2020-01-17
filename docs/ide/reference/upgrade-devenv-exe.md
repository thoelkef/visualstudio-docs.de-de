---
title: -Upgrade („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bb2b296d8728587c9aa3c22b7a670d89612eff1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596423"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Aktualisiert die Projektmappendatei und alle zugehörigen Projektdateien bzw. die angegebene Projektdatei mit den aktuellen, für diese Dateien gültigen Visual Studio-Formaten.

## <a name="syntax"></a>Syntax

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Argumente

- *SolutionFile*

  Dies ist erforderlich, sofern Sie eine vollständige Projektmappe und deren Projekte aktualisieren. Der Pfad und Name einer Projektmappendatei. Es reicht aus, nur den Namen der Projektmappendatei oder einen vollständigen Pfad und den Namen der Projektmappendatei einzugeben. Wenn der angegebene Ordner bzw. die Datei noch nicht vorhanden ist, wird der Ordner oder die Datei erstellt.

- *ProjectFile*

  Dies ist erforderlich, sofern Sie ein einzelnes Projekt aktualisieren. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Es reicht aus, nur den Namen der Projektdatei oder einen vollständigen Pfad und den Namen der Projektdatei einzugeben. Wenn der angegebene Ordner bzw. die Datei noch nicht vorhanden ist, wird der Ordner oder die Datei erstellt.

- `/Out` *OutputFilename*

  Dies ist optional. Der Name der Datei, an die die Ausgabe des Tools gesendet werden soll. Wenn die Datei bereits vorhanden ist, fügt das Tool die Ausgabe an das Ende der Datei an.

## <a name="remarks"></a>Hinweise

Es werden automatisch Sicherungen erstellt und in ein Verzeichnis mit der Bezeichnung „Backup“ kopiert, das im aktuellen Verzeichnis erstellt wird.

Der Quellcodeverwaltung unterliegende Projektmappen oder Projekte müssen ausgecheckt werden, bevor sie aktualisiert werden können.

Bei Verwendung des Schalters `/Upgrade` wird Visual Studio nicht geöffnet. Die Ergebnisse des Upgrades sind im Upgradebericht für die Entwicklungssprache der Projektmappe oder des Projekts aufgeführt. Informationen zu Fehlern oder zur Verwendung werden nicht zurückgegeben. Weitere Informationen zum Upgraden von Projekten in Visual Studio finden Sie unter [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Beispiel

In diesem Beispiel wird eine Projektmappendatei mit dem Namen „MyProject.sln“ aktualisiert.

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
