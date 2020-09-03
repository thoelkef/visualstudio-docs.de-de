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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665577"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Löscht alle Optionen, damit bei Benutzern, die keine problematischen VSPackages laden möchten, das Laden hinzugefügter VSPackages übersprungen wird, und startet dann [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Syntax

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Bemerkungen
 Das Tag „SkipLoading“ deaktiviert das Laden eines VSPackage, während das Leeren des Tags das Laden des VSPackage erneut aktiviert.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden alle SkipLoading-Tags geleert.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Weitere Informationen
 [Debug-Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md)
