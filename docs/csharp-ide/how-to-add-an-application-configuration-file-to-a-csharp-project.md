---
title: "How to: Add an Application Configuration File to a C# Project | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "app.config files, adding to C# projects"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Add an Application Configuration File to a C# Project
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit einer Anwendungskonfigurationsdatei \(app.config\) zu einem C\#\-Projekt hinzufügen, können Sie anpassen, wie Assemblydateien von der Common Language Runtime gesucht und geladen wird.  Weitere Informationen zu Anwendungskonfigurationsdateien finden Sie unter [So sucht Common Language Runtime nach Assemblys](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
> [!NOTE]
>  Der Windows Store nicht unterstützt <xref:System.Configuration>.  Daher enthalten Speicher\-Apps keine app.config\-Vorlage.  
  
 Wenn Sie das Projekt erstellen, kopiert die Entwicklungsumgebung automatisch die Datei app.config, ändert den Dateinamen der Kopie, um die ausführbare Datei übereinstimmt und verschieben dann die Kopie in das Verzeichnis bin.  
  
### So fügen Sie dem C\#\-Projekt eine Anwendungskonfigurationsdatei hinzu  
  
1.  Klicken Sie auf der Menüleiste wählen Sie **Projekt**, **Neues Element hinzufügen** aus.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  Erweitern Sie **Installiert**, erweitern Sie **Visual C\#\-Elemente** und dann die Vorlage aus. **Anwendungskonfigurationsdatei**  
  
3.  Im **Name** Textfeld geben Sie einen Namen ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Eine Datei, die app.config\-Datei vorhanden ist, wird dem Projekt hinzugefügt.  
  
## Siehe auch  
 [Verwalten von Anwendungseinstellungen \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [Konfigurationsdateischema](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [Konfigurieren von Apps](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/de-de/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)