---
title: Befehl "ShowWebBrowser"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8c97659cc6036433c5bcf2547a9f88aee56f451
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747717"
---
# <a name="showwebbrowser-command"></a>Befehl "ShowWebBrowser"

Zeigt die in einem Webbrowserfenster angegebene URL entweder in der integrierten Entwicklungsumgebung (IDE) oder außerhalb der IDE an.

## <a name="syntax"></a>Syntax

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumente
`URL`

Erforderlich. URL (Uniform Resource Locator) für die Website.

## <a name="switches"></a>Schalter
/new

Optional. Gibt an, dass die Seite in einer neuen Instanz des Webbrowsers angezeigt wird.

/ext

Optional. Gibt an, dass die Seite im Standardwebbrowser außerhalb der IDE angezeigt wird.

## <a name="remarks"></a>Anmerkungen
Der Alias für den Befehl **ShowWebBrowser** ist **navigate** oder **nav**.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird die Microsoft-Dokumentation-Homepage in einem Webbrowser außerhalb der IDE gezeigt. Falls bereits eine Instanz des Webbrowsers geöffnet ist, wird sie verwendet. Andernfalls wird eine neue Instanz gestartet.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)