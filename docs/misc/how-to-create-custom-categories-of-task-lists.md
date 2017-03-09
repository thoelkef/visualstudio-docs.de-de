---
title: "Gewusst wie: Erstellen benutzerdefinierter Kategorien von Aufgabenlisten | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aufgabenliste, benutzerdefinierte Kategorien"
ms.assetid: 5e4ac1b1-9afb-46c5-9dcc-6cab9c5ceee8
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Gewusst wie: Erstellen benutzerdefinierter Kategorien von Aufgabenlisten
Benutzerdefinierte Kategorien von Aufgaben stellen Steuerelement zum Aufgaben im **Aufgabenliste** Fenster angezeigt werden.  
  
 Implementieren Sie eine benutzerdefinierte Kategorie Aufgaben aus folgenden Gründen:  
  
-   Sie steuern möchten, wo die Kategorien sortiert \(\) in der Liste der Kategorien angezeigt werden.  
  
-   Sie haben verschiedene Unterkategorien von Aufgaben, die Sie in eine andere Aufgaben ohne Kategorie sortiert werden soll sortierend zwischen ihnen.  
  
-   Sie möchten eine benutzerdefinierte Ansicht erstellen, in der nur die Aufgaben angezeigt werden.  
  
    > [!NOTE]
    >  Sie können die Effekte erzielen, die den benutzerdefinierten Kategorien ähneln, ohne eine benutzerdefinierte Kategorie tatsächlich zu implementieren.  Sie können z. B. eine Bitmap für eine Kategorie und Unterkategorie anzeigen, indem Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2.ImageList%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.ImageListIndex%2A>implementieren.  Das Aufgaben und dann die Liste stellt für jede Aufgabe erstellt einen Index in der Liste bereit.  
  
 Um eine benutzerdefinierte Kategorie in **Aufgabenliste**zu erstellen, registrieren Sie es mit **Aufgabenliste** indem Sie das folgende Verfahren verwenden.  
  
### So fügen Sie eine benutzerdefinierte Kategorie der Aufgabenliste Registrieren  
  
-   Aufrufs <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterCustomCategory%2A> , um eine benutzerdefinierte Kategorie mit der Aufgabenliste zu registrieren.  
  
     Jede benutzerdefinierte Kategorie muss über ein eigenes GUID verfügen, das im `guidCat`\-Parameter angegeben wird.  Im `dwSortOrder`\-Parameter geben Sie den Speicherort bereit, in dem Sie möchten, dass diese Kategorie sortiert \(wenn die Liste nach Kategorien sortiert ist\).  Diese Methode gibt die tatsächliche Sortierung der der benutzerdefinierten Kategorie innerhalb der größeren Liste von Kategorien zurück.  
  
     Sortierungen für die integrierten Funktionen Kategorien, die in der <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKCATEGORY>\-Enumeration definiert sind, sind in der folgenden Tabelle.  
  
    |Kategorie|Wert|Beschreibung|  
    |---------------|----------|------------------|  
    |CAT\_ALL|1|Es wird keine wirkliche Kategorie.  Wird verwendet, um eine Ansicht der Aufgabenliste können alle Aufgaben in **Aufgabenliste**anzuzeigen.|  
    |CAT\_BUILDCOMPILE|10|Buildfehler, Warnungen und ggf. Bereitstellungsfehler.|  
    |CAT\_COMMENTS|20|Generieren von Kommentaren spezielle Aufgaben, z. B. „TODO“, „RÜCKGÄNGIG GEMACHT KERBE“ oder „.“|  
    |CAT\_CODESENSE|30|Quellcode Sie als Fehler generiert.|  
    |CAT\_SHORTCUTS|40|Tastenkombinationen zum Code.|  
    |CAT\_USER|50|Vom Benutzer eingegebene Aufgaben.|  
    |CAT\_MISC|60|Verschiedene Aufgaben, die **Aufgabenliste**VSPackages hinzugefügt werden soll.|  
    |CAT\_HTML|70|Aufgaben, die Entwicklung von Webseiten.|  
  
     Wenn Sie beispielsweise eine Kategorie zwischen CAT\_CODESENSE und CAT\_SHORTCUTS einzuschließen, übergäben ggf. einen Wert von 31 für die Sortierung.  Da ein Wert von 31 bereits von einem anderen Kategorien für benutzerdefinierte Aufgaben nach Hersteller verwendet wird, weist **Aufgabenliste** Sie die Kategorie Aufgaben für den folgenden leeren Slot zugewiesen.  Dieser Wert wird wieder im `pCat`\-Parameter übergeben.  
  
### So fügen Sie eine benutzerdefinierte Kategorie der Aufgabenliste Registrierung aufheben  
  
-   Aufrufs <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.UnregisterCustomCategory%2A> , um die benutzerdefinierten Kategorie Registrierung aufgehoben.  
  
## Siehe auch  
 [Erstellen von benutzerdefinierten Aufgabenlistenansichten](../misc/creating-custom-task-list-views.md)