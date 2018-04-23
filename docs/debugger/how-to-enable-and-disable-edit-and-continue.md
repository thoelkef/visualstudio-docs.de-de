---
title: 'Vorgehensweise: Aktivieren und Deaktivieren von bearbeiten und Fortfahren (c#, VB, C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 9070913d1106eb5e2ca04160ad95c6a6fd46f752
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Vorgehensweise: Aktivieren und Deaktivieren von bearbeiten und Fortfahren (c#, VB, C++)
Sie deaktivieren oder aktivieren Sie bearbeiten und Fortfahren auf die **Optionen** Dialogfeld zur Entwurfszeit. Sie können diese Einstellung nicht ändern, während Sie debuggen.  
  
Die Funktion "Bearbeiten und Fortfahren" funktioniert nur in Debugversionen. Bei systemeigenem C++ muss die /INCREMENTAL-Option verwendet werden, damit "Bearbeiten und Fortfahren" funktioniert. Weitere Informationen zu Anforderungen für Funktionen in C++, finden Sie in diesem [Blogbeitrag](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) und [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
#### <a name="to-enabledisable-edit-and-continue"></a>So aktivieren bzw. deaktivieren Sie "Bearbeiten und Fortfahren"  
  
1.  Wenn Sie in einer Debugsitzung befinden, Beenden des Debuggens (**UMSCHALT + F5**).

2.  Optionsseite mit Debuggen öffnen (**Extras > Optionen > Debugging**).
  
3.  Wählen Sie **allgemeine**, und führen Sie einen Bildlauf nach unten bis zum **bearbeiten und Fortfahren** Kategorie (rechter Bereich).  
  
4.  Aktivieren Sie die **bearbeiten und Fortfahren aktivieren** Kontrollkästchen. Deaktivieren Sie das Kontrollkästchen, wenn Sie die Funktion deaktivieren möchten.  
  
    > [!NOTE]
    >  Wenn IntelliTrace aktiviert ist und Sie IntelliTrace-Ereignisse und Aufrufinformationen erfassen, wird „Bearbeiten und Fortfahren“ deaktiviert. Weitere Informationen finden Sie unter [IntelliTrace](../debugger/intellitrace.md).

5. (C++) Aktivieren Sie **Native bearbeiten und Fortfahren aktivieren**. Deaktivieren Sie das Kontrollkästchen, wenn Sie die Funktion deaktivieren möchten.

6. (C++) Festlegen Sie zusätzliche Optionen für systemeigenen Code.

    - **Anwenden von Änderungen beim fortfahren (nur systemeigen)**  
        Beim Fortsetzen eines unterbrochenen Prozesses kompiliert Visual Studio automatisch alle ausstehenden Codeänderungen und wendet sie an. Wenn nicht ausgewählt ist, können Sie beim Übernehmen der Änderungen, die mithilfe des Elements "Codeänderungen übernehmen" im Menü "Debuggen" auswählen.  
  
    - **Warnung bei veraltetem Code (nur systemeigen)**  
        Ruft Warnungen über veralteten Code ab. 
  
7.  Klicken Sie auf **OK**.    
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md)