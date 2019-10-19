---
title: Befehl „Aktuellen Wert anzeigen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da9ba9572e121a9eba74cd8d624789032f1bb4a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665670"
---
# <a name="quick-watch-command"></a>Befehl "Aktuellen Wert anzeigen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt den ausgewählten oder angegebenen Text im Feld „Ausdruck“ des [Dialogfelds „Schnellansicht“](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) an. Sie können dieses Dialogfeld verwenden, um den aktuellen Wert einer Variablen, eines Ausdrucks oder den Inhalt eines Registers zu berechnen, der vom Debugger erkannt wird. Darüber hinaus können Sie den Wert jeder nicht konstanten Variablen oder den Inhalt jedes Registers ändern.

## <a name="syntax"></a>Syntax

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumente
 `text` ist optional. Der Text, der zum Dialogfeld **Schnellüberwachung** hinzugefügt werden soll.

## <a name="remarks"></a>Anmerkungen
 Wenn `text` ausgelassen wird, wird der aktuell ausgewählte Text oder das Wort an der Curserposition zum Überwachungsfenster hinzugefügt.

## <a name="example"></a>Beispiel

```
>Debug.QuickWatch
```

## <a name="see-also"></a>Siehe auch
 [Gewusst wie: Verwenden des Dialog Felds "schnell Überwachung](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) " [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
