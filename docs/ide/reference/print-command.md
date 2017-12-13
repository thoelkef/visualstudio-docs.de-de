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
ms.openlocfilehash: 6eaf5d77da1dbc6e005764087dad338458e7ce8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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
 Sie können ein Fragezeichen (?) als Alias für diesen Befehl verwenden. Der Befehl  
  
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