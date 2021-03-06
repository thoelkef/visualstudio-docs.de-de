---
title: -ResetSettings („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eebcf2c6796723e51c3aefdb12575aa89779429f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593862"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Stellt die Standardeinstellungen von Visual Studio wieder her und startet die Visual Studio-IDE automatisch. Dieser Schalter setzt die Einstellungen optional auf die einer angegebenen Einstellungsdatei zurück.

Die Standardeinstellungen stammen aus dem Profil, das ausgewählt war, als Visual Studio zum ersten Mal gestartet wurde.

> [!TIP]
> Weitere Informationen zum Zurücksetzen von Einstellungen mithilfe der integrierten Entwicklungsumgebung (IDE) finden Sie unter [Zurücksetzen von Einstellungen](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Syntax

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Argumente

- *SettingsFile*

  Dies ist optional. Der vollständige Pfad und Name der Einstellungsdatei, die auf Visual Studio angewendet werden soll.

- *DefaultCollectionSpecifier*

  Dies ist optional. Ein Spezifizierer, der eine Standardsammlung wiederherzustellender Einstellungen darstellt. Wählen Sie einen der in der Tabelle aufgeführten Spezifizierer für eine Standardsammlung aus.

  | Name der Standardsammlung | Sammlungsspezifizierer |
  | --- | --- |
  | **Allgemein** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Webentwicklung** | `Web` |
  | **Webentwicklung (nur Code)** | `WebCode` |

## <a name="remarks"></a>Bemerkungen

Wenn kein Wert für *SettingsFile* angegeben ist, wird die IDE mit den vorhandenen Einstellungen geöffnet.

## <a name="example"></a>Beispiel

Im ersten Beispiel werden die in der Datei `MySettings.vssettings` gespeicherten Einstellungen übernommen.

Im zweiten Beispiel wird das Visual C#-Standardprofil wiederhergestellt.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Weitere Informationen

- [Umgebungseinstellungen](../environment-settings.md)
- [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
