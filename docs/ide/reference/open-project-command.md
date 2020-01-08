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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c1034fbbafa04af2d62526fdbb48812d64e050
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565811"
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

## <a name="remarks"></a>Hinweise

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
