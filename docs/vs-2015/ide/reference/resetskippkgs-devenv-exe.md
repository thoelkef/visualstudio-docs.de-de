---
title: -ResetSkipPkgs („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 207ceb92d84c2186aeec49c205d8d32f4d7aa969
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665577"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Löscht alle Optionen, damit bei Benutzern, die keine problematischen VSPackages laden möchten, das Laden hinzugefügter VSPackages übersprungen wird, und startet dann [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Syntax

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Anmerkungen
 Das Tag „SkipLoading“ deaktiviert das Laden eines VSPackage, während das Leeren des Tags das Laden des VSPackage erneut aktiviert.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden alle SkipLoading-Tags geleert.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Siehe auch
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
