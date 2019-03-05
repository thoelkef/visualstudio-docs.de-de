---
title: -Command („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6daa21f9db7eef9a651577ad829d884dccf353dc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717519"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Führt den angegebenen Befehl nach dem Starten der Visual Studio-IDE aus.

## <a name="syntax"></a>Syntax

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argumente

*CommandName*

Erforderlich. Der vollständige Name eines Visual Studio-Befehls oder dessen Aliasname in doppelten Anführungszeichen. Weitere Informationen zur Syntax von Befehlen und Alias finden Sie unter [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Anmerkungen

Nachdem der Startvorgang abgeschlossen wurde, wird der genannte Befehl in der IDE ausgeführt.

::: moniker range="vs-2017"

Bei Verwendung dieses Parameters wird die Startseite beim Start nicht in der IDE angezeigt.

::: moniker-end

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