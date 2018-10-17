---
title: 'Vorgehensweise: feststellen, welche DLL Absturz des Programms | Microsoft-Dokumentation'
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
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 469d4a3f42fc749a0a7a05f4a034bde28332dc57
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183169"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Gewusst wie: Feststellen, welche DLL zum Absturz des Programms geführt hat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Wenn die Anwendung während des Aufrufs einer System-DLL oder des Codes eines anderen Benutzers abstürzt, muss herausgefunden werden, welche DLL zur Zeit des Absturzes aktiv war. Wenn Sie in einer DLL außerhalb der eigenen Anwendung abgestürzt ist, können Sie identifizieren, die Ursache mithilfe der **Module** Fenster.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>So ermitteln Sie im Fenster "Module" die Stelle, die einen Absturz verursacht hat  
  
1.  Notieren Sie die Adresse, an der der Absturz stattgefunden hat.  
  
2.  Auf der **Debuggen** Menü wählen **Windows**, und klicken Sie auf **Module**.  
  
3.  In der **Module** Fenster Suchen der **Adresse** Spalte. Zur Anzeige der Spalte müssen Sie möglicherweise die Bildlaufleiste verwenden.  
  
4.  Klicken Sie auf die **Adresse** Schaltfläche am Anfang der Spalte, die die DLLs Adresse nach zu sortieren.  
  
5.  Durchsuchen Sie die sortierte Liste nach der DLL, in deren Adressbereich die vom Absturz betroffene Stelle zu finden ist.  
  
6.  Sehen Sie sich die **Namen** und **Pfad** Spalten finden in der DLL-Name und Pfad.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Debuggen von systemeigenen DLLs](../debugger/how-to-debug-native-dlls.md)   
 [Gewusst wie: Verwenden des Modulfensters](../debugger/how-to-use-the-modules-window.md)





