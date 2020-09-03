---
title: Befehl „Arbeitsspeicher auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672746"
---
# <a name="list-memory-command"></a>Befehl "Arbeitsspeicher auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt den Inhalt des angegebenen Speicherbereichs an.

## <a name="syntax"></a>Syntax

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argumente
 `expression` ist optional. Die Speicheradresse, ab der die Anzeige des Arbeitsspeicher begonnen werden soll

## <a name="switches"></a>Schalter
 /ANSI&#124;Unicode ist optional. Zeigen Sie den Arbeitsspeicher als Zeichen an, die den Bytes im Arbeitsspeicher entsprechen, entweder als ANSI- oder Unicode-Zeichen.

 /Count: `number` optional. Bestimmt, wie viele Byte Arbeitsspeicher angezeigt werden, beginnend bei `expression`.

 /Format: `formattype` optional. Formattypen für das Anzeigen von Speicherinformationen im Fenster **Arbeitsspeicher**; entweder OneByte, TwoBytes, FourBytes, EightBytes, Float (32-Bit), oder Double (64-Bit). Wenn OneByte verwendet wird, ist `/Unicode` nicht verfügbar.

 /Hex&#124;signierte&#124;ohne Vorzeichen. Gibt das Format zum Anzeigen von Zahlen an: mit Vorzeichen, ohne Vorzeichen oder hexadezimal.

## <a name="remarks"></a>Bemerkungen
 Anstatt einen kompletten **Debug.ListMemory**-Befehl mit allen Schaltern zu schreiben, können Sie den Befehl mithilfe vordefinierter Aliase aufrufen, bei denen bestimmte Schalter auf angegebene Werte voreingestellt werden. Anstatt z.B. Folgendes einzugeben:

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 Können Sie Folgendes schreiben:

```
>df /Count:30 /Unicode
```

 Hier finden Sie eine Liste vorhandener Aliase für den **Debug.ListMemory**-Befehl:

|Alias|Befehl und Schalter|
|-----------|--------------------------|
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**Utility**|Debug.ListMemory /Format:OneByte|
|**DC**|Debug.ListMemory /Format:FourBytes /Ansi|
|**benutzen**|Debug.ListMemory /Format:FourBytes|
|**DF**|Debug.ListMemory /Format:Float|
|**DQ**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Beispiel

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Weitere Informationen
 Liste der Befehle zum [Auflisten der Befehls](../../ide/reference/list-call-stack-command.md) [Liste Thread Befehl](../../ide/reference/list-threads-command.md) Befehlsfenster für [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
