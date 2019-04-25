---
title: Befehl „Aktuellen Wert anzeigen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a4bc73046ca32645ffcdc8c3f2978c9245aaec6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668066"
---
# <a name="quick-watch-command"></a>Befehl "Aktuellen Wert anzeigen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt den ausgewählten oder angegebenen Text im Feld „Ausdruck“ des [Dialogfelds „Schnellansicht“](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) an. Sie können dieses Dialogfeld verwenden, um den aktuellen Wert einer Variablen, eines Ausdrucks oder den Inhalt eines Registers zu berechnen, der vom Debugger erkannt wird. Darüber hinaus können Sie den Wert jeder nicht konstanten Variablen oder den Inhalt jedes Registers ändern.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Argumente  
 `text`  
 Dies ist optional. Der Text, der zum Dialogfeld **Schnellüberwachung** hinzugefügt werden soll.  
  
## <a name="remarks"></a>Anmerkungen  
 Wenn `text` ausgelassen wird, wird der aktuell ausgewählte Text oder das Wort an der Curserposition zum Überwachungsfenster hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden des Dialogfelds „Schnellüberwachung“](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
