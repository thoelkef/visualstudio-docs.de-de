---
title: -ResetSettings („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdec487781928c22a34e5e7586700ed0e91a31a7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Stellt die Standardeinstellungen von Visual Studio wieder her und startet die Visual Studio-IDE automatisch. Setzt die Einstellungen optional auf die einer angegebenen *VSSETTINGS-Datei* zurück.

Die Standardeinstellungen werden von dem Profil bestimmt, das ausgewählt war, als Visual Studio zum ersten Mal gestartet wurde.

## <a name="syntax"></a>Syntax

```
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumente

`SettingsFile`

Der vollständige Pfad und Name der *VSSETTINGS-Datei*, die auf Visual Studio angewendet werden soll.

Um die allgemeinen Entwicklungseinstellungen wiederherzustellen, verwenden Sie `General`.

## <a name="remarks"></a>Hinweise

Wenn `SettingsFile` nicht angegeben ist, werden Sie beim nächsten Start von Visual Studio dazu aufgefordert, eine Standardauflistung von Einstellungen auszuwählen.

## <a name="example"></a>Beispiel

In der folgenden Befehlszeile werden die in der Datei `MySettings.vssettings` gespeicherten Einstellungen übernommen.

```
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Siehe auch

- [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)