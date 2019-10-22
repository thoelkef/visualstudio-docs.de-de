---
title: Befehl „Quelle auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f13689b6e3ac4db2d58c1def3a5d0dd05c219f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672321"
---
# <a name="list-source-command"></a>Befehl "Quelle auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt die angegebenen Quellcodezeilen an.

## <a name="syntax"></a>Syntax

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Schalter
 /Count: `number` optional. Gibt die Anzahl der anzuzeigenden Zeilen an.

 /Current optional. Zeigt die aktuelle Zeile an.

 /File: `filename` optional. Pfad der anzuzeigenden Datei. Ist kein Dateiname angegeben, zeigt der Befehl den Quellcode für die Zeile der aktuellen Anweisung an.

 /Line: `number` optional. Zeigt eine bestimmte Zeilennummer an.

 /ShowLineNumbers: `yes|no` optional. Gibt an, ob Zeilennummern angezeigt werden sollen.

## <a name="remarks"></a>Anmerkungen

## <a name="example"></a>Beispiel
 Dieses Beispiel listet den Quellcode aus Zeile 4 der Datei „Form1.vb“ mit eingeblendeten Zeilennummern an.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Siehe auch
 [Befehlsfenster](../../ide/reference/command-window.md) für [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
