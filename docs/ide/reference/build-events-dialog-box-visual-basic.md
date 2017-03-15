---
title: "Dialogfeld &quot;Buildereignisse&quot; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "Buildereignisse"
  - "Buildereignisse, angeben"
  - "Präbuildereignisse"
  - "Buildereignisse (Dialogfeld)"
  - "Postbuildereignisse"
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Dialogfeld &quot;Buildereignisse&quot; (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Dialogfeld **Buildereignisse** können Sie Buildkonfigurationsanweisungen festlegen.  Sie können auch die Bedingungen angeben, unter denen jedes Präbuild\- oder Postbuildereignis ausgeführt wird.  Weitere Informationen finden Sie unter [Gewusst wie: Festlegen von Buildereignissen \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
 **Befehlszeile für Präbuildereignis**  
 Gibt einen oder mehrere Befehle an, die vor dem Buildvorgang ausgeführt werden sollen.  Zur Eingabe längerer Befehle klicken Sie auf **Präbuild bearbeiten**, um [Dialogfeld "Befehlszeile für Präbuildereignis"\/"Befehlszeile für Postbuildereignis"](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) anzuzeigen.  
  
> [!NOTE]
>  Präbuildereignisse werden nicht ausgeführt, wenn das Projekt aktuell ist und kein Build ausgelöst wird.  
  
 **Befehlszeile für Postbuildereignis**  
 Gibt einen oder mehrere Befehle an, die nach dem Buildvorgang ausgeführt werden sollen.  Zur Eingabe längerer Befehle klicken Sie auf **Postbuild bearbeiten**, um das Dialogfeld **Befehlszeile für Präbuildereignis\/Postbuildereignis** anzuzeigen.  
  
> [!NOTE]
>  Fügen Sie vor allen Postbuildbefehlen, die BAT\-Dateien ausführen, eine `call`\-Anweisung hinzu.  Beispielsweise `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Soll das Postbuildereignis ausgeführt werden?**  
 Legt die in der folgenden Tabelle aufgeführten Bedingungen für das auszuführende Postbuildereignis fest.  
  
|Option|Ergebnis|  
|------------|--------------|  
|**Immer**|Das Postbuildereignis wird unabhängig davon ausgeführt, ob der Buildvorgang erfolgreich war oder nicht.|  
|**Bei erfolgreichem Erstellen**|Das Postbuildereignis wird ausgeführt, wenn der Buildvorgang erfolgreich war.  Das Ereignis wird auch für ein aktuelles Projekt ausgeführt, sofern der Buildvorgang erfolgreich war.  Dies ist die Standardeinstellung.|  
|**Wenn der Build die Projektausgabe aktualisiert**|Das Postbuildereignis wird nur ausgeführt, wenn sich die Compilerausgabedatei \(.exe oder .dll\) von der vorherigen Compilerausgabedatei unterscheidet.  Es wird kein Postbuildereignis ausgeführt, wenn ein Projekt auf dem neuesten Stand ist.|  
  
## Siehe auch  
 [Seite "Kompilieren", Projekt\-Designer \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Gewusst wie: Festlegen von Buildereignissen \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Dialogfeld "Befehlszeile für Präbuildereignis"\/"Befehlszeile für Postbuildereignis"](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)