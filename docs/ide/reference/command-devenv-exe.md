---
title: -Command („devenv.exe“)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dfc52c66fd56f2d3d7954584804cfd4e3e75ee24
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227953"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Führt den angegebenen Befehl nach dem Starten der Visual Studio-IDE aus.

## <a name="syntax"></a>Syntax

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argumente

- *CommandName*

  Erforderlich. Der vollständige Name eines Visual Studio-Befehls oder dessen Aliasname in doppelten Anführungszeichen. Weitere Informationen zur Syntax von Befehlen und Alias finden Sie unter [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Hinweise

Nachdem der Startvorgang abgeschlossen wurde, wird der genannte Befehl in der IDE ausgeführt. Bei Verwendung dieses Schalters wird in der IDE beim Start nicht die Visual Studio-Startseite angezeigt.

Wenn ein Befehl mittels eines Add-Ins verfügbar gemacht wird, können Sie das Add-In mithilfe dieses Schalters von der Befehlszeile aus starten. Weitere Informationen finden Sie unter [Vorgehensweise: Steuern von Add-Ins mit dem Add-In-Manager](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Beispiel

Im ersten Beispiel wird Visual Studio gestartet und automatisch das Makro „Open Favorite Files“ ausgeführt.

Im zweiten Beispiel wird eine Webbrowser-Registerkarte in der IDE geöffnet und zur Website mit der Microsoft-Dokumentation navigiert.

Im dritten Beispiel wird eine neue Datei namens `some_file.cs` erstellt und diese Datei in einem Code-Editor geöffnet.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Befehlsfenster](command-window.md)