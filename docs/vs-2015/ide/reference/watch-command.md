---
title: Befehl „Überwachung“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd362c01c996dc6a32197b9acd88f11b26c034bf
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655803"
---
# <a name="watch-command"></a>Befehl "Überwachung"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Erstellt und öffnet eine angegebene Instanz des Fensters **Überwachen** . Sie können das Fenster **Überwachen** verwenden, um die Werte von Variablen, Ausdrücken und Registern zu berechnen, um diese Werte zu berechnen und die Ergebnisse zu speichern.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argumente  
 `index`  
 Erforderlich. Die Instanznummer des Fensters „Überwachen“.  
  
## <a name="remarks"></a>Anmerkungen  
 Der `index` muss eine ganze Zahl sein. Gültige Werte sind 1, 2, 3 oder 4.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Fenster „Auto“ und „Lokal“](../../debugger/autos-and-locals-windows.md)   
 [Vorgehensweise: Bearbeiten eines Werts in einem Variablenfenster](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Vorgehensweise: Verwenden des Dialogfelds „Schnellüberwachung“](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
