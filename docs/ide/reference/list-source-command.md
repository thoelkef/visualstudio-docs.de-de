---
title: Befehl "Quelle auflisten"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03a5d0699fced4d01d439942081b359454bcf476
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943617"
---
# <a name="list-source-command"></a>Befehl "Quelle auflisten"
Zeigt die angegebenen Quellcodezeilen an.

## <a name="syntax"></a>Syntax

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Schalter
 /Count:`number`

 Dies ist optional. Gibt die Anzahl der anzuzeigenden Zeilen an.

 /Current

 Dies ist optional. Zeigt die aktuelle Zeile an.

 /File:`filename`

 Dies ist optional. Pfad der anzuzeigenden Datei. Ist kein Dateiname angegeben, zeigt der Befehl den Quellcode für die Zeile der aktuellen Anweisung an.

 /Line:`number`

 Dies ist optional. Zeigt eine bestimmte Zeilennummer an.

 /ShowLineNumbers:`yes|no`

 Dies ist optional. Gibt an, ob Zeilennummern angezeigt werden sollen.

## <a name="example"></a>Beispiel
 Dieses Beispiel listet den Quellcode aus Zeile 4 der Datei „Form1.vb“ mit eingeblendeten Zeilennummern an.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)