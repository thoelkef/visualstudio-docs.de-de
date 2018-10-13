---
title: 'Vorgehensweise: Debuggen im gemischten Modus | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a08cf3cf95073d06c1dfa350f2de86bf72837c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182675"
---
# <a name="how-to-debug-in-mixed-mode"></a>Gewusst wie: Debuggen im gemischten Modus
Die folgenden Verfahren wird beschrieben, wie debugging für das Debuggen von verwaltetem und systemeigenem Code gemeinsam, auch bekannt als im gemischten Modus zu aktivieren. Es gibt zwei Szenarios des Debuggens im gemischten Modus:  
  
- Die app, die aufruft, eine DLL in systemeigenem Code geschrieben ist, und die DLL wird verwaltet. 
  
- Die app, die eine DLL-Datei aufruft, ist in verwaltetem Code geschrieben, und die DLL in systemeigenem Code ist. Ein Lernprogramm, das dieses Szenario ausführlicher behandelt, finden Sie unter [verwalteten und systemeigenen Code Debuggen](../debugger/how-to-debug-managed-and-native-code.md).
   
Sie können sowohl verwaltete als auch systemeigene Debugger in der aufrufenden app-Projekt **Eigenschaft** Seiten. Die Einstellungen unterscheiden sich zwischen nativen und verwalteten apps. 

Wenn Sie keinen Zugriff auf eine aufrufende app-Projekt haben, können Sie die DLL aus dem DLL-Projekt debuggen. Im gemischten Modus nur das DLL-Projekt zu Debuggen ist nicht erforderlich. Weitere Informationen finden Sie unter [Vorgehensweise: Debuggen über ein DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md). 

> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können von den in diesem Artikel, abhängig von der Visual Studio-Einstellungen oder die Edition abweichen. Wählen Sie zum Ändern Ihrer Einstellungen **Tools** > **Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Aktivieren Sie Debuggen im gemischten Modus für eine native aufrufende app  
  
1. Wählen Sie das C++-Projekt in **Projektmappen-Explorer** , und klicken Sie auf die **Eigenschaften** Symbol, drücken Sie **Alt**+**EINGABETASTE**, oder mit der rechten Maustaste, und wählen Sie **Eigenschaften**.
   
1. In der  **\<Projekt > Eigenschaftenseiten** Dialogfeld erweitern Sie **Konfigurationseigenschaften**, und wählen Sie dann **Debuggen**.  
   
1. Legen Sie **Debuggertyp** zu **gemischten** oder **automatisch**.
   
1. Klicken Sie auf **OK**.
   
   ![Aktivieren Sie das Debuggen im gemischten Modus](../debugger/media/dbg-mixed-mode-from-native.png "Debuggen im gemischten Modus aktivieren")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Aktivieren des Debuggens im gemischten Modus für eine verwaltete app aus aufrufen  
  
1. Wählen Sie das C#- oder Visual Basic-Projekt in **Projektmappen-Explorer** , und wählen Sie die **Eigenschaften** Symbol, drücken Sie **Alt**+**EINGABETASTE**, oder mit der rechten Maustaste, und wählen Sie **Eigenschaften**.
   
1. Wählen Sie die **Debuggen** Registerkarte, und wählen Sie dann **Debuggen von nativem Code aktivieren**.
   
1. Verwendung **Datei** > **ausgewählte Elemente speichern** oder **STRG + S** um Änderungen zu speichern.

   ![Debuggen von nativem Code aktivieren](../debugger/media/dbg-mixed-mode-from-csharp.png "Debuggen von nativem Code aktivieren")
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Debuggen über ein DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md)