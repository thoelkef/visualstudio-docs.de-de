---
title: -Log („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f427edfe294605b7b2adcbb0889e48c4f37b6ba9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666846"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Protokolliert sämtliche Aktivitäten zur Problembehandlung in der Protokolldatei. Diese Datei wird angezeigt, nachdem Sie `devenv /log` mindestens einmal aufgerufen haben. Standardmäßig wird folgende Protokolldatei verwendet:

 *%APPDATA%* \Microsoft\VisualStudio\\*Version*\ActivityLog.xml

 wobei *Version* für die Visual Studio-Version steht. Sie können jedoch einen anderen Pfad und Dateinamen angeben.

## <a name="syntax"></a>Syntax

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Anmerkungen
 Dieser Schalter muss am Ende der Befehlszeile nach allen anderen Schaltern angezeigt werden.

 Das Protokoll wird für alle Instanzen von Visual Studio geschrieben, die Sie mit dem /log-Schalter aufgerufen haben. Es werden keine Instanzen von Visual Studio protokolliert, die Sie ohne den Schalter aufgerufen haben.

## <a name="see-also"></a>Siehe auch
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
