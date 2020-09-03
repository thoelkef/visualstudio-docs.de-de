---
title: Befehl „Überwachung“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604831"
---
# <a name="watch-command"></a>Befehl "Überwachung"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Erstellt und öffnet eine angegebene Instanz des Fensters **Überwachen** . Sie können das Fenster **Überwachen** verwenden, um die Werte von Variablen, Ausdrücken und Registern zu berechnen, um diese Werte zu berechnen und die Ergebnisse zu speichern.

## <a name="syntax"></a>Syntax

```
Debug.Watch[index]
```

## <a name="arguments"></a>Argumente
 `index` ist erforderlich. Die Instanznummer des Fensters „Überwachen“.

## <a name="remarks"></a>Bemerkungen
 Der `index` muss eine ganze Zahl sein. Gültige Werte sind 1, 2, 3 oder 4.

## <a name="example"></a>Beispiel

```
>Debug.Watch1
```

## <a name="see-also"></a>Weitere Informationen
 [Fenster](../../debugger/autos-and-locals-windows.md) "Auto" und "lokal" Gewusst [wie: Bearbeiten eines Werts in einem Variablen Fenster Gewusst](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [wie: Verwenden des Dialog Felds "schnell Überwachung](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) " [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
