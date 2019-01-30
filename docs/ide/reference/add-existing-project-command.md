---
title: Befehl "Vorhandenes Projekt hinzufügen"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cded9ecfa76114e43efa07c7bac5d5b0c314f91c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980049"
---
# <a name="add-existing-project-command"></a>Befehl "Vorhandenes Projekt hinzufügen"
Fügt der aktuellen Projektmappe ein vorhandenes Projekt hinzu.

## <a name="syntax"></a>Syntax

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumente
 `filename` ist optional. Der vollständige Pfad und der Projektname des Projekts mit Erweiterung, die der Projektmappe hinzugefügt werden sollen.

 Wenn das `filename`-Argument Leerzeichen enthält, muss es in Anführungszeichen stehen.

 Wenn kein Dateiname angegeben ist, öffnet der Befehl das Dialogfeld „Datei“, damit der Benutzer ein Projekt auswählen kann.

## <a name="remarks"></a>Hinweise
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird das [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]-Projekt, TestProject1, der aktuellen Projektmappe hinzugefügt.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)