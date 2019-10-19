---
title: Befehl „Anweisung auswerten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657707"
---
# <a name="evaluate-statement-command"></a>Befehl "Anweisung auswerten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wertet die angegebene Anweisung aus und zeigt sie an.

## <a name="syntax"></a>Syntax

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argumente
 `text` ist erforderlich. Die auszuwertende Anweisung.

## <a name="remarks"></a>Anmerkungen
 Abhängig vom Fenster, das zur Eingabe des Befehls **Anweisung auswerten** verwendet wird, wird ein Gleichheitszeichen (=) als Vergleichsoperator oder als Zuweisungsoperator interpretiert.

 Im Fenster **Befehl** wird ein Gleichheitszeichen (=) als Vergleichsoperator interpretiert. Wenn die Werte der Variablen `a` und `b` beispielsweise unterschiedlich sind, gibt der Befehl

```
>Debug.EvaluateStatement(a=b)
```

 den Wert `false` zurück.

 Im Fenster **Direkt** wird ein Gleichheitszeichen (=) dagegen als Zuweisungsoperator interpretiert. Daher wird mit dem Befehl

```
>Debug.EvaluateStatement(a=b)
```

 der Variablen `a` der Wert von Variable `b` zugewiesen.

## <a name="example"></a>Beispiel

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Siehe auch
 Befehl " [Drucken](../../ide/reference/print-command.md) " [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
