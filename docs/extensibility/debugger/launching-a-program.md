---
title: Starten eines Programms | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46d35961e1db1acf11d544b7523a264470340de0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710876"
---
# <a name="launch-a-program"></a>Ein Programm starten
Drücken Sie die Benutzer, die ein Programm debuggen möchten, können **F5** zum Ausführen des Debuggers in der IDE. Dies beginnt mit einer Reihe von Ereignissen, die letztlich in der IDE mit einer Debug-Engine (DE), die wiederum verbunden ist, oder angefügt, um die Anwendung wie folgt:

1. Die IDE ruft zuerst das Projektpaket, um Einstellungen zum Debuggen von aktiven Projekt der Projektmappe zu erhalten. Die Einstellungen umfassen das Startverzeichnis, die Umgebungsvariablen, den Port an, in dem das Programm ausgeführt wird, und die DE zu verwenden, um das Programm erstellen, wenn angegeben. Diese Einstellungen werden an das debugpaket übergeben.

2. Wenn eine bereitgestellten Kompatibilitätsrichtlinie angegeben wird, ruft die DE das Betriebssystem das Programm zu starten. Lädt daher den Start des Programms an, die Laufzeitumgebung des Programms ein. Wenn ein Programm in MSIL geschrieben ist, wird z. B. die common Language Runtime aufgerufen, um das Programm ausgeführt werden.

    - oder - 

    Wenn eine bereitgestellten Kompatibilitätsrichtlinie nicht angegeben ist, ruft der Port des Betriebssystems, um das Programm zu starten, das Laufzeitumgebung des Programms geladen wird.

   > [!NOTE]
   >  Wenn ein DE zum Starten eines Programms verwendet wird, ist es wahrscheinlich, dass die gleichen DE an die Anwendung angefügt wird.

3. Je nachdem, ob die DE oder den Port des Programms gestartet die DE oder die Laufzeitumgebung klicken Sie dann erstellt eine Beschreibung des Programms, oder klicken Sie auf Knoten und benachrichtigt den Port, den das Programm ausgeführt wird.

   > [!NOTE]
   >  Es wird empfohlen, dass die Laufzeitumgebung den Programm-Knoten, zu erstellen, da der Programm-Knoten eine vereinfachte Darstellung ein Programm ist, die debuggt werden kann. Besteht keine Notwendigkeit einer gesamten DE nur zum Erstellen und registrieren einen Knoten für die Anwendung laden. Wenn die DE entworfen wurde gerade die IDE, jedoch keine IDE ausführen tatsächlich auszuführen, muss es eine Komponente, die an den Port einen Programm Knoten hinzufügen können.

   Die neu erstellte Anwendung, zusammen mit alle anderen Programme, verknüpft oder unabhängig vom stagingstatus, gestartet oder angefügt werden, um die gleichen IDE, eine Debugsitzung zu verfassen.

   Programmgesteuert, wenn der Benutzer zunächst drückt **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]des debugpaket Aufrufe das Projektpaket (die zugeordneten mit dem Typ der Anwendung gestartet wird) über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> -Methode, die wiederum füllt eine <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> Struktur mit den Debugeinstellungen für das aktive Projekt der Projektmappe. Diese Struktur wird durch einen Aufruf an das debugpaket übergeben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> Methode. Das debugpaket instanziiert dann die sitzungsbasierter Debug-Manager (SDM), der das Programm debuggt und alle zugeordneten Debug-Engines wird gestartet.

   Eines der Argumente übergeben, das SDM ist die GUID des DE verwendet werden, um das Programm zu starten.

   Die DE-GUID ist nicht `GUID_NULL`, das SDM zusammen erstellt die DE und ruft dann die [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) Methode, um das Programm zu starten. Wenn ein Programm in systemeigenem Code geschrieben ist z. B. `IDebugEngineLaunch2::LaunchSuspended` wahrscheinlich ruft `CreateProcess` und `ResumeThread` (Win32-Funktionen), um das Programm auszuführen.

   Daher das Programm gestartet, wird die Laufzeitumgebung des Programms geladen. Entweder die DE oder der Laufzeitumgebung erstellt dann ein [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle, um die Anwendung beschreiben und übergibt diese Schnittstelle [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) auf den Port zu benachrichtigen, dass das Programm ist ausgeführt.

   Wenn `GUID_NULL` übergeben wird, und klicken Sie dann der Port des Programms wird gestartet. Sobald das Programm ausgeführt wird, erstellt die Runtime-Umgebung eine `IDebugProgramNode2` Schnittstelle, um die Anwendung beschreiben und übergibt es an `IDebugPortNotify2::AddProgramNode`. Dadurch wird den Port, den das Programm ausgeführt wird benachrichtigt. Anschließend wird das SDM Debug-Engine an ein ausgeführtes Programm angefügt.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md) wird erläutert, was passiert, nachdem ein Programm gestartet wird, und der Port wird benachrichtigt.

 [Anfügen nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md) dokumentiert werden, wenn die Debug-Sitzung bereit, die DE an die Anwendung angefügt ist.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md) enthält Links zu verschiedenen Debuggingaufgaben ausführen, z. B. Starten eines Programms und Auswerten von Ausdrücken.