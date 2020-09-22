---
title: 'Vorgehensweise: Debuggen über ein DLL-Projekt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841171"
---
# <a name="how-to-debug-from-a-dll-project"></a>Gewusst wie: Debuggen über ein DLL-Projekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um mit dem Debuggen eines DLL-Projekts zu beginnen, müssen Sie die aufrufende Anwendung in den Projekteigenschaften angeben. Die Eigenschaftenseiten in C++ unterscheiden sich im Hinblick auf Layout und Inhalt von den Eigenschaftenseiten in C# und Visual Basic.  
  
 Wenn eine verwaltete DLL von nativem Code aufgerufen wird, und Sie sowohl DLL als auch Code debuggen möchten, können Sie dies in den Projekteigenschaften angeben. Weitere Informationen finden Sie unter Gewusst [wie: Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
> In den Express-Versionen von Visual Studio kann keine externe aufrufende Anwendung angegeben werden. Um eine DLL in einer Express-Version zu debuggen, fügen Sie der Lösung ein ausführbares Projekt hinzu, legen es als Startpunkt für die Lösung fest  und rufen Methoden in der DLL vom ausführbaren Projekt aus auf.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>So geben Sie die aufrufende Anwendung in einem C++-Projekt an  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Eigenschaften**aus. Wechseln Sie zur Registerkarte **Debuggen** .  
  
2. Stellen Sie sicher, dass das Feld **Konfiguration** am oberen Rand des Fensters auf **Debuggen** festgelegt ist.  
  
3. Wechseln Sie zu **Konfigurations Eigenschaften/Debuggen**.  
  
4. Wählen Sie in der Liste **zu startender Debugger** die Option **lokaler Windows-Debugger** oder **Remote-Windows-Debugger**aus.  
  
5. Fügen Sie im Feld **Befehl** oder **Remote Befehl** den voll qualifizierten Pfadnamen der Anwendung hinzu.  
  
6. Fügen Sie die notwendigen Programmargumente in das Feld **Befehlsargumente** ein.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>So geben Sie die aufrufende Anwendung in einem C#- oder Visual Basic-Projekt an  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Eigenschaften**aus. Wechseln Sie zur Registerkarte **Debuggen** .  
  
     Wählen Sie **externes Programm starten**aus, und fügen Sie den voll qualifizierten Pfadnamen des Programms ein, das ausgeführt werden soll.  
  
     Wenn Sie die Befehlszeilenargumente des externen Programms hinzufügen müssen, fügen Sie Sie in das Feld **Befehlszeilenargumente** ein.  
  
2. Sie können eine Anwendung auch als URL aufrufen. (Dies empfiehlt sich u. U., wenn Sie eine verwaltete DLL debuggen, die von einer lokalen ASP.NET-Anwendung verwendet wird.)  
  
     Wählen Sie unter **Start Aktion**die Options Schaltfläche **Browser in URL starten** aus, und geben Sie die URL ein.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>So debuggen Sie über das DLL-Projekt  
  
1. Legen Sie die gewünschten Haltepunkte fest.  
  
2. Starten Sie das Debugging (drücken Sie F5, klicken Sie auf den grünen Pfeil, oder klicken Sie auf **Debuggen/Debugging starten**)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugging von DLL-Projekten](../debugger/debugging-dll-projects.md)   
 [Projekteinstellungen für c#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Projekteinstellungen für eine Visual Basic Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
