---
title: Projekt öffnen (Befehl)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e9249088b188fde1b346772ab1230d33160fe59
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996816"
---
# <a name="open-project-command"></a>Projekt öffnen (Befehl)

Öffnet ein vorhandenes Projekt oder eine vorhandene Projektmappe.

## <a name="syntax"></a>Syntax

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumente

`filename`

Erforderlich. Der vollständige Pfad und Dateiname des zu öffnenden Projekts oder der zu öffnenden Projektmappe.

> [!NOTE]
> Die Syntax für das Argument `filename` erfordert, dass Pfade, die Leerzeichen enthalten, in Anführungszeichen gesetzt werden.

## <a name="remarks"></a>Anmerkungen

Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.

Dieser Befehl ist während des Debuggens nicht verfügbar.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird das Visual Basic-Projekt **Test1** geöffnet:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)