---
title: "Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten | Microsoft Docs"
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
  - "Ereignishandler [Office-Entwicklung in Visual Studio]"
  - "Ereignisse [Office-Entwicklung in Visual Studio]"
  - "Visual Basic [Office-Entwicklung in Visual Studio], Ereignishandler"
  - "Visual C# [Office-Entwicklung in Visual Studio], Ereignishandler"
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten
  Ereignishandler können in Visual Basic und C\# auf unterschiedliche Arten erstellt werden.  In der Entwurfsansicht können Sie die Standardereignishandler für Steuerelemente erstellen, indem Sie auf das Steuerelement doppelklicken. Sie können auch den Ereignisbereich im **Eigenschaftenfenster** verwenden, um Handler für jedes beliebige Ereignis für das Steuerelement zu erstellen.  Wenn Sie sich jedoch in der Codeansicht befinden, möchten Sie zum Erstellen eines Ereignishandlers möglicherweise nicht in die Entwurfsansicht wechseln.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### So erstellen Sie einen Ereignishandler in Visual Basic  
  
1.  Wählen Sie oben im Code\-Editor aus der Dropdownliste **Klassenname** das Objekt aus, für das Sie einen Ereignishandler erstellen möchten.  
  
    > [!NOTE]  
    >  Wenn Sie Ereignishandler für `ThisDocument` bzw. `ThisWorkbook` erstellen möchten, müssen Sie in der Dropdownliste **Klassenname** den Eintrag **\(ThisDocument\-Ereignisse\)** bzw. **\(ThisWorkbook\-Ereignisse\)** auswählen.  
  
2.  Wählen Sie oben im Code\-Editor aus der Dropdownliste **Methodenname** das Ereignis aus.  
  
     Visual Studio erstellt den Ereignishandler und bewegt die Einfügemarke zum neu erstellten Ereignishandler.  Wenn der Ereignishandler bereits vorhanden ist, wird die Einfügemarke zum vorhandenen Ereignishandler bewegt.  
  
### So erstellen Sie einen Ereignishandler in C\#  
  
1.  Erstellen Sie den Ereignisdelegaten im **Startup**\-Ereignis der Klasse, indem Sie den qualifizierten Ereignisnamen gefolgt von einem Leerzeichen eingeben. Geben Sie anschließend "\+\=" ohne darauf folgendes Leerzeichen ein.  Beispiel:  
  
     `this.<object name>.<event name> +=`  
  
2.  Drücken Sie am Ende der Codezeile zweimal die TAB\-TASTE.  
  
     Visual Studio vervollständigt automatisch die Codezeile, erstellt den Ereignishandler und bewegt die Einfügemarke zum neu erstellten Ereignishandler.  
  
## Siehe auch  
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)  
  
  