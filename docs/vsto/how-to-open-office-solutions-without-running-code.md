---
title: "Gewusst wie: &#214;ffnen von Office-Projektmappen ohne die Ausf&#252;hrung von Code"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Assemblys [Office-Entwicklung in Visual Studio], Umgehen"
  - "Umgehen von Assemblys"
  - "Dokumente [Office-Entwicklung in Visual Studio], Öffnen ohne Ausführen von Code"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Öffnen ohne Ausführen von Code"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Öffnen"
  - "Öffnen von Office-Projektmappen"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Öffnen"
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: &#214;ffnen von Office-Projektmappen ohne die Ausf&#252;hrung von Code
  Eine Microsoft Office\-Lösung mit Erweiterungen durch verwalteten Code wird auch dann ausgeführt, wenn in der Office\-Anwendung des Endbenutzers die Sicherheitseinstellung auf Hoch festgelegt ist.  Die Ursache besteht darin, dass die Sicherheit des .NET\-Assemblycodes von Microsoft .NET Framework und nicht von Microsoft Office verwaltet wird.  
  
 Manchmal möchten Sie jedoch möglicherweise ein Dokument öffnen, ohne den Code auszuführen.  So kann z. B. Code, der beim Öffnen des Dokuments ausgeführt wird, unter Umständen den Inhalt ändern. Sie möchten das Aussehen des Dokuments jedoch aktualisieren, bevor es vom Code geändert wird.  Oder Sie möchten möglicherweise das Dokument mit bestimmten Informationen darin an jemanden senden, und Sie möchten nicht, dass der Code ausgeführt wird und möglicherweise den Inhalt ändert.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Es gibt mehrere Möglichkeiten, wie Sie ein Dokument oder eine Arbeitsmappe mit Erweiterungen durch verwalteten Code öffnen können, ohne den Assemblycode auszuführen.  
  
### So umgehen Sie die Assembly mit der UMSCHALTTASTE  
  
-   Öffnen Sie Dokumente und Arbeitsmappen im Menü **Datei**, und halten Sie dabei die UMSCHALTTASTE gedrückt, um zu verhindern, dass Word und Excel beim Öffnen des Dokuments Initialisierungsereignisse auslösen.  
  
    > [!NOTE]  
    >  Wenn Sie ein Dokument oder eine Arbeitsmappe im Aufgabenbereich **Erste Schritte** öffnen, wird der Code durch das Drücken der UMSCHALTTASTE nicht umgangen.  Ebenso wenig wird damit verhindert, dass Ereignisse nach dem Öffnen des Dokuments ausgelöst werden.  
  
     Diese Methode ist nützlich, wenn Sie ein Dokument öffnen möchten, um Änderungen vorzunehmen, ohne dass zunächst der Code ausgeführt wird und das Dokument ändert.  
  
### So umgehen Sie eine Assembly, indem Sie sie umbenennen oder entfernen  
  
-   Wenn Sie über die erforderlichen Berechtigungen für den Computer verfügen, auf dem sich die Assembly befindet, können Sie die Assembly umbenennen oder entfernen, sodass sie nicht durch das Dokument oder die Arbeitsmappe gefunden werden kann.  Das führt dazu, dass bei jedem Öffnen des Office\-Dokuments ein Fehler ausgelöst wird.  
  
     Wenn die Projektmappe von mehreren Personen verwendet wird, verhindert diese Methode, dass die Projektmappe für alle ausgeführt wird.  Das kann nützlich sein, wenn im Code oder auf einem Server, auf den verwiesen wird, ein Problem gefunden wird und kein Benutzer diesen Code weiter ausführen sollte.  
  
## Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  