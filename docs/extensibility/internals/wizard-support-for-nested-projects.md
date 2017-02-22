---
title: "Unterst&#252;tzung f&#252;r geschachtelte Projekte-Assistenten | Microsoft Docs"
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
  - "Mit dem Assistenten hinzufügen"
  - "geschachtelte Projekte, Unterstützung für Assistenten"
  - "Assistent für neue"
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Unterst&#252;tzung f&#252;r geschachtelte Projekte-Assistenten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die IDE führt zwei Assistenten aus, die das übergeordnete Projekt für geschachtelte Projekte implementiert werden kann: **Element hinzufügen** und der Assistent **Neues Projekt** der Assistent.  
  
 Wenn ein Benutzer den **Neues Projekt** Assistenten startet, indem er **Projekt hinzufügen** ausgewählt und im Menü Datei auf **Neues Projekt** klickt oder klicken Sie im Projektmappen\-Explorer auf **Hinzufügen** ausgewählt und **Neues Projekt** mit der rechten Maustaste klickt, führt die IDE den **AddProject** Befehl aus und Elemente Implementierung des Projekts des Befehls **AddProject** entweder Vorlagenprojekt gibt eine Datei oder eine Datei des Assistenten \(.vsz\) zurück, die einen Satz Kontextparameter verfügt.  
  
 Entsprechend gibt eine übergeordnete Implementierung des Projekts von **AddItem** Assistenten eine VSZ\-Datei zurück, die einen anderen Satz Kontextparameter verfügt.  
  
 Weitere Informationen zum Assistenten finden Sie unter [Assistenten \(. VSZ\)\-Datei](../../extensibility/internals/wizard-dot-vsz-file.md), [Kontextparameter](../../extensibility/internals/context-parameters.md) und [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Die Schachtelung von Projekten](../../extensibility/internals/nesting-projects.md)