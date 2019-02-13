---
title: Befehl "Vorhandenes Element hinzufügen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8ab2ce6e9f1260172bf0ffbf0aede9138a5115f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951565"
---
# <a name="add-existing-item-command"></a>Befehl "Vorhandenes Element hinzufügen"
Fügt der aktuellen Projektmappe eine vorhandene Datei hinzu und öffnet diese.

## <a name="syntax"></a>Syntax

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumente
 `filename` ist erforderlich. Der vollständige Pfad und der Dateiname des Elements, das einschließlich der Erweiterung der aktuellen Projektmappe hinzugefügt werden sollen. Wenn der Dateipfad oder Dateiname Leerzeichen enthalten, schließen Sie den vollständigen Pfad in Anführungszeichen ein.

## <a name="switches"></a>Schalter
 /e: `editorname` ist optional. Der Name des Editors, in dem die Datei geöffnet wird. Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.

 Die Argumentsyntax /e:`editorname` verwendet die Editornamen wie im Dialogfeld **Öffnen mit** angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist. Um ein Stylesheet im Quellcode-Editor zu öffnen, geben Sie für das Argument /e:`editorname` beispielsweise Folgendes ein:

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Hinweise
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.

## <a name="example"></a>Beispiel
 Dieses Beispiel fügt die Datei „Form1.frm“ der aktuellen Projektmappe zu.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)