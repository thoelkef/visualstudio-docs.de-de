---
title: 'Vorgehensweise: Debuggen über ein DLL-Projekt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a3ab401c4631da22f2afc84d2e1ec763258fc42
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515814"
---
# <a name="how-to-debug-from-a-dll-project"></a>Gewusst wie: Debuggen über ein DLL-Projekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Debuggen über ein DLL-Projekt](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-from-a-dll-project).  
  
Um mit dem Debuggen eines DLL-Projekts zu beginnen, müssen Sie die aufrufende Anwendung in den Projekteigenschaften angeben. Die Eigenschaftenseiten in C++ unterscheiden sich im Hinblick auf Layout und Inhalt von den Eigenschaftenseiten in C# und Visual Basic.  
  
 Wenn eine verwaltete DLL von nativem Code aufgerufen wird, und Sie sowohl DLL als auch Code debuggen möchten, können Sie dies in den Projekteigenschaften angeben. Weitere Informationen finden Sie unter [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  In den Express-Versionen von Visual Studio kann keine externe aufrufende Anwendung angegeben werden. Um eine DLL in einer Express-Version zu debuggen, fügen Sie der Lösung ein ausführbares Projekt hinzu, legen es als Startpunkt für die Lösung fest  und rufen Methoden in der DLL vom ausführbaren Projekt aus auf.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>So geben Sie die aufrufende Anwendung in einem C++-Projekt an  
  
1.  Mit der rechten Maustaste des Knotens "Projekt" in der **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**. Wechseln Sie zu der **Debuggen** Registerkarte.  
  
2.  Stellen Sie sicher, dass die **Konfiguration** Feld am oberen Rand des Fensters nastaven NA hodnotu **Debuggen**.  
  
3.  Wechseln Sie zu **Konfigurationseigenschaften / Debugging**.  
  
4.  In der **zu startender Debugger** wählen **lokaler Windows-Debugger** oder **Remote-Windows-Debugger**.  
  
5.  In der **Befehl** oder **Remotebefehl** hinzu, und den vollqualifizierten Pfadnamen der Anwendung.  
  
6.  Fügen Sie die notwendigen Programmargumente auf die **Befehlsargumente** Feld.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>So geben Sie die aufrufende Anwendung in einem C#- oder Visual Basic-Projekt an  
  
1.  Mit der rechten Maustaste des Knotens "Projekt" in der **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**. Wechseln Sie zu der **Debuggen** Registerkarte.  
  
     Wählen Sie **externes Programm starten**, und fügen Sie den vollqualifizierten Pfadnamen der Ausführung des Programms hinzu.  
  
     Wenn Sie Befehlszeilenargumente für das externe Programm hinzufügen müssen, fügen Sie sie in der **Befehlszeilenargumente** Feld.  
  
2.  Sie können eine Anwendung auch als URL aufrufen. (Dies empfiehlt sich u. U., wenn Sie eine verwaltete DLL debuggen, die von einer lokalen ASP.NET-Anwendung verwendet wird.)  
  
     Klicken Sie unter **Startaktion**, wählen die **Browser mit folgender URL starten:** Optionsfeld aus, und geben Sie in der URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>So debuggen Sie über das DLL-Projekt  
  
1.  Legen Sie die gewünschten Haltepunkte fest.  
  
2.  Starten Sie das Debuggen (drücken Sie F5, klicken Sie auf den grünen Pfeil, oder klicken Sie auf **Debuggen / Debugging starten**).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md)   
 [Project Settings for  C# Debug Configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Project Settings for a Visual Basic Debug Configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)



