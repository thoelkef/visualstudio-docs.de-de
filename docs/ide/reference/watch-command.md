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
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: bf91686a212551ef4b760d5bb2740a14f8495a1b
ms.contentlocale: de-de
ms.lasthandoff: 05/24/2017

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
