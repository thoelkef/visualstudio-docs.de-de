---
title: 'Vorgehensweise: feststellen, welche DLL Absturz des Programms | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40f27e0bec20e1dd037beaa5f60ea648c0ccb171
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257096"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Vorgehensweise: feststellen, welche DLL Absturz des Programms (C#, C++, Visual Basic F#)
  
 Wenn die Anwendung während des Aufrufs einer System-DLL oder des Codes eines anderen Benutzers abstürzt, muss herausgefunden werden, welche DLL zur Zeit des Absturzes aktiv war. Wenn Sie in einer DLL außerhalb der eigenen Anwendung abgestürzt ist, können Sie identifizieren, die Ursache mithilfe der **Module** Fenster.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>So ermitteln Sie im Fenster "Module" die Stelle, die einen Absturz verursacht hat  
  
1.  Notieren Sie die Adresse, an der der Absturz stattgefunden hat.

    Wenn die Adresse in der Fehlermeldung nicht angezeigt wird, müssen Sie alternative Methoden zu verwenden, um die DLL zu identifizieren. Wenn Sie eine System-DLL vermuten, können Sie [Laden von Symbolen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) von den Microsoft-Symbolservern beim Debuggen. Andernfalls müssen möglicherweise [Erstellen einer Dumpdatei](../debugger/using-dump-files.md) mit heap Informationen stattdessen. Verschiedene [Tools](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) stehen für die debugdumpdateien erstellt.
  
2.  Auf der **Debuggen** Menü wählen **Windows**, und klicken Sie auf **Module**.  
  
3.  In der **Module** Fenster Suchen der **Adresse** Spalte. Zur Anzeige der Spalte müssen Sie möglicherweise die Bildlaufleiste verwenden.  
  
4.  Klicken Sie auf die **Adresse** Schaltfläche am Anfang der Spalte, die die DLLs Adresse nach zu sortieren.  
  
5.  Durchsuchen Sie die sortierte Liste nach der DLL, in deren Adressbereich die vom Absturz betroffene Stelle zu finden ist.  
  
6.  Sehen Sie sich die **Namen** und **Pfad** Spalten finden in der DLL-Name und Pfad.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md)   
 [Gewusst wie: Verwenden des Modulfensters](../debugger/how-to-use-the-modules-window.md)