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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f774458eb63d9e56b99a635e7b32309375a903ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199360"
---
# <a name="evaluate-statement-command"></a>Befehl "Anweisung auswerten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wertet die angegebene Anweisung aus und zeigt sie an.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Argumente  
 `text`  
 Erforderlich. Die auszuwertende Anweisung.  
  
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
 [Befehl „Drucken“](../../ide/reference/print-command.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
