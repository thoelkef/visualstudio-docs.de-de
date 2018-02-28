---
title: "Befehl „Anweisung auswerten“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b3f0d5ecdcf1318490ac0829bb9dd6ded9519872
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="evaluate-statement-command"></a>Befehl "Anweisung auswerten"
Wertet die angegebene Anweisung aus und zeigt sie an.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Argumente  
 `text`  
 Erforderlich. Die auszuwertende Anweisung.  
  
## <a name="remarks"></a>Hinweise  
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
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)