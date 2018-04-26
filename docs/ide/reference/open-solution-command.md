---
title: Befehl "Projektmappe öffnen"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 652305e6d5d360169645e7801e788b39b8982400
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="open-solution-command"></a>Befehl "Projektmappe öffnen"
Öffnet eine vorhandene Projektmappe und schließt alle anderen geöffneten Projektmappen.

## <a name="syntax"></a>Syntax

```
File.OpenSolution filename
```

## <a name="arguments"></a>Argumente
 `Filename`

 Erforderlich. Der vollständige Pfad und Dateiname der zu öffnenden Projektmappe.

 Die Syntax für das Argument `filename` erfordert, dass Pfade, die Leerzeichen enthalten, in Anführungszeichen gesetzt werden.

## <a name="remarks"></a>Hinweise
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die Projektmappe „Test1.sln“ geöffnet.

```
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)