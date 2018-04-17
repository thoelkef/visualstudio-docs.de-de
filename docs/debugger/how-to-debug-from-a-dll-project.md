---
title: 'Vorgehensweise: Debuggen von DLL-Projekt | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 903723616b55467a49c43986ccd6df63dea71491
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>Vorgehensweise: Debuggen von DLL-Projekt in Visual Studio
Eine Möglichkeit zum Debuggen einer DLL-Projekt wird an die aufrufende Anwendung in den Projekteigenschaften der DLL-Projekts, und dann Sie das Debuggen über das DLL-Projekt selbst starten können. Diese Methode funktioniert, muss die Anwendung die DLL aufrufen und die DLL in den Speicherort, an die Anwendung erwartet, gefunden, werden muss (, andernfalls die Anwendung möglicherweise eine andere Version der DLL zu suchen und zu laden, die stattdessen und es wird nicht die Haltepunkte erreicht). Weitere Methoden zum Debuggen von DLLs finden Sie unter [DLL-Projekte Debuggen](../debugger/debugging-dll-projects.md).
  
Wenn eine verwaltete DLL von nativem Code aufgerufen wird, und Sie sowohl DLL als auch Code debuggen möchten, können Sie dies in den Projekteigenschaften angeben. Weitere Informationen finden Sie unter [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).   

Die Eigenschaftenseiten in C++ unterscheiden sich im Hinblick auf Layout und Inhalt von den Eigenschaftenseiten in C# und Visual Basic. 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>So geben Sie die aufrufende Anwendung in einem C++-Projekt an  
  
1.  Mit der rechten Maustaste in des Projektknoten der **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**.  
  
2.  Stellen Sie sicher, dass die **Konfiguration** Feld am oberen Rand des Fensters **Debuggen**. 

    Ein **Debuggen** Konfiguration ist für diese Methode erforderlich. 
  
3.  Wechseln Sie zu **Konfigurationseigenschaften > Debuggen**.  
  
4.  In der **zu startender Debugger** wählen **lokaler Windows-Debugger** oder **Remote-Windows-Debugger**.  
  
5.  In der **Befehl** oder **Remotebefehl** hinzu, die den vollqualifizierten Pfadnamen der aufrufenden Anwendung (z. B. eine .exe-Datei).

    ![Fenster "Eigenschaften" Debuggen](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  Fügen Sie alle notwendigen Programmargumente der **Befehlsargumente** Feld.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>So geben Sie die aufrufende Anwendung in einem C#- oder Visual Basic-Projekt an  
  
1.  Mit der rechten Maustaste in des Projektknoten der **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**, und wählen Sie dann die **Debuggen** Registerkarte.

2.  Stellen Sie sicher, dass die **Konfiguration** Feld am oberen Rand des Fensters **Debuggen**.

3.  ((.NET Framework) Wählen Sie **externes Programm starten**, und fügen Sie den vollqualifizierten Pfadnamen der aufrufenden Anwendung.

4.  (.NET Core) Wählen Sie **ausführbare Datei** aus der **starten** aus, und fügen Sie dann den vollqualifizierten Pfadnamen der aufrufenden Anwendung in der **ausführbare Datei** Feld. 
  
     Wenn Sie Befehlszeilenargumente für das externe Programm hinzufügen müssen, fügen sie in der **Befehlszeilenargumente** (oder **Anwendungsargumente**) Feld.

    ![Fenster "Eigenschaften" Debuggen](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  Wenn Sie möchten, können Sie auch eine Anwendung als URL aufrufen. (Dies empfiehlt sich u. U., wenn Sie eine verwaltete DLL debuggen, die von einer lokalen ASP.NET-Anwendung verwendet wird.)  
  
     Klicken Sie unter **Startaktion**, wählen die **Start-Browser mit URL:** Optionsfeld aus, und geben Sie die URL.
  
### <a name="to-start-debugging-from-the-dll-project"></a>So debuggen Sie über das DLL-Projekt  
  
1.  Legen Sie Haltepunkte in der DLL-Projekt. 

2.  Mit der rechten Maustaste in des DLL-Projekts, und wählen Sie **als Startprojekt festlegen**. 

    (Stellen Sie außerdem sicher, dass die **Lösungskonfiguration** Feld ist immer noch auf festgelegt **Debuggen**.)   
  
3.  Starten Sie das Debuggen (drücken Sie F5, klicken Sie auf den grünen Pfeil, oder klicken Sie auf **Debuggen > Debuggen starten**).

    Haltepunkte werden in der DLL erreicht werden. Wenn Sie nicht die Haltepunkte können, stellen Sie sicher, dass Ihre DLL ausgeben (standardmäßig der **Project\Debug** Ordner) wird an einem Ort, dass die aufrufende Anwendung erwartet wird, um ihn zu finden.
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md)   
 [Project Settings for  C# Debug Configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Project Settings for a Visual Basic Debug Configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)