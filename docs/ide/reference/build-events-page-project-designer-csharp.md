---
title: "Seite &quot;Buildereignisse&quot;, Projekt-Designer (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "Buildereignisse"
  - "Projekt-Designer, Seite „Buildereignisse“"
  - "Präbuildereignisse"
  - "Postbuildereignisse"
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Seite &quot;Buildereignisse&quot;, Projekt-Designer (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Seite **Buildereignisse** des **Projekt\-Designers**, um Anweisungen für Buildkonfigurationen festzulegen.  Sie können auch die Bedingungen angeben, unter denen Postbuildereignisse ausgeführt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Angeben von Buildereignissen \(C\#\)](../../ide/how-to-specify-build-events-csharp.md) und unter [Gewusst wie: Festlegen von Buildereignissen \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
## UIElement-Liste  
 **Konfiguration**  
 Dieses Steuerelement ist auf dieser Seite nicht bearbeitbar.  Eine Beschreibung dieses Steuerelements finden Sie unter [Seite "Erstellen", Projekt\-Designer \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plattform**  
 Dieses Steuerelement ist auf dieser Seite nicht bearbeitbar.  Eine Beschreibung dieses Steuerelements finden Sie unter [Seite "Erstellen", Projekt\-Designer \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Befehlszeile für Präbuildereignis**  
 Gibt einen oder mehrere Befehle an, die vor dem Buildvorgang ausgeführt werden sollen.  Zur Eingabe längerer Befehle klicken Sie auf **Präbuild bearbeiten**, um [Dialogfeld "Befehlszeile für Präbuildereignis"\/"Befehlszeile für Postbuildereignis"](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) anzuzeigen.  
  
> [!NOTE]
>  Präbuildereignisse werden nicht ausgeführt, wenn das Projekt aktuell ist und kein Build ausgelöst wird.  
  
 **Befehlszeile für Postbuildereignis**  
 Gibt einen oder mehrere Befehle an, die nach dem Buildvorgang ausgeführt werden sollen.  Zur Eingabe längerer Befehle klicken Sie auf **Postbuild bearbeiten**, um **Präbuildereignis\/Dialogfeld "Befehlszeile für Postbuildereignis"** anzuzeigen.  
  
> [!NOTE]
>  Fügen Sie vor allen Postbuildbefehlen, die BAT\-Dateien ausführen, eine `call`\-Anweisung hinzu.  Beispielsweise `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Soll das Postbuildereignis ausgeführt werden?**  
 Legt die in der folgenden Tabelle aufgeführten Bedingungen für das auszuführende Postbuildereignis fest.  
  
|Option|Ergebnis|  
|------------|--------------|  
|**Immer**|Das Postbuildereignis wird unabhängig davon ausgeführt, ob der Buildvorgang erfolgreich war oder nicht.|  
|**Bei erfolgreichem Erstellen**|Das Postbuildereignis wird ausgeführt, wenn der Buildvorgang erfolgreich war.  Folglich wird das Ereignis auch für ein aktuelles Projekt ausgeführt, sofern das Erstellen erfolgreich war.|  
|**Wenn der Build die Projektausgabe aktualisiert**|Das Postbuildereignis wird nur ausgeführt, wenn sich die Compilerausgabedatei \(.exe oder .dll\) von der vorherigen Compilerausgabedatei unterscheidet.  Folglich wird kein Postbuildereignis ausgeführt, wenn ein Projekt aktuell ist.|  
  
## Siehe auch  
 [Gewusst wie: Festlegen von Buildereignissen \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Gewusst wie: Angeben von Buildereignissen \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)   
 [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)   
 [Anwendungen in Visual Studio erstellen](../../ide/compiling-and-building-in-visual-studio.md)