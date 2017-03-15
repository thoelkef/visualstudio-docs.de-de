---
title: "Projekt-Kontext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK] Elemente öffnen"
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Projekt-Kontext
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn der Benutzer mit Projekten und Projektelementen hinzufügt oder eine Funktion, die IDE verwendet das Konzept des Projekts, um zu bestimmen, wie verschiedene Operationen ausgeführt werden sollen.  
  
 In der Regel sind die Dateien, die der Benutzer projektobjekte explizit erstellt, indem der **Neues Projekt** Befehl auswählt oder zur Verfügung stellt, indem er den **Projekt öffnen** Befehl für das **Datei** Menü ausgewählt wird.  In diesen Fällen werden die Dateien erstellt und geöffnet im Kontext eines Projekts und des Projekttyps definiert den Kontext für die Bearbeitung des Dokuments.  
  
 Einige Projekte stellen einen sehr umfangreichen Kontext.  Zum Beispiel verwaltet das Projekt einen PROJECT\-bewerteten, Namespace\- oder programmgesteuerter durch Projekte festgelegten eine Datenbankverbindung für die Datenbindung.  Der Benutzer kann häufig geöffnete Dateien oder Datenbankverbindungen direkte indem er ein bestimmtes Projektobjekt im Projektmappen\-Explorer das Projektelement Projektmappen\-Explorer angezeigt.  
  
 Um anderen Zeiten Kontext eines Elements wird das Projekt nicht explizit angegeben ist.  Beispielsweise ist der Kontext eines Elements nicht verfügbar, wenn der Benutzer eine Datei geöffnet, indem er den **Vorhandene Datei öffnen** Befehl im Menü **Datei** auswählt, wenn der Debugger an eine Datei oder betreibt **In Dateien suchen** wenn der Benutzer auf den Befehl im **Suchen und Ersetzen** Dialogfeld klickt.  Um diese Situationen gerecht zu werden, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> an, um den Prozess des Suchens des Projekts besten erreichen ein Dokument zu öffnen.  
  
## Siehe auch  
 [Projektpriorität](../../extensibility/internals/project-priority.md)   
 [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)