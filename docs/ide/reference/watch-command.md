---
title: "Befehl „Überwachung“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ad450688e8399ef247333685f95423e5fab7bec8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="watch-command"></a>Befehl "Überwachung"
Erstellt und öffnet eine angegebene Instanz des Fensters **Überwachen** . Sie können das Fenster **Überwachen** verwenden, um die Werte von Variablen, Ausdrücken und Registern zu berechnen, um diese Werte zu berechnen und die Ergebnisse zu speichern.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argumente  
 `index`  
 Erforderlich. Die Instanznummer des Fensters „Überwachen“.  
  
## <a name="remarks"></a>Hinweise  
 Der `index` muss eine ganze Zahl sein. Gültige Werte sind 1, 2, 3 oder 4.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Fenster „Auto“ und „Lokal“](../../debugger/autos-and-locals-windows.md)   
 [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio (Festlegen einer Überwachung von Variablen in den Fenstern „Überwachung“ und „Schnellüberwachung“ in Visual Studio)](../../debugger/watch-and-quickwatch-windows.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)