---
title: 'Gewusst wie: Auslösen anhalten, fortsetzen und hintergrundereignissen während des Debuggens uwp-apps | Microsoft Docs'
ms.custom: ''
ms.date: 01/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 00e448da2f5a23c2f6aebf6e163181080949129a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481228"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Gewusst wie: Auslösen anhalten, fortsetzen und hintergrundereignissen während des Debuggens uwp-apps in Visual Studio
Wenn Sie nicht debuggen, steuert die Windows-PLM ( **Process Lifetime Management** , Prozessverwaltung für Lebensdauer) den Ausführungszustand der App, d. h. das Starten, Anhalten, Fortsetzen und Beenden der App als Reaktion auf Benutzeraktionen und den Gerätezustand. Wenn Sie debuggen, deaktiviert Windows diese Aktivierungsereignisse. In diesem Thema wird beschrieben, wie solche Ereignisse im Debugger ausgelöst werden.  
  
 Außerdem wird in diesem Thema das Debuggen von **Hintergrundaufgaben**beschrieben. Hintergrundaufgaben ermöglichen das Ausführen bestimmte Vorgänge in einem Hintergrundprozess, selbst wenn Ihre App nicht ausgeführt wird. Sie können den Debugger verwenden, um die App in den Debugmodus zu versetzen und die Hintergrundaufgabe anschließend zu debuggen, ohne die Benutzeroberfläche zu starten.  
  
 Weitere Informationen zu Prozesslebensdauer-Verwaltung und im Hintergrund Aufgaben finden Sie unter [wird gestartet, fortsetzen und Multitasking](/windows/uwp/launch-resume/index).  
  
##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Auslösen von Ereignissen der Prozesslebensdauer-Verwaltung  
 Windows kann die App anhalten, wenn der Benutzer zu einem anderen Element wechselt oder Windows ein einen Zustand mit geringem Energieverbrauch wechselt. Sie können auf das `Suspending` -Ereignis reagieren, um relevante App- und Benutzerdaten im permanenten Speicher zu speichern und Ressourcen freizugeben. Wenn eine Anwendung nach dem Zustand **Angehalten** fortgesetzt wird, wechselt sie in den Zustand **Aktiv** und wird an der Position fortgesetzt, an der sie angehalten wurde. Sie können auf das `Resuming` -Ereignis reagieren, um den Anwendungszustand zu aktualisieren oder wiederherzustellen und Ressourcen zurückzufordern.  
  
 Obwohl Windows versucht, so viele angehaltene Apps wie möglich im Arbeitsspeicher zu behalten, kann die App beendet werden, wenn die Ressourcen nicht ausreichen, um sie im Arbeitsspeicher zu behalten. Außerdem Ihre App auch durch einen Benutzer explizit geschlossen werden. Es gibt kein gesondertes Ereignis, um anzugeben, dass die App durch den Benutzer geschlossen wurde.  
  
 Im Visual Studio-Debugger können Sie Ihre Apps manuell anhalten, fortsetzen und beenden, um Prozesslebenszyklusereignisse zu debuggen. So debuggen Sie ein Prozesslebenszyklusereignis:  
  
1.  Legen Sie einen Haltepunkt im Handler des Ereignisses fest, das Sie debuggen möchten.  
  
2.  Drücken Sie die Taste **F5** , um mit dem Debuggen zu beginnen.  
  
3.  Wählen Sie auf der Symbolleiste **Debugspeicherort** das Ereignis aus, das Sie auslösen möchten:  
  
     ![Anhalten, fortsetzen, beenden und Hintergrundaufgaben](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
     Beachten Sie, dass **Anhalten und beenden** die App schließt und die Debugsitzung beendet.  
  
##  <a name="BKMK_Trigger_background_tasks"></a> Auslösen von Hintergrundaufgaben  
 Jede App kann eine Hintergrundaufgabe registrieren, um auf bestimmte Systemereignisse zu reagieren, selbst wenn die App nicht ausgeführt wird. Hintergrundaufgaben können keinen Code ausführen, der die Benutzeroberfläche direkt aktualisiert. Stattdessen zeigen sie dem Benutzer Informationen mithilfe von mit Kachelupdates, Infoanzeigerupdates und Toastbenachrichtigungen an. Weitere Informationen finden Sie unter [Supporting your app with background tasks](http://msdn.microsoft.com/en-us/4c7bb148-eb1f-4640-865e-41f627a46e8e)  
  
 Sie können die Ereignisse, die Hintergrundaufgaben für die App starten, über den Debugger auslösen.  
  
> [!NOTE]
>  Der Debugger kann nur Ereignisse auslösen, die keine Daten enthalten, z. B. Ereignisse, die eine Zustandsänderung im Gerät angeben. Sie müssen Hintergrundaufgaben, die Benutzereingaben oder andere Daten benötigen, manuell auslösen.  
  
 Bei der realistischsten Methode, um ein Hintergrundaufgabenereignis auszulösen, sollte Ihre App nicht ausgeführt werden. Das Auslösen des Ereignisses in einer Standarddebugsitzung wird jedoch ebenfalls unterstützt.  
  
###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Auslösen eines Hintergrundaufgabenereignisses aus einer Standarddebugsitzung  
  
1.  Legen Sie einen Haltepunkt im Code der Hintergrundaufgabe fest, den Sie debuggen möchten.  
  
2.  Drücken Sie die Taste **F5** , um mit dem Debuggen zu beginnen.  
  
3.  Wählen Sie die Hintergrundaufgabe, die Sie starten möchten, aus der Ereignisliste auf der Symbolleiste **Debugspeicherort** aus.  
  
     ![Anhalten, fortsetzen, beenden und Hintergrundaufgaben](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Auslösen einer Hintergrundaufgabe, wenn die App nicht ausgeführt wird  
  
1.  Legen Sie einen Haltepunkt im Code der Hintergrundaufgabe fest, den Sie debuggen möchten.  
  
2.  Öffnen Sie die Debugeigenschaftenseite für das Startprojekt. Wählen Sie im Projektmappen-Explorer das Projekt aus. Klicken Sie im Menü **Debuggen** auf **Eigenschaften**.  
  
     Erweitern Sie für C++ und JavaScript-Projekten **Konfigurationseigenschaften** und wählen Sie dann **Debuggen**.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Wählen Sie für Visual C#- und Visual Basic-Projekte **Eigenen Code zunächst nicht starten sondern debuggen**aus.  
  
         ![C&#35;&#47;VB Debuggen starten Anwendungseigenschaft](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")  
  
    -   Wählen Sie für JavaScript- und Visual C++-Projekte **Nein** aus der Liste **Anwendung starten** aus.  
  
         ![C&#43;&#43;&#47;VB starten Debug Anwendungseigenschaft](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")  
  
4.  Drücken Sie **F5** , um die App in den Debugmodus zu versetzen. Beachten Sie, dass die Liste **Prozess** auf der Symbolleiste **Debugspeicherort** den Namen des Apppakets anzeigt, um zu signalisieren, dass der Debugmodus aktiv ist.  
  
     ![Prozessliste Hintergrund](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")  
  
5.  Wählen Sie die Hintergrundaufgabe, die Sie starten möchten, aus der Ereignisliste auf der Symbolleiste **Debugspeicherort** aus.  
  
     ![Anhalten, fortsetzen, beenden und Hintergrundaufgaben](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Ereignisse zur Verwaltung der Prozesslebensdauer sowie Hintergrundaufgaben der installierten App auslösen bzw. aktivieren.  
 Verwenden der **installiertes App-Paket Debuggen** (Dialogfeld), eine app zu laden, die bereits im Debugger installiert ist. Angenommen, Sie Debuggen einer app, die von Microsoft Store installiert wurde oder eine app zu debuggen, wenn Sie die Quelldateien für die app, aber nicht Visual Studio-Projekt für die app verfügen. Die **installiertes App-Paket Debuggen** Dialogfeld können Sie eine app starten, im Debugmodus befinden, auf dem Visual Studio-Computer oder auf einem Remotegerät oder zum Festlegen der Anwendung im Debugmodus ausgeführt, aber nicht starten. Weitere Informationen finden Sie unter [eine installierte app-Paket Debuggen](../debugger/debug-installed-app-package.md).
  
 Sobald die App in den Debugger geladen ist, können Sie die oben beschriebenen Prozeduren anwenden.  
  
##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnostizieren von Hintergrundaufgaben-Aktivierungsfehlern  
 Die Diagnoseprotokolle in der Windows-Ereignisanzeige für die hintergrundinfrastruktur enthält ausführliche Informationen, die Sie zur diagnose und Behebung von hintergrundaufgabenfehlern verwenden können. So zeigen Sie das Protokoll an:  
  
1.  Öffnen Sie die Ereignisanzeige.  
  
2.  In der **Aktionen** Bereich auswählen **Ansicht** , und stellen Sie sicher, dass **anzeigen analytische und Debugprotokolle** aktiviert ist.  
  
3.  Auf der **Ereignisanzeige (lokal)** Struktur, erweitern Sie den Knoten **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows**   >  **BackgroundTasksInfrastructure**.  
  
4.  Wählen Sie das **Diagnose** -Protokoll aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Testen von UWP-Apps mit Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debug apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Anwendungslebenszyklus](/windows/uwp/launch-resume/app-lifecycle)   
 [Starten, fortsetzen und multitasking](/windows/uwp/launch-resume/index)