---
title: -Updateconfiguration (devenv.exe) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657921"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Teilt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Pakete auf dem System zusammenzuführen und den MEF-Cache auf Änderungen zu prüfen.

## <a name="syntax"></a>Syntax

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Anmerkungen
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] führt diesen Befehl automatisch aus, wenn Sie ein VSIX-Paket installieren. Sie sollten `devenv.exe /updateconfiguration` nach dem Patchen Ihrer Dateien ausführen, damit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] den MEF-Cache aktualisiert. Dadurch können Sie feststellen, ob die Korrektur geeignet ist.

## <a name="example"></a>Beispiel
 Die folgende Befehlszeile bewirkt, dass [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Pakete auf dem System zusammenführt und den MEF-Cache auf Änderungen prüft.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Siehe auch
 [Anpassen von Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [devenv-Befehls zeilenschaltern](../../ide/reference/devenv-command-line-switches.md)
