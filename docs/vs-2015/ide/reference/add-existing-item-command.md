---
title: Befehl „Vorhandenes Element hinzufügen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2f636c2a0eb2cfdcebf383fdc7eea70f72cb90e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670227"
---
# <a name="add-existing-item-command"></a>Befehl "Vorhandenes Element hinzufügen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fügt der aktuellen Projektmappe eine vorhandene Datei hinzu und öffnet diese.

## <a name="syntax"></a>Syntax

```
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumente
 `filename` ist erforderlich. Der vollständige Pfad und der Dateiname des Elements, das einschließlich der Erweiterung der aktuellen Projektmappe hinzugefügt werden sollen. Wenn der Dateipfad oder Dateiname Leerzeichen enthalten, schließen Sie den vollständigen Pfad in Anführungszeichen ein.

## <a name="switches"></a>Schalter
 /e: `editorname` ist optional. Der Name des Editors, in dem die Datei geöffnet wird. Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.

 Die Argumentsyntax /e:`editorname` verwendet die Editornamen wie im Dialogfeld **Öffnen mit** angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist. Um ein Stylesheet im Quellcode-Editor zu öffnen, geben Sie für das Argument /e:`editorname` beispielsweise Folgendes ein:

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Bemerkungen
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.

## <a name="example"></a>Beispiel
 Dieses Beispiel fügt die Datei „Form1.frm“ der aktuellen Projektmappe zu.

```
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
