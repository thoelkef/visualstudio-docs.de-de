---
title: Befehl "Quelle auflisten"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c211773f20ab4643b62c8c71fc6ae6581a91987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747901"
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

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)