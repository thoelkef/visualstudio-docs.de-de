---
title: Befehl „Drucken“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 65d78387c6d60d0b432db9aab175fbfe8dc2869b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666545"
---
# <a name="print-command"></a>Befehl "Drucken"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wertet einen Ausdruck aus oder zeigt angegebenen Text an  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argumente  
 `text`  
 Erforderlich. Der auszuwertende Ausdruck oder der anzuzeigende Text  
  
## <a name="remarks"></a>Anmerkungen  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
