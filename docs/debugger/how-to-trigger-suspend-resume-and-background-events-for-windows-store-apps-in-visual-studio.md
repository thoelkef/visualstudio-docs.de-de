---
title: "Ausl&#246;sen von Anhalte-, Fortsetzungs- und Hintergrundereignissen f&#252;r Windows Store-Apps in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.background_task_activate_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 824ff3ca-fedf-4cf5-b3e2-ac8dc82d40ac
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ausl&#246;sen von Anhalte-, Fortsetzungs- und Hintergrundereignissen f&#252;r Windows Store-Apps in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie nicht debuggen, steuert die Windows\-PLM \(**Process Lifetime Management**, Prozessverwaltung für Lebensdauer\) den Ausführungszustand der App, d. h. das Starten, Anhalten, Fortsetzen und Beenden der App als Reaktion auf Benutzeraktionen und den Gerätezustand. Wenn Sie debuggen, deaktiviert Windows diese Aktivierungsereignisse. In diesem Thema wird beschrieben, wie solche Ereignisse im Debugger ausgelöst werden.  
  
 Außerdem wird in diesem Thema das Debuggen von **Hintergrundaufgaben** beschrieben. Hintergrundaufgaben ermöglichen das Ausführen bestimmte Vorgänge in einem Hintergrundprozess, selbst wenn Ihre App nicht ausgeführt wird. Sie können den Debugger verwenden, um die App in den Debugmodus zu versetzen und die Hintergrundaufgabe anschließend zu debuggen, ohne die Benutzeroberfläche zu starten.  
  
 Weitere Informationen zu Prozesslebensdauer\-Verwaltung und Hintergrundaufgaben finden Sie unter [Launching, resuming, and multitasking](http://msdn.microsoft.com/de-de/04307b1b-05af-46a6-b639-3f35e297f71b).  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Auslösen von Ereignissen der Prozesslebensdauer-Verwaltung](#BKMK_Trigger_Process_Lifecycle_Management_events)  
  
 [Auslösen von Hintergrundaufgaben](#BKMK_Trigger_background_tasks)  
  
-   [Auslösen eines Hintergrundaufgabenereignisses aus einer Standarddebugsitzung](#BKMK_Trigger_a_background_task_event_from_a_standard_debug_session)  
  
-   [Auslösen einer Hintergrundaufgabe, wenn die App nicht ausgeführt wird](#BKMK_Trigger_a_background_task_when_the_app_is_not_running)  
  
 [Ereignisse zur Verwaltung der Prozesslebensdauer sowie Hintergrundaufgaben der installierten App auslösen bzw. aktivieren.](#BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app)  
  
 [Diagnostizieren von Hintergrundaufgaben-Aktivierungsfehlern](#BKMK_Diagnosing_background_task_activation_errors)  
  
##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Auslösen von Ereignissen der Prozesslebensdauer\-Verwaltung  
 Windows kann die App anhalten, wenn der Benutzer zu einem anderen Element wechselt oder Windows ein einen Zustand mit geringem Energieverbrauch wechselt. Sie können auf das `Suspending`\-Ereignis reagieren, um relevante App\- und Benutzerdaten im permanenten Speicher zu speichern und Ressourcen freizugeben. Wenn eine Anwendung nach dem Zustand **Angehalten** fortgesetzt wird, wechselt sie in den Zustand **Aktiv** und wird an der Position fortgesetzt, an der sie angehalten wurde. Sie können auf das `Resuming`\-Ereignis reagieren, um den Anwendungszustand zu aktualisieren oder wiederherzustellen und Ressourcen zurückzufordern.  
  
 Obwohl Windows versucht, so viele angehaltene Apps wie möglich im Arbeitsspeicher zu behalten, kann die App beendet werden, wenn die Ressourcen nicht ausreichen, um sie im Arbeitsspeicher zu behalten. Außerdem Ihre App auch durch einen Benutzer explizit geschlossen werden. Es gibt kein gesondertes Ereignis, um anzugeben, dass die App durch den Benutzer geschlossen wurde.  
  
 Im Visual Studio\-Debugger können Sie Ihre Apps manuell anhalten, fortsetzen und beenden, um Prozesslebenszyklusereignisse zu debuggen. So debuggen Sie ein Prozesslebenszyklusereignis:  
  
1.  Legen Sie einen Haltepunkt im Handler des Ereignisses fest, das Sie debuggen möchten.  
  
2.  Drücken Sie die Taste **F5**, um mit dem Debuggen zu beginnen.  
  
3.  Wählen Sie auf der Symbolleiste **Debugspeicherort** das Ereignis aus, das Sie auslösen möchten:  
  
     ![Aufgaben für Unterbrechen, Wiederaufnehmen, Beenden und Hintergrund](../debugger/media/dbg_suspendresumebackground.png "DBG\_SuspendResumeBackground")  
  
     Beachten Sie, dass **Anhalten und beenden** die App schließt und die Debugsitzung beendet.  
  
##  <a name="BKMK_Trigger_background_tasks"></a> Auslösen von Hintergrundaufgaben  
 Jede App kann eine Hintergrundaufgabe registrieren, um auf bestimmte Systemereignisse zu reagieren, selbst wenn die App nicht ausgeführt wird. Hintergrundaufgaben können keinen Code ausführen, der die Benutzeroberfläche direkt aktualisiert. Stattdessen zeigen sie dem Benutzer Informationen mithilfe von mit Kachelupdates, Infoanzeigerupdates und Toastbenachrichtigungen an. Weitere Informationen finden Sie unter [Supporting your app with background tasks](http://msdn.microsoft.com/de-de/4c7bb148-eb1f-4640-865e-41f627a46e8e)  
  
 Sie können die Ereignisse, die Hintergrundaufgaben für die App starten, über den Debugger auslösen.  
  
> [!NOTE]
>  Der Debugger kann nur Ereignisse auslösen, die keine Daten enthalten, z. B. Ereignisse, die eine Zustandsänderung im Gerät angeben. Sie müssen Hintergrundaufgaben, die Benutzereingaben oder andere Daten benötigen, manuell auslösen.  
  
 Bei der realistischsten Methode, um ein Hintergrundaufgabenereignis auszulösen, sollte Ihre App nicht ausgeführt werden. Das Auslösen des Ereignisses in einer Standarddebugsitzung wird jedoch ebenfalls unterstützt.  
  
###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Auslösen eines Hintergrundaufgabenereignisses aus einer Standarddebugsitzung  
  
1.  Legen Sie einen Haltepunkt im Code der Hintergrundaufgabe fest, den Sie debuggen möchten.  
  
2.  Drücken Sie die Taste **F5**, um mit dem Debuggen zu beginnen.  
  
3.  Wählen Sie die Hintergrundaufgabe, die Sie starten möchten, aus der Ereignisliste auf der Symbolleiste **Debugspeicherort** aus.  
  
     ![Aufgaben für Unterbrechen, Wiederaufnehmen, Beenden und Hintergrund](../debugger/media/dbg_suspendresumebackground.png "DBG\_SuspendResumeBackground")  
  
###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Auslösen einer Hintergrundaufgabe, wenn die App nicht ausgeführt wird  
  
1.  Legen Sie einen Haltepunkt im Code der Hintergrundaufgabe fest, den Sie debuggen möchten.  
  
2.  Öffnen Sie die Debugeigenschaftenseite für das Startprojekt. Wählen Sie im Projektmappen\-Explorer das Projekt aus. Klicken Sie im Menü **Debuggen** auf **Eigenschaften**.  
  
     Für C\+\+\-Projekte müssen Sie möglicherweise **Konfigurationseigenschaften** erweitern und anschließend **Debugging** auswählen.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Wählen Sie für Visual C\#\- und Visual Basic\-Projekte **Eigenen Code zunächst nicht starten sondern debuggen** aus.  
  
         ![Eigenschaft zum Starten der Anwendung beim Debuggen in C&#35;&#47;VB](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG\_CsVb\_DontLaunchApp")  
  
    -   Wählen Sie für JavaScript\- und Visual C\+\+\-Projekte **Nein** aus der Liste **Anwendung starten** aus.  
  
         ![Eigenschaft zum Starten des Anwendungs&#45;Debuggens in C&#43;&#43;&#47;VB](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG\_CppJs\_DontLaunchApp")  
  
4.  Drücken Sie **F5**, um die App in den Debugmodus zu versetzen. Beachten Sie, dass die Liste **Prozess** auf der Symbolleiste **Debugspeicherort** den Namen des Apppakets anzeigt, um zu signalisieren, dass der Debugmodus aktiv ist.  
  
     ![Prozessliste für Hintergrundaufgaben](../debugger/media/dbg_backgroundtask_processlist.png "DBG\_BackgroundTask\_ProcessList")  
  
5.  Wählen Sie die Hintergrundaufgabe, die Sie starten möchten, aus der Ereignisliste auf der Symbolleiste **Debugspeicherort** aus.  
  
     ![Aufgaben für Unterbrechen, Wiederaufnehmen, Beenden und Hintergrund](../debugger/media/dbg_suspendresumebackground.png "DBG\_SuspendResumeBackground")  
  
##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Ereignisse zur Verwaltung der Prozesslebensdauer sowie Hintergrundaufgaben der installierten App auslösen bzw. aktivieren.  
 Um eine App zu starten, die bereits im Debugger installiert ist, verwenden Sie das Dialogfeld "Installiertes App\-Paket debuggen". Sie können beispielsweise eine App debuggen, die aus dem Windows Store installiert wurde, oder eine App, deren Quelldateien Sie zwar besitzen, für die Sie jedoch nicht über ein Visual Studio\-Projekt verfügen. Über das Dialogfeld "Installiertes App\-Paket debuggen" können Sie eine App auf einem Visual Studio\- oder einem Remotegerät im Debugmodus starten, oder für die App den Dubugmodus festlegen, ohne sie zu starten. Weitere Informationen finden Sie im Abschnitt **Start an installed app in the debugger** der Anleitung [How to start a debugging session](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Start_an_installed_app_in_the_debugger) für [JavaScript](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md#BKMK_Start_an_installed_app_in_the_debugger) oder **Visual C\+\+, Visual C\# und Visual Basic**.  
  
 Sobald die App in den Debugger geladen ist, können Sie die oben beschriebenen Prozeduren anwenden.  
  
##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnostizieren von Hintergrundaufgaben\-Aktivierungsfehlern  
 Die Diagnoseprotokolle in der Windows\-Ereignisanzeige für die Hintergrundinfrastruktur enthalten ausführliche Informationen, die Sie zur Diagnose und Behebung von Hintergrundaufgabenfehlern verwenden können. So zeigen Sie das Protokoll an:  
  
1.  Öffnen Sie die Ereignisanzeige.  
  
2.  Wählen Sie im Bereich **AktionenAnsicht** aus, und stellen Sie sicher, dass **Analytische und Debugprotokolle einblenden** aktiviert ist.  
  
3.  Erweitern Sie in der Struktur **Ereignisanzeige \(Lokal\)** die Knoten **Anwendungs\- und Dienstprotokolle** \/ **Microsoft** \/ **Windows** \/ **BackgroundTasksInfrastructure**.  
  
4.  Wählen Sie das **Diagnose**\-Protokoll aus.  
  
## Siehe auch  
 [Testen von Store\-Apps mit Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debuggen von Apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Application lifecycle](http://msdn.microsoft.com/de-de/53cdc987-c547-49d1-a5a4-fd3f96b2259d)   
 [Launching, resuming, and multitasking](http://msdn.microsoft.com/de-de/04307b1b-05af-46a6-b639-3f35e297f71b)