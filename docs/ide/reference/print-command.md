---
title: Befehl „Drucken“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66175f8aa1d371386793b892c0ead5b4dd1885b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="print-command"></a>Befehl "Drucken"
Wertet einen Ausdruck aus oder zeigt angegebenen Text an  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argumente  
 `text`  
 Erforderlich. Der auszuwertende Ausdruck oder der anzuzeigende Text  
  
## <a name="remarks"></a>Hinweise  
 Sie können ein Fragezeichen (?) als Alias für diesen Befehl verwenden. Daher wird mit dem Befehl  
  
```  
>Debug.Print expA  
```  
  
 kann beispielsweise auch folgendermaßen geschrieben werden:  
  
```  
>? expA  
```  
  
 Beide Versionen dieses Befehls geben den aktuellen Wert des Ausdrucks `expA` zurück.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehl „Anweisung auswerten“](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)