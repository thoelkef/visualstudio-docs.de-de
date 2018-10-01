---
title: Befehl „Überwachung“ | Microsoft-Dokumentation
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
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d06e15f23a8f75e4a771b9db1991f5aba2ffc0d8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516025"
---
# <a name="watch-command"></a>Befehl "Überwachung"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Befehl](https://docs.microsoft.com/visualstudio/ide/reference/watch-command).  
  
  
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
 [Vorgehensweise: Bearbeiten eines Werts in einem Variablenfenster](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Vorgehensweise: Verwenden Sie das Dialogfeld ' Schnellüberwachung '](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)



