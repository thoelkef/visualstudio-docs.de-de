---
title: -ResetSettings („devenv.exe“)
ms.date: 11/16/2018
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
ms.openlocfilehash: 568a829ff10cbee535729361b7c95dd7db6814f5
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948062"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Stellt die Standardeinstellungen von Visual Studio wieder her und startet die Visual Studio-IDE automatisch. Setzt die Einstellungen optional auf die einer angegebenen *VSSETTINGS-Datei* zurück.

Die Standardeinstellungen werden von dem Profil bestimmt, das ausgewählt war, als Visual Studio zum ersten Mal gestartet wurde.

> [!TIP]
> Weitere Informationen zum Zurücksetzen von Einstellungen mithilfe der integrierten Entwicklungsumgebung (IDE) finden Sie unter [Zurücksetzen von Einstellungen](../synchronized-settings-in-visual-studio.md#reset-settings).

## <a name="syntax"></a>Syntax

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumente

`SettingsFile`

Der vollständige Pfad und Name der *VSSETTINGS-Datei*, die auf Visual Studio angewendet werden soll.

Um die allgemeinen Entwicklungseinstellungen wiederherzustellen, verwenden Sie `General`.

## <a name="remarks"></a>Hinweise

Wenn `SettingsFile` nicht angegeben ist, werden Sie beim nächsten Start von Visual Studio dazu aufgefordert, eine Standardsammlung von Einstellungen auszuwählen.

## <a name="example"></a>Beispiel

In der folgenden Befehlszeile werden die in der Datei `MySettings.vssettings` gespeicherten Einstellungen übernommen.

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Siehe auch

- [Zurücksetzen von Einstellungen](../synchronized-settings-in-visual-studio.md#reset-settings)
- [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)