---
title: 'Vorgehensweise: Feststellen, welche DLL Absturz des Programms | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 44ebe042ff6e2507530e4be410e768550e922b44
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703629"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Vorgehensweise: Feststellen Sie, welche DLL Absturz des Programms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Wenn die Anwendung während des Aufrufs einer System-DLL oder des Codes eines anderen Benutzers abstürzt, muss herausgefunden werden, welche DLL zur Zeit des Absturzes aktiv war. Wenn Sie feststellen, dass eine DLL außerhalb der eigenen Anwendung abgestürzt ist, kann die Ursache mithilfe des Fensters **Module** ermittelt werden.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>So ermitteln Sie im Fenster "Module" die Stelle, die einen Absturz verursacht hat  
  
1. Notieren Sie die Adresse, an der der Absturz stattgefunden hat.  
  
2. Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie auf **Module**.  
  
3. Suchen Sie im Fenster **Module** die Spalte **Adresse**. Zur Anzeige der Spalte müssen Sie möglicherweise die Bildlaufleiste verwenden.  
  
4. Klicken Sie im oberen Spaltenbereich auf die Schaltfläche **Adresse**, um die DLLs der Adresse nach zu sortieren.  
  
5. Durchsuchen Sie die sortierte Liste nach der DLL, in deren Adressbereich die vom Absturz betroffene Stelle zu finden ist.  
  
6. Namen und Pfad der DLL finden Sie in der Spalte **Name** bzw. **Pfad**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Debuggen von systemeigenen DLLs](../debugger/how-to-debug-native-dlls.md)   
 [Vorgehensweise: Verwenden des Modulfensters](../debugger/how-to-use-the-modules-window.md)
