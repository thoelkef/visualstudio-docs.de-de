---
title: Projekt öffnen (Befehl)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34a6783e71d2a6dfee718aa441fbb3007aa71fa9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946239"
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