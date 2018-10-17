---
title: Befehl „Aktuellen Wert anzeigen“ | Microsoft-Dokumentation
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
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: afe27d567601e43b10323f9dcc3417bcf15e9298
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269411"
---
# <a name="quick-watch-command"></a>Befehl "Aktuellen Wert anzeigen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Zeigt den ausgewählten oder angegebenen Text in das Feld Ausdruck, der die [Schnellüberwachung (Dialogfeld)](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Sie können dieses Dialogfeld verwenden, um den aktuellen Wert einer Variablen, eines Ausdrucks oder den Inhalt eines Registers zu berechnen, der vom Debugger erkannt wird. Darüber hinaus können Sie den Wert jeder nicht konstanten Variablen oder den Inhalt jedes Registers ändern.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Argumente  
 `text`  
 Dies ist optional. Der Text, der zum Dialogfeld **Schnellüberwachung** hinzugefügt werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `text` ausgelassen wird, wird der aktuell ausgewählte Text oder das Wort an der Curserposition zum Überwachungsfenster hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden Sie das Dialogfeld ' Schnellüberwachung '](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



