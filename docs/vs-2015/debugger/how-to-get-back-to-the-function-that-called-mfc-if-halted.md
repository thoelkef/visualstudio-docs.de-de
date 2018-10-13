---
title: 'Vorgehensweise: Zurückkehren zur Funktion, die MFC aufgerufen hat, wenn angehalten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cf717fec6324d26d2f483bd0f38c3a0731f0d67
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172925"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Gewusst wie: Zurückkehren zur Funktion, die MFC aufgerufen hat, wenn die Ausführung angehalten wurde
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Bei Verwendung der **unterbrechen** Befehl die **Debuggen** im Menü des Programms angehalten jetzt in MFC, und Sie sind Sie sicher, dass das Problem in Ihrem Code können Sie das Fenster "Aufrufliste" zum Navigieren zu Ihrer Funktion zurück. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden Sie das Fenster "Aufrufliste"](../debugger/how-to-use-the-call-stack-window.md).  
  
 Manchmal wird der Code in der Meldungsverteilschleife unterbrochen. In diesem Fall ist kein Benutzercode in der Aufrufliste vorhanden. Sie können Haltepunkte (möglicherweise mit Bedingungen und Trefferanzahl) anstelle von verwenden, um dieses Problem zu vermeiden, die **unterbrechen** Befehl. Weitere Informationen finden Sie unter [Haltepunkte und Ablaufverfolgungspunkte](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>So navigieren Sie zu der Funktion, von der MFC aufgerufen wurde  
  
-   Verwenden der **Aufrufliste** Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)



