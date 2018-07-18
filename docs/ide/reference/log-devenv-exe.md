---
title: -Log („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3373f1e1a23ae0373a9c49a39a924398ebe143e0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704771"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Protokolliert sämtliche Aktivitäten zur Problembehandlung in der Protokolldatei. Diese Datei wird angezeigt, nachdem Sie `devenv /log` mindestens einmal aufgerufen haben. Standardmäßig wird folgende Protokolldatei verwendet:

 *%APPDATA%* \Microsoft\VisualStudio\\*Version*\ActivityLog.xml

 wobei *Version* für die Visual Studio-Version steht. Sie können jedoch einen anderen Pfad und Dateinamen angeben.

## <a name="syntax"></a>Syntax

```cmd
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Hinweise
 Dieser Schalter muss am Ende der Befehlszeile nach allen anderen Schaltern angezeigt werden.

 Das Protokoll wird für alle Instanzen von Visual Studio geschrieben, die Sie mit dem /log-Schalter aufgerufen haben. Es werden keine Instanzen von Visual Studio protokolliert, die Sie ohne den Schalter aufgerufen haben.

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)