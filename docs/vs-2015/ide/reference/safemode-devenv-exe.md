---
title: /SafeMode („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28480399238c1c915056d3929f8fd188cfff7eca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665508"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Startet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] im abgesicherten Modus und lädt nur die Standardumgebung und -dienste

## <a name="syntax"></a>Syntax

```
devenv /SafeMode
```

## <a name="remarks"></a>Bemerkungen
 Dieser Schalter verhindert, dass beim Start von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackages von Drittanbietern geladen werden und stellt dadurch eine stabile Ausführung sicher.

## <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] im abgesicherter Modus.

## <a name="code"></a>Code

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Weitere Informationen
 [Debug-Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md)
