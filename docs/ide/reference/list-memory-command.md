---
title: Befehl "Arbeitsspeicher auflisten"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57d6c8c7821df8bd22723900ebd011c110a1857f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815181"
---
# <a name="list-memory-command"></a>Befehl "Arbeitsspeicher auflisten"
Zeigt den Inhalt des angegebenen Speicherbereichs an.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argumente
 `expression`

 Dies ist optional. Die Speicheradresse, ab der die Anzeige des Arbeitsspeicher begonnen werden soll

## <a name="switches"></a>Schalter
 /ANSI|Unicode

 Dies ist optional. Zeigen Sie den Arbeitsspeicher als Zeichen an, die den Bytes im Arbeitsspeicher entsprechen, entweder als ANSI- oder Unicode-Zeichen.

 /Count:`number`

 Dies ist optional. Bestimmt, wie viele Byte Arbeitsspeicher angezeigt werden, beginnend bei `expression`.

 /Format:`formattype`

 Dies ist optional. Formattypen für das Anzeigen von Speicherinformationen im Fenster **Arbeitsspeicher**; entweder OneByte, TwoBytes, FourBytes, EightBytes, Float (32-Bit), oder Double (64-Bit). Wenn OneByte verwendet wird, ist `/Unicode` nicht verfügbar.

 /Hex|Signed|Unsigned

 Dies ist optional. Gibt das Format zum Anzeigen von Zahlen an: mit Vorzeichen, ohne Vorzeichen oder hexadezimal.

## <a name="remarks"></a>Hinweise
 Anstatt einen kompletten **Debug.ListMemory**-Befehl mit allen Schaltern zu schreiben, können Sie den Befehl mithilfe vordefinierter Aliase aufrufen, bei denen bestimmte Schalter auf angegebene Werte voreingestellt werden. Anstatt z.B. Folgendes einzugeben:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 Können Sie Folgendes schreiben:

```cmd
>df /Count:30 /Unicode
```

 Hier finden Sie eine Liste vorhandener Aliase für den **Debug.ListMemory**-Befehl:

|Alias|Befehl und Schalter|
|-----------| - |
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**db**|Debug.ListMemory /Format:OneByte|
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**df**|Debug.ListMemory /Format:Float|
|**dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Beispiel

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)
- [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)