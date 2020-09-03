---
title: Befehl „Datei öffnen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c8dcf35e4c045db0d9acd45e2eb307a31ba39f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671931"
---
# <a name="open-file-command"></a>Befehl "Datei öffnen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öffnet eine vorhandene Datei und ermöglicht die Angabe eines Editors.

## <a name="syntax"></a>Syntax

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumente
 `filename` ist erforderlich. Der vollständige oder partielle Pfad und Dateiname der zu öffnenden Datei. Pfade, die Leerzeichen enthalten, müssen in Anführungszeichen eingeschlossen werden.

## <a name="switches"></a>Schalter
 /e: `editorname` ist optional. Der Name des Editors, in dem die Datei geöffnet wird. Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.

 Die Argumentsyntax /e:`editorname` verwendet die Editornamen wie im Dialogfeld „Öffnen mit“ angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist.

 Geben Sie zum Öffnen einer Datei im Quellcode-Editor für das Argument /e:`editorname` beispielsweise Folgendes ein:

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Bemerkungen
 Bei der automatischen Vervollständigung wird während der Eingabe eines Pfads versucht, den richtigen Pfad und Dateinamen zu finden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die Stildatei „Test1.css“ im Quellcode-Editor geöffnet.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [direkt Fenster](../../ide/reference/immediate-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
