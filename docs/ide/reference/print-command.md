---
title: "Befehl „Drucken“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bba20817c03b7ff542c3af11a440ad8e619f5567
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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