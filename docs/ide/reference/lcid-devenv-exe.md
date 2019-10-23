---
title: -LCID („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 991886289ac2c2ee06e37476169dff6d2354a52e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659978"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Legt die Standardsprache für Text, Währungen und andere Werte in der IDE fest.

## <a name="syntax"></a>Syntax

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argumente

- *LocaleID*

  Erforderlich. Die Gebietsschema-ID der Sprache, die Sie angeben.

## <a name="remarks"></a>Anmerkungen

Lädt die IDE und legt die natürliche Standardsprache für die Umgebung fest. Diese Änderung wird zwischen den Sitzungen beibehalten, und die IDE zeigt diese Änderung in **Tools** > **Optionen** > **Umgebung** > **Internationale Einstellungen** > **Sprache** an.

Wenn die angegebene Sprache in Ihrem System nicht vorhanden ist, wird der `/LCID`-Schalter ignoriert.

In der folgenden Tabelle sind die LCIDs der von Visual Studio unterstützten Sprachen aufgeführt.

|Sprache|LCID|
|--------------|----------|
|Chinesisch (vereinfacht)|2052|
|Chinesisch (traditionell)|1028|
|Englisch|1033|
|Französisch|1036|
|Deutsch|1031|
|Italienisch|1040|
|Japanisch|1041|
|Koreanisch|1042|
|Spanisch|3082|

## <a name="example"></a>Beispiel

In diesem Beispiel wird die IDE mit englischen Ressourcenzeichenfolgen geladen.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [Internationale Einstellungen, Umgebung, Dialogfeld „Optionen“](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)