---
title: Befehl „Drucken“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: e518b3c6ffc3520b408e7c1bfb1fd1703e40a8de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512469"
---
# <a name="print-command"></a>Befehl "Drucken"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Befehl "Drucken"](https://docs.microsoft.com/visualstudio/ide/reference/print-command).  
  
  
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



