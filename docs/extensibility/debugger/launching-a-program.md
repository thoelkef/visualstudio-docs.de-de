---
title: "Starten eines Programms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, starten"
  - "Starten von Programmen"
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Starten eines Programms
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Benutzer, die ein Programm debuggen möchten, können F5 drücken, um den Debugger über die IDE auszuführen.  Dadurch wird eine Reihe von Ereignissen, die letztlich die IDE dazu führen, dass an eine Debug\- Modul \(DE\) herstellt, das wiederum verbunden ist, angehängt oder zum Programm wie folgt:  
  
1.  Die IDE\-ersten Rufe das Projekt Paket, um die Einstellungen des aktuellen Projekts Debuggen der Projektmappe abzurufen.  Die Einstellungen zählen das Startverzeichnis, um die Umgebungsvariablen, den Port, auf die das Programm ausgeführt wird, und DE, mit dem das Programm zu erstellen, wenn sie angegeben werden.  Diese Einstellungen werden zum Debuggen von Paket übergeben.  
  
2.  Wenn DE angegeben wird, ruft das Betriebssystem DE auf, um das Programm zu starten.  Daraus folgt das Programm starten, wird die Laufzeitumgebung des Programms geladen.  Wenn beispielsweise ein Programm in MSIL geschrieben wird, wird die Common Language Runtime \(CLR\) aufgerufen, um das Programm auszuführen.  
  
     \- oder \-  
  
     Wenn DE nicht angegeben ist, wird der Anschluss das Betriebssystem an, um das Programm zu starten, die die Laufzeitumgebung des Programms wird geladen.  
  
    > [!NOTE]
    >  Wenn DE verwendet wird, um ein Programm zu starten, ist es wahrscheinlich, dass dieselbe DE dem Programm angefügt wird.  
  
3.  Abhängig davon, ob der Port oder DE starteten das Programm erstellt DE oder die Laufzeitumgebung dann eine Beschreibung des Programms oder Knoten und benachrichtigt den Port, dass das Programm ausgeführt wird.  
  
    > [!NOTE]
    >  Es wird empfohlen, dass die Laufzeitumgebung den Knoten Programm erstellt, da der Knoten Programm eine einfache Darstellung eines Programms, das gedebuggt werden kann.  Es ist nicht erforderlich, ebenso oben DE ganzes zu laden, um einen Knoten Programm zu erstellen und zu registrieren.  Wenn DE entwickelt wurde, um sich bei der IDE ausgeführt, aber kein IDE tatsächlich ausgeführt wird, muss eine Komponente vorhanden sein, die einen Anschluss dem Knoten Programm hinzufügen kann.  
  
 Das neu erstellte Programm zusammen mit allen anderen Programmen, die verknüpft werden, oder auf den gleichen IDE gestartet oder angefügt nicht verknüpft, Zusammensetzen einer Debugsitzung.  
  
 Programmgesteuert, wenn der Benutzer zuerst **F5**klickt, ruft der vsprvss Paket Debuggen des Projekts \(das Paket mit dem Typ des Programms zugeordnet ist, die gestartet wird\) von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>\-Methode, die wiederum eine <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> Struktur mit den Einstellungen des aktuellen Projekts Debuggen der Projektmappe geändert.  Diese Struktur wird zurück zum Debuggen von Pakets durch einen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>\-Methode übergeben.  Das Paket Debuggen instanziiert dann den Debug\- Manager der Sitzung \(SDM\), der das Programm, das gedebuggt wird und alle zugeordneten Debugmodule.  
  
 Eines der Argumente, die an das SDM übergebenen GUID ist das zum Starten verwendet werden soll DEs, das Programm.  
  
 Wenn keine GUIDs DE `GUID_NULL`ist, erstellt das SDM DE und ruft anschließend die [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)\-Methode auf, um das Programm zu starten.  Wenn beispielsweise ein Programm in systemeigenem Code geschrieben wird, `IDebugEngineLaunch2::LaunchSuspended` wird wahrscheinlich `CreateProcess` und `ResumeThread` \(Win32\-Funktionen\) an, um das Programm auszuführen.  
  
 Daraus folgt das Programm starten, wird die Laufzeitumgebung des Programms geladen.  Entweder DE oder die Laufzeitumgebung erstellt eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)\-Schnittstelle, um das Programm zu beschreiben und übergibt diese Schnittstelle an [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) , um den Port zu benachrichtigen, dass das Programm ausgeführt wird.  
  
 Wenn `GUID_NULL` übergeben wird, dann wird der Anschluss das Programm.  Nachdem das Programm ausgeführt wird, erstellt die Laufzeitumgebung eine `IDebugProgramNode2`\-Schnittstelle, um das Programm zu beschreiben und übergibt sie an `IDebugPortNotify2::AddProgramNode`.  Dies weist den Port, dass das Programm ausgeführt wird.  Anschließend fügt das SDM das Debugmodul an den laufenden Programm an.  
  
## In diesem Abschnitt  
 [Benachrichtigen den Port](../../extensibility/debugger/notifying-the-port.md)  
 Erläutert, was geschieht, wenn ein Programm gestartet wird und der Port benachrichtigt wird.  
  
 [Nach einem starten Anfügen](../../extensibility/debugger/attaching-after-a-launch.md)  
 Dokumente, wenn die Debugsitzung bereit ist, DE dem Programm anzufügen.  
  
## Verwandte Abschnitte  
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu den verschiedenen Aufgaben Debuggen eines Programms starten, z und Auswerten von Ausdrücken.