---
title: -LCID („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04c67b1b7d581a7e4b9d4309bfe432bf2a3298e4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Legt die Standardsprache für Text, Währungen und andere Werte in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) fest.

## <a name="syntax"></a>Syntax

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Argumente
 `LocaleID` ist erforderlich. Die LCID (Gebietsschema-ID) der Sprache, die Sie angeben

## <a name="remarks"></a>Hinweise
 Lädt die IDE und legt die natürliche Standardsprache für die Umgebung fest. Diese Änderung wird zwischen den Sitzungen beibehalten und wird im Bereich **Internationale Einstellungen** der Optionen **Umgebung** im Dialogfeld **Optionen** in der IDE angezeigt.

 Wenn die angegebene Sprache im System des Benutzers nicht vorhanden ist, wird der /LCID-Schalter ignoriert.

 In der folgenden Tabelle sind die LCIDs der von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützten Sprachen aufgeführt.

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

```
devenv /LCID 1033
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [Internationale Einstellungen, Umgebung, Dialogfeld „Optionen“](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)