---
title: "Kennwortschutz f&#252;r Office-Dokumente"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
  - "Kennwörter [Office-Entwicklung in Visual Studio], Dokumentschutz"
  - "Berechtigungen [Office-Entwicklung in Visual Studio]"
  - "Arbeitsmappen [Office-Entwicklung in Visual Studio], Eingeschränkte Berechtigungen"
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Kennwortschutz f&#252;r Office-Dokumente
  Es ist möglich, ein Kennwort für Ihre Microsoft Office Word\-Dokumente und Microsoft Office Excel\-Arbeitsmappen festzulegen, sodass sie von einem Benutzer, der das Kennwort nicht kennt, nicht geöffnet werden können.  Diese Option heißt **Kennwort beim Öffnen**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können Projekte auf Dokumentebene mithilfe vorhandener Dokumente und Arbeitsmappen erstellen, bei denen **Kennwort beim Öffnen** aktiviert ist.  Das Verhalten in Visual Studio unterscheidet sich bei Word\- und Excel\-Dokumenten, bei denen **Kennwort beim Öffnen** aktiviert ist.  
  
 Informationen zum Aktivieren von **Kennwort beim Öffnen** finden Sie in der Hilfe in Word oder Excel.  
  
## Verhalten von Excel und Word  
 Bei jedem Öffnen einer Excel\-Arbeitsmappe in Visual Studio, bei der **Kennwort beim Öffnen** aktiviert ist, werden Sie von Excel zur Eingabe des Kennworts aufgefordert.  Beim Erstellen der Projektmappe werden Sie erneut zur Eingabe des Kennworts aufgefordert, da das Dokument während des Erstellens geöffnet wird.  
  
 Beim ersten Öffnen eines Word\-Dokuments in Visual Studio, bei dem **Kennwort beim Öffnen** aktiviert ist, werden Sie von Word zur Eingabe des Kennworts aufgefordert.  Nachdem Sie das Kennwort eingegeben haben, wird **Kennwort beim Öffnen** aus dem Dokument entfernt. Beim Öffnen des Dokuments ist daher kein Kennwort mehr erforderlich.  Wenn zum Öffnen des Dokuments in Ihrer Projektmappe ein Kennwort erforderlich sein soll, müssen Sie **Kennwort beim Öffnen** nach dem endgültigen Build und vor Bereitstellung der Projektmappe aktivieren.  
  
## Siehe auch  
 [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Übersicht über Information Rights Management und Erweiterungen durch verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Gewusst wie: Zulassen der Ausführung von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)  
  
  