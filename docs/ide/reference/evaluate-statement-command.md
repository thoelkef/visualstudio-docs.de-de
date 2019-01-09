---
title: Befehl "Anweisung auswerten"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0be6e57c0c741420006d20c0945b9b8c8b77d51
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864124"
---
# <a name="evaluate-statement-command"></a>Befehl "Anweisung auswerten"
Wertet die angegebene Anweisung aus und zeigt sie an.

## <a name="syntax"></a>Syntax

```cmd
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argumente
 `text` ist erforderlich. Die auszuwertende Anweisung.

## <a name="remarks"></a>Hinweise
 Abhängig vom Fenster, das zur Eingabe des Befehls **Anweisung auswerten** verwendet wird, wird ein Gleichheitszeichen (=) als Vergleichsoperator oder als Zuweisungsoperator interpretiert.

 Im Fenster **Befehl** wird ein Gleichheitszeichen (=) als Vergleichsoperator interpretiert. Wenn die Werte der Variablen `a` und `b` beispielsweise unterschiedlich sind, gibt der Befehl

```cmd
>Debug.EvaluateStatement(a=b)
```

 den Wert `false` zurück.

 Im Fenster **Direkt** wird ein Gleichheitszeichen (=) dagegen als Zuweisungsoperator interpretiert. Daher wird mit dem Befehl

```cmd
>Debug.EvaluateStatement(a=b)
```

 der Variablen `a` der Wert von Variable `b` zugewiesen.

## <a name="example"></a>Beispiel

```cmd
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Siehe auch

- [Befehl "Drucken"](../../ide/reference/print-command.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)