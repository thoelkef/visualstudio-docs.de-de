---
title: "Bestimmen des Status des Befehls mithilfe von Interop-Assemblys | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interop-Assemblys, die Bestimmung des Befehlsstatus"
  - "Befehlsbehandlung mit Interop-Assemblys, status"
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Bestimmen des Status des Befehls mithilfe von Interop-Assemblys
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein VSPackage muss den Status der Befehle von verfolgt, die nicht verarbeitet werden können. Die Umgebung kann nicht bestimmt werden, wenn ein Befehl in das VSPackage behandelt aktiviert oder deaktiviert wird. Es handelt sich um die Verantwortung für das VSPackage um die Umgebung zum Befehl Status zu informieren, z. B. der Status der allgemeine Befehle wie **Ausschneiden**, **Kopie**, und **Einfügen**.  
  
## Status Benachrichtigungsquellen  
 Die Umgebung empfängt Informationen über die VSPackages' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, die Teil der Implementierung des VSPackage ist von der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \-Methode des VSPackages in zwei Situationen:  
  
-   Die Umgebung ausgeführt wird, wenn ein Benutzer ein Hauptmenü oder im Kontextmenü \(durch Rechtsklick\) geöffnet wird, die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode für alle Befehle in diesem Menü, deren Status zu bestimmen.  
  
-   Wenn das VSPackage angefordert wird, dass die Umgebung die aktuelle Benutzeroberfläche \(UI\) aktualisieren. In diesem Fall wie die Befehle, die derzeit für den Benutzer sichtbar, z. B. sind die **Ausschneiden**, **Kopie**, und **Einfügen** auf der Symbolleiste standard gruppieren, werden aktiviert und deaktiviert als Antwort auf den Kontext und Benutzeraktionen.  
  
 Da die Shell mehrere VSPackages hostet, würde die Shell\-Leistung unannehmbar beeinträchtigen, wenn er erforderlich waren, um jede VSPackage zum Bestimmen des Status des Befehls abrufen. Stattdessen sollten Ihr VSPackage die Umgebung aktiv benachrichtigen, wenn zum Zeitpunkt der Änderung die Benutzeroberfläche ändert. Weitere Informationen über die Benachrichtigung über Updates, finden Sie unter [Aktualisieren der Benutzeroberfläche](../../extensibility/updating-the-user-interface.md).  
  
## Fehler bei Status der Benachrichtigung  
 Fehlgeschlagene Ihr VSPackage benachrichtigen die Umgebung eine Zustandsänderung Befehl kann die Benutzeroberfläche in einem inkonsistenten Zustand platzieren. Denken Sie daran, dass die Menübefehle im Menü oder Kontext auf einer Symbolleiste vom Benutzer platziert werden können. Daher ist Aktualisierung der Benutzeroberfläche nur, wenn ein Menü oder im Kontextmenü öffnet nicht ausreichend.  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementierung](../../extensibility/internals/command-implementation.md)