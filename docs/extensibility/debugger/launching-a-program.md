---
title: Starten eines Programms | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738478"
---
# <a name="launch-a-program"></a>Starten eines Programms
Benutzer, die ein Programm debuggen möchten, können **F5** drücken, um den Debugger von der IDE auszuführen. Damit beginnt eine Reihe von Ereignissen, die letztlich dazu führen, dass die IDE eine Verbindung zu einem Debugmodul (DE) herstellt, das wiederum wie folgt mit dem Programm verbunden oder angefügt ist:

1. Die IDE ruft zuerst das Projektpaket auf, um die aktiven Projektdebugeinstellungen der Projektmappe abzubekommen. Die Einstellungen umfassen das Startverzeichnis, die Umgebungsvariablen, den Port, in dem das Programm ausgeführt wird, und die DE, die zum Erstellen des Programms verwendet werden soll, falls angegeben. Diese Einstellungen werden an das Debugpaket übergeben.

2. Wenn ein DE angegeben ist, ruft die DE das Betriebssystem auf, um das Programm zu starten. Als Folge des Startens des Programms wird die Laufzeitumgebung des Programms geladen. Wenn z. B. ein Programm in MSIL geschrieben wird, wird die Common Language Runtime aufgerufen, um das Programm auszuführen.

    - oder -

    Wenn kein DE angegeben ist, ruft der Port das Betriebssystem auf, um das Programm zu starten, wodurch die Laufzeitumgebung des Programms geladen wird.

   > [!NOTE]
   > Wenn ein DE zum Starten eines Programms verwendet wird, ist es wahrscheinlich, dass dasselbe DE an das Programm angehängt wird.

3. Je nachdem, ob die DE oder der Port das Programm gestartet hat, erstellt die DE- oder die Laufzeitumgebung dann eine Programmbeschreibung oder einen Knoten und benachrichtigt den Port, dass das Programm ausgeführt wird.

   > [!NOTE]
   > Es wird empfohlen, dass die Laufzeitumgebung den Programmknoten erstellt, da der Programmknoten eine leichte Darstellung eines Programms ist, das gedebuggt werden kann. Es ist nicht notwendig, eine ganze DE zu laden, nur um einen Programmknoten zu erstellen und zu registrieren. Wenn de so konzipiert ist, dass es im Prozess der IDE ausgeführt wird, aber keine IDE tatsächlich ausgeführt wird, muss es eine Komponente geben, die dem Port einen Programmknoten hinzufügen kann.

   Das neu erstellte Programm, zusammen mit allen anderen Programmen, die mit derselben IDE verknüpft oder nicht verwandt sind, gestartet oder an sie angefügt werden, verfassen eine Debugsitzung.

   Programmgesteuert, wenn der Benutzer zum ersten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Mal **F5**drückt, ruft das Debugpaket das Projektpaket (das dem Typ des gestarteten Programms zugeordnet ist) über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> Methode auf, die wiederum eine <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> Struktur mit den aktiven Projektdebugeinstellungen der Projektmappe ausfüllt. Diese Struktur wird durch einen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> Methode an das Debugpaket zurückübergaben. Das Debugpaket instanziiert dann den Sitzungsdebug-Manager (SDM), der das zu debuggende Programm und alle zugehörigen Debugmodule startet.

   Eines der Argumente, die an das SDM übergeben werden, ist die GUID der DE, die zum Starten des Programms verwendet werden soll.

   Wenn die DE GUID nicht `GUID_NULL`ist, erstellt das SDM die DE mit und ruft dann die [LaunchSuspended-Methode](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) auf, um das Programm zu starten. Wenn z. B. ein Programm `IDebugEngineLaunch2::LaunchSuspended` in systemeigenem Code geschrieben ist, wird es wahrscheinlich aufrufen `CreateProcess` und `ResumeThread` (Win32-Funktionen) das Programm ausführen.

   Als Folge des Startens des Programms wird die Laufzeitumgebung des Programms geladen. Entweder die DE- oder die Laufzeitumgebung erstellt dann eine [IDebugProgramNode2-Schnittstelle,](../../extensibility/debugger/reference/idebugprogramnode2.md) um das Programm zu beschreiben, und übergibt diese Schnittstelle an [AddProgramNode,](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) um den Port zu benachrichtigen, dass das Programm ausgeführt wird.

   Wenn `GUID_NULL` übergeben, startet der Port das Programm. Sobald das Programm ausgeführt wird, erstellt `IDebugProgramNode2` die Laufzeitumgebung eine Schnittstelle `IDebugPortNotify2::AddProgramNode`zur Beschreibung des Programms und übergibt es an . Dadurch wird der Port benachrichtigt, dass das Programm ausgeführt wird. Dann fügt das SDM das Debugmodul an das laufende Programm an.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Benachrichtigung über den Hafen](../../extensibility/debugger/notifying-the-port.md) Erläutert, was passiert, nachdem ein Programm gestartet und der Port benachrichtigt wurde.

 [Anfügen nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md) Dokumente, wenn die Debugsitzung bereit ist, die DE an das Programm anzuhängen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggen von Aufgaben](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debugaufgaben, z. B. zum Starten eines Programms und Auswerten von Ausdrücken.
