---
title: /LCID („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: badb88abdf4b3ffd6140cb587b2b0add20630925
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672701"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt die Standardsprache für Text, Währungen und andere Werte in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) fest.

## <a name="syntax"></a>Syntax

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Argumente
 `LocaleID` ist erforderlich. Die LCID (Gebietsschema-ID) der Sprache, die Sie angeben

## <a name="remarks"></a>Anmerkungen
 Lädt die IDE und legt die natürliche Standardsprache für die Umgebung fest. Diese Änderung wird zwischen den Sitzungen beibehalten und wird im Bereich **Internationale Einstellungen** der Optionen **Umgebung** im Dialogfeld **Optionen** in der IDE angezeigt.

 Wenn die angegebene Sprache im System des Benutzers nicht vorhanden ist, wird der /LCID-Schalter ignoriert.

 In der folgenden Tabelle sind die LCIDs der von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützten Sprachen aufgeführt.

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
 [Devenv-Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md) [internationale Einstellungen, Umgebung, Dialog Feld "Optionen](../../ide/reference/international-settings-environment-options-dialog-box.md) " [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)
