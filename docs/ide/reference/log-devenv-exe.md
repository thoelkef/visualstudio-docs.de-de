---
title: -Log („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: b0d2e6af25b4e0acc4aad88c33861e9d22a775b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846125"
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