---
title: "Gewusst wie: Einrichten von Konfigurationsinformationen f&#252;r eine Office-Projektmappe"
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
  - "Konfigurationsdateien [Office-Entwicklung in Visual Studio]"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Konfigurationsdateien"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Gewusst wie: Einrichten von Konfigurationsinformationen f&#252;r eine Office-Projektmappe
  Einstellungen, die für Ihre Office\-Projektmappe spezifisch sind, können Sie mithilfe von Konfigurationsdateien konfigurieren.  Sie können zum Beispiel Einstellungen für Remoteobjekte, das Debuggen und die Ablaufverfolgung sowie eine Assemblybindungsrichtlinie angeben.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### So fügen Sie Ihrem Office\-Projekt eine Konfigurationsdatei hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Klicken Sie im Bereich **Kategorien** auf **Allgemein**.  
  
3.  Wählen Sie im Bereich **Vorlagen** die Option **Anwendungskonfigurationsdatei** aus.  
  
4.  Geben Sie im Feld **Name** den Namen der Assembly mit der Erweiterung .config ein.  Die Konfigurationsdatei einer Excel\-Projektassembly mit dem Namen ExcelWorkbook1.dll würde beispielsweise den Namen ExcelWorkbook1.dll.config erhalten.  
  
5.  Klicken Sie auf **Hinzufügen**.  
  
6.  Erstellen Sie die Konfigurationsdatei gemäß dem Schema für Anwendungskonfigurationsdateien.  Weitere Informationen finden Sie unter [Konfigurationsdateischema für .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38).  
  
 Bei der Verwendung von Konfigurationsdateien in Office\-Projekten sind keine besonderen Überlegungen erforderlich.  
  
## Siehe auch  
 [Konfigurationsdateischema für .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  