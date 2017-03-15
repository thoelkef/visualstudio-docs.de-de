---
title: "Anzeigen von Dateien mit &#214;ffnen mit (Befehl) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Unterstützung von Befehl Öffnen mit-Projekttypen"
  - "Öffnen mit (Befehl)"
  - "Persistenz, Unterstützung von Befehl Öffnen mit"
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Anzeigen von Dateien mit &#214;ffnen mit (Befehl)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Projekt kann damit die IDE aufgefordert, um das **Öffnen mit** Dialogfeld anzuzeigen.  Diese Anforderung fordert den Benutzer auf, eine Datei zu öffnen, die eine Reihe von standardmäßigen editoren verfügt.  Die folgenden Schritte beschreiben diesen Prozess.  
  
1.  Das Projekt wird das <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>an und gibt einen Wert OSE\_UseOpenWithDialog für den `OSEOpenDocEditor`\-Parameter an.  
  
2.  Auf Grundlage der Dateinamenerweiterung des Dokuments bestimmt die IDE, der die Editoren, die in der Registrierung aufgeführten das angegebene Dokument öffnen und zeigt diese Informationen im **Öffnen mit** Dialogfeld an.  
  
    > [!NOTE]
    >  Projekte, die einen systeminternen im Editor Dialog **Öffnen mit** enthalten sein muss, müssen eine Editor factory für jeden solchen Editor registriert werden.  Systeminterne Editoren funktionieren nur mit einem bestimmten Projekttyp, das in der Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>\-Methode erzwungen wird.  Die IDE bietet eine integrierte Editor factory für den Kern text\-editor und den binären Editor.  Die IDE erstellt außerdem eine Instanz einer Editor factorys im Namen aller registrierten Windows\-Datei Zuordnung.  Ein Beispiel für eine solche Datei ist Microsoft Word.  
  
3.  Sobald der Benutzer ein Element auswählt **Öffnen mit** im Dialogfeld öffnet die IDE anschließend das Dokument durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>\-Methode.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen Sie die Standard\-Editoren](../../extensibility/how-to-open-standard-editors.md).  
  
## Siehe auch  
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Anzeigen von Dateien mit dem Befehl Datei öffnen](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Gewusst wie: Öffnen Sie die Standard\-Editoren](../../extensibility/how-to-open-standard-editors.md)