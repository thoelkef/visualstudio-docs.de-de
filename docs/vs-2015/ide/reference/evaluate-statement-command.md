---
title: Befehl „Anweisung auswerten“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3e50b519b162201d741f2460a8e9dbbe675c16e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230320"
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



