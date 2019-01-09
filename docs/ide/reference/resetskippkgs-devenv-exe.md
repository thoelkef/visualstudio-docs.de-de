---
title: -ResetSkipPkgs („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a892902e129044549f781648d34bf058bf6eae9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853631"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Löscht alle Optionen, damit bei Benutzern, die keine problematischen VSPackages laden möchten, das Laden hinzugefügter VSPackages übersprungen wird, und startet dann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntax

```cmd
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Hinweise
 Das Tag „SkipLoading“ deaktiviert das Laden eines VSPackage, während das Leeren des Tags das Laden des VSPackage erneut aktiviert.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden alle SkipLoading-Tags geleert.

```cmd
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)