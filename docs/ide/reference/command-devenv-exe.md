---
title: -Command („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2ee6f1166a543cc3dc85dfb62d19d1c5b194a16
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948165"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Öffnet die integrierte Entwicklungsumgebung (IDE) von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und führt dann den angegebenen Befehl aus.

## <a name="syntax"></a>Syntax

```cmd
devenv /command CommandName
```

## <a name="arguments"></a>Argumente
 `CommandName` ist erforderlich. Der vollständige Name eines [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Befehls oder dessen Aliasname in doppelten Anführungszeichen. Weitere Informationen zur Syntax von Befehlen und Alias finden Sie unter [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Hinweise
 Nachdem der Startvorgang abgeschlossen wurde, wird der genannte Befehl in der IDE ausgeführt. Bei Verwendung dieses Schalters wird in der IDE beim Start nicht die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Startseite angezeigt.

 Wenn ein Befehl mittels eines Add-Ins verfügbar gemacht wird, können Sie das Add-In mithilfe dieses Schalters von der Befehlszeile aus starten. Weitere Informationen finden Sie unter [Vorgehensweise: Steuern von Add-Ins mit dem Add-In-Manager](https://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).

## <a name="example"></a>Beispiel
 In diesem Beispiel wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestartet und automatisch das Makro "Open Favorite Files" ausgeführt.

```cmd
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)