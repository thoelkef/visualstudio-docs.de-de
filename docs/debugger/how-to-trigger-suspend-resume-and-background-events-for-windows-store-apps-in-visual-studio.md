---
title: Trigger anhalten, fortsetzen und im Hintergrund von Ereignissen beim Debuggen von UWP | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 01/16/2018
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: b1fa94c632ad4296eac4eb81ca3e172ad0893b86
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018578"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Wie Sie auslösen, anhalten, fortsetzen und im Hintergrund von Ereignissen beim Debuggen von UWP-apps in Visual Studio
Wenn Sie nicht debuggen, steuert die Windows-PLM ( **Process Lifetime Management** , Prozessverwaltung für Lebensdauer) den Ausführungszustand der App, d. h. das Starten, Anhalten, Fortsetzen und Beenden der App als Reaktion auf Benutzeraktionen und den Gerätezustand. Wenn Sie debuggen, deaktiviert Windows diese Aktivierungsereignisse. In diesem Thema wird beschrieben, wie solche Ereignisse im Debugger ausgelöst werden.  
  
 Außerdem wird in diesem Thema das Debuggen von **Hintergrundaufgaben**beschrieben. Hintergrundaufgaben ermöglichen das Ausführen bestimmte Vorgänge in einem Hintergrundprozess, selbst wenn Ihre App nicht ausgeführt wird. Sie können den Debugger verwenden, um die App in den Debugmodus zu versetzen und die Hintergrundaufgabe anschließend zu debuggen, ohne die Benutzeroberfläche zu starten.  
  
 Weitere Informationen zu Prozesslebensdauer-Verwaltung und Hintergrundaufgaben finden Sie unter [Launching, resuming, and multitasking](/windows/uwp/launch-resume/index).  
  
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
 Jede App kann eine Hintergrundaufgabe registrieren, um auf bestimmte Systemereignisse zu reagieren, selbst wenn die App nicht ausgeführt wird. Hintergrundaufgaben können keinen Code ausführen, der die Benutzeroberfläche direkt aktualisiert. Stattdessen zeigen sie dem Benutzer Informationen mithilfe von mit Kachelupdates, Infoanzeigerupdates und Toastbenachrichtigungen an. Weitere Informationen finden Sie unter [Supporting your app with background tasks](https://msdn.microsoft.com/library/4c7bb148-eb1f-4640-865e-41f627a46e8e)  
  
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
  
         ![C&#35;&#47;Anwendungseigenschaft für VB Debuggen starten](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")  
  
    -   Wählen Sie für JavaScript- und Visual C++-Projekte **Nein** aus der Liste **Anwendung starten** aus.  
  
         ![C&#43;&#43;&#47;VB Starten der Anwendung Debug-Eigenschaft](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")  
  
4.  Drücken Sie **F5** , um die App in den Debugmodus zu versetzen. Beachten Sie, dass die Liste **Prozess** auf der Symbolleiste **Debugspeicherort** den Namen des Apppakets anzeigt, um zu signalisieren, dass der Debugmodus aktiv ist.  
  
     ![Hintergrund Prozessliste](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")  
  
5.  Wählen Sie die Hintergrundaufgabe, die Sie starten möchten, aus der Ereignisliste auf der Symbolleiste **Debugspeicherort** aus.  
  
     ![Anhalten, fortsetzen, beenden und Hintergrundaufgaben](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Ereignisse zur Verwaltung der Prozesslebensdauer sowie Hintergrundaufgaben der installierten App auslösen bzw. aktivieren.  
 Verwenden der **Debuggen Installed App Package** Dialogfeld, um eine app zu starten, die bereits in den Debugger installiert ist. Sie können z. B. Debuggen einer app, die über Microsoft Store installiert wurde oder Debuggen einer app aus, wenn Sie die Quelldateien für die app, aber nicht Visual Studio-Projekt für die app verfügen. Die **Debuggen Installed App Package** Dialogfeld können Sie Starten einer app im Debugmodus auf dem Visual Studio-Computer oder auf einem Remotegerät, oder legen Sie die app im Debugmodus ausgeführt, aber nicht gestartet wird. Weitere Informationen finden Sie unter [Debuggen eines installierten app-Pakets](../debugger/debug-installed-app-package.md).
  
 Sobald die App in den Debugger geladen ist, können Sie die oben beschriebenen Prozeduren anwenden.  
  
##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnostizieren von Hintergrundaufgaben-Aktivierungsfehlern  
 Die Diagnoseprotokolle in der Windows-Ereignisanzeige für die Hintergrundinfrastruktur enthalten ausführliche Informationen, die Sie zur Diagnose und Behebung von Hintergrundaufgabenfehlern verwenden können. So zeigen Sie das Protokoll an:  
  
1.  Öffnen Sie die Ereignisanzeige.  
  
2.  Wählen Sie im Bereich **Aktionen** die Option **Ansicht** aus, und stellen Sie sicher, dass **Show Analytic and Debug Logs** (Analytische Protokolle und Debugprotokolle einblenden) aktiviert ist.  
  
3.  Wählen Sie auf der Symbolleiste **Ereignisanzeige (Lokal)** die Knoten **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **BackgroundTasksInfrastructure**beschrieben.  
  
4.  Wählen Sie das **Diagnose** -Protokoll aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Testen von UWP-Apps mit Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debug apps in Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)   
 [Anwendungslebenszyklus](/windows/uwp/launch-resume/app-lifecycle)   
 [Launching, resuming, and multitasking](/windows/uwp/launch-resume/index)