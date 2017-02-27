---
title: "Benachrichtigen den Port | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ports, Benachrichtigung"
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Benachrichtigen den Port
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nachdem Sie ein Programm gestartet hat, muss der Port benachrichtigt werden wie folgt:  
  
1.  Wenn ein Programm einen neuen Anschluss Knoten erhält, sendet er ein Programm für Auswahlereignisse Builds zurück in der Debugsitzung.  Das Ereignis fügt ihm eine Schnittstelle, die das Programm darstellt.  
  
2.  Die Debuggen von Sitzungen fragt das Programm für den Bezeichner eines Debugmoduls \(DE\) anfügen kann.  
  
3.  Die Debugkonfiguration Sitzung wird überprüft, wenn DE in der Liste zulässigen DES für dieses Programm ist.  Die Debugsitzung ruft diese Liste mit den Einstellungen des aktiven Programms der Lösung ursprünglich an sie übergeben ab, durch das Debuggen Paket.  
  
     DE muss auf der zulässigen Liste sein, andernfalls wird DE nicht auf das Programm angefügt.  
  
 Programmgesteuert, wenn ein Anschluss zuerst einen neuen Knoten Programm empfängt, erstellt er eine [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle, um das Programm zu repräsentieren.  
  
> [!NOTE]
>  Dies darf nicht mit der `IDebugProgram2`\-Schnittstelle verwechselt werden, die später durch das Debugmodul \(DE\) erstellt wird.  
  
 Der Anschlusses sendet ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Programm Builds zurück an das Klickereignis Debuggen die Option Manager der Sitzung \(SDM\) mittels einer Schnittstelle für COM `IConnectionPoint` .  
  
> [!NOTE]
>  Dies darf nicht mit der `IDebugProgramCreateEvent2`\-Schnittstelle verwechselt werden, die später durch DE gesendet wird.  
  
 Zusammen mit der Ereignisschnittstelle selbst, sendet der Port, der [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)[IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) und Schnittstellen, die den Port, den Prozess und das Programm darstellen.  Das SDM ruft [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) auf, um die GUID DEs abzurufen, das das Programm gedebuggt werden kann.  Die GUID wurde ursprünglich aus der [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)\-Schnittstelle abgerufen.  
  
 Die SDM wird überprüft, wenn DE in der Liste zulässigen DES ist.  Das SDM ruft diese Liste mit den Einstellungen des aktiven Programms der Lösung ab, von ihm ursprünglich übergeben das Debuggen Paket.  DE muss auf der zulässigen Liste sein, andernfalls wird sie nicht in das Programm angefügt.  
  
 Sobald die Identität bekannt, das DEs SDM bereit ist, es an das Programm anzufügen.  
  
## Siehe auch  
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)   
 [Nach einem starten Anfügen](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)