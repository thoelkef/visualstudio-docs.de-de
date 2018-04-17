---
title: Starten eines Programms | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 714d751e9855b5567bf76ccd902fada727e14ba1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="launching-a-program"></a>Starten eines Programms
Benutzer, ein Programm debuggen möchten, können F5 zum Ausführen des Debuggers in der IDE drücken. Dies startet eine Reihe von Ereignissen, die letztlich in der IDE mit einem Debugging-Modul (DE), die wiederum verbunden ist, oder angefügt, um die Anwendung wie folgt:  
  
1.  Die IDE ruft zunächst das Projektpaket, um das aktive Projekt der Projektmappe Debugeinstellungen abrufen. Die Einstellungen umfassen das Startverzeichnis, die Umgebungsvariablen, den Port an, in dem das Programm ausgeführt wird, und die DE zu verwenden, um das Programm zu erstellen, wenn angegeben. Diese Einstellungen werden an das debugpaket übergeben.  
  
2.  Wenn eine bereitgestellten Kompatibilitätsrichtlinie angegeben wird, ruft die DE des Betriebssystems, um das Programm zu starten. Als Folge der Anwendung wird gestartet, wird das Programm zur Laufzeit Umgebung geladen. Wenn ein Programm in MSIL geschrieben ist, wird z. B. die common Language Runtime aufgerufen, um das Programm ausgeführt werden.  
  
     - oder -   
  
     Wenn eine bereitgestellten Kompatibilitätsrichtlinie nicht angegeben wird, ruft der Port des Betriebssystems, um die Anwendung gestartet werden, die bewirkt, dass das Programm zur Laufzeit Umgebung geladen werden soll.  
  
    > [!NOTE]
    >  Wenn eine bereitgestellten Kompatibilitätsrichtlinie verwendet wird, um ein Programm zu starten, ist es wahrscheinlich, dass die gleichen DE an die Anwendung angefügt wird.  
  
3.  Je nachdem, ob die DE oder den Port des Programms gestartet die DE oder der Laufzeitumgebung erstellt eine Beschreibung des Programms oder Knoten danach benachrichtigt den Port, den das Programm ausgeführt wird.  
  
    > [!NOTE]
    >  Es wird empfohlen, die Laufzeitumgebung der Programm-Knoten zu erstellen, da es sich bei der Programm-Knoten eine vereinfachte Darstellung eines Programms ist, die gedebuggt werden kann. Es ist nicht erforderlich, um eine gesamte DE nur zum Erstellen und registrieren Sie einen Knoten für die Anwendung zu laden. Wenn DE konzipiert ist, ist im Prozess der IDE jedoch keine IDE ausgeführt werden, die tatsächlich ausgeführt, es muss eine Komponente sein, die an den Port einen Programm Knoten hinzufügen können.  
  
 Die neu erstellte Anwendung, sowie alle anderen Programme im Zusammenhang oder unabhängig vom stagingstatus, gestartet oder angefügt werden, um aus der gleichen IDE eine Debugsitzung zu verfassen.  
  
 Programmgesteuert, wenn der Benutzer zunächst drückt **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]des debugpaket Ruft die Projektpaket (das verknüpft mit dem Typ des Programms gestartet ist) über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> -Methode, die wiederum füllt eine <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> Struktur mit der Projektmappe aktiven Projekt Debugeinstellungen. Diese Struktur wird durch einen Aufruf an das debugpaket übergeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> Methode. Das debugpaket instanziiert dann den Sitzung Debug-Manager (SDM), der das Programm wird von einer debuggten und alle zugehörigen Debugmodule startet.  
  
 Eines der Argumente an die SDM übergeben ist die GUID des DE verwendet werden, um das Programm zu starten.  
  
 Die DE GUID ist nicht `GUID_NULL`, das SDM DE zusammen erstellt, und ruft anschließend die [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) Methode, um das Programm zu starten. Angenommen, ein Programm in systemeigenem Code geschrieben wird, klicken Sie dann `IDebugEngineLaunch2::LaunchSuspended` wahrscheinlich angerufen `CreateProcess` und `ResumeThread` (Win32-Funktionen), das Programm auszuführen.  
  
 Als Folge der Anwendung wird gestartet, wird das Programm zur Laufzeit Umgebung geladen. Die DE oder der Laufzeitumgebung erstellt dann ein [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle, um die Anwendung beschreiben und übergibt diese Schnittstelle für [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) an den Port zu benachrichtigen, dass das Programm ist ausgeführt.  
  
 Wenn `GUID_NULL` übergeben wird, und klicken Sie dann der Port des Programms wird gestartet. Sobald das Programm ausgeführt wird, erstellt die Laufzeit-Umgebung ein `IDebugProgramNode2` -Schnittstelle, um die Anwendung beschreiben und übergibt es an `IDebugPortNotify2::AddProgramNode`. Dies benachrichtigt den Port, den das Programm ausgeführt wird. Klicken Sie dann fügt der SDM das Debugmodul an das ausgeführte Programm.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md)  
 Erläutert, was passiert, nachdem ein Programm gestartet wird, und der Port wird benachrichtigt.  
  
 [Anfügen nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md)  
 Dokumente, wenn die Debugsitzung bereit, die DE an die Anwendung angefügt ist.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debugaufgaben, z. B. ein Programm starten und Auswerten von Ausdrücken.