---
title: -Log („devenv.exe“)
ms.date: 12/12/2018
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
ms.openlocfilehash: e6573bb8bb6118a38266c0b76ef435c59e6ccecb
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227238"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Protokolliert sämtliche Aktivitäten zur Problembehandlung in der Protokolldatei. Diese Datei wird angezeigt, nachdem Sie `devenv /log` mindestens einmal aufgerufen haben. Standardmäßig befindet sich die Protokolldatei an folgendem Speicherort:

**%APPDATA%\\Microsoft\\VisualStudio\\**\<Version\>**\\ActivityLog.xml**

wobei \<Version\> für die Visual Studio-Version steht. Sie können jedoch einen anderen Pfad und Dateinamen angeben.

## <a name="syntax"></a>Syntax

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumente

- *NameOfLogFile*

  Erforderlich. Der vollständige Pfad und Name der Protokolldatei, in die gespeichert werden soll.

## <a name="remarks"></a>Hinweise

Dieser Schalter muss am Ende der Befehlszeile nach allen anderen Schaltern angezeigt werden.

Das Protokoll wird nur für alle Instanzen von Visual Studio geschrieben, die Sie mit dem `/Log`-Schalter geöffnet haben.

## <a name="example"></a>Beispiel

In diesem Beispiel erfolgt die Protokollierung in der Datei `MyVSLog.xml` im Basisverzeichnis des Benutzers.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)