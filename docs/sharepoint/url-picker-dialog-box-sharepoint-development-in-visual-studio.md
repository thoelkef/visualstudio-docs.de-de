---
title: "URL-Auswahldialogfeld (SharePoint-Entwicklung in Visual Studio)"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.VWD.URLPicker"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Designer"
  - "SharePoint-Entwicklung in Visual Studio, URL-Auswahl"
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# URL-Auswahldialogfeld (SharePoint-Entwicklung in Visual Studio)
  Im URL\-Auswahldialogfeld können Sie Dateien wie Masterseitendateien oder Bilddateien auswählen, die im Projekt oder auf dem lokalen Server, auf dem SharePoint ausgeführt wird.  
  
 Dieses Dialogfeld wird angezeigt, wenn Sie die Option verfügen, eine Datei auszuwählen, um eine Eigenschaft festzulegen.  Sie können dieses Dialogfeld, indem Sie die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](~/docs/sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")\) neben den jeweiligen Eigenschaften im Fenster **Eigenschaften** öffnen auswählen.  Die Schaltfläche mit den Auslassungspunkten wird auch als IntelliSense\-Auswahl angezeigt, wenn Sie bestimmten Attributen in der **Quellansicht** des Designers Werte zuweisen.  
  
## UIElement-Liste  
 **Projektordner**  
 Zeigt eine Liste der Ordner an, die im Projekt oder auf dem lokalen Server definiert sind, auf dem SharePoint ausgeführt wird.  Klicken Sie auf die Erweiterungsschaltfläche, um die Unterordner anzuzeigen.  
  
 Erweitern Sie den Knoten **Projekt**, um Dateien im Projekt.  Damit Dateien im Projekt im Dialogfeld ausgewählt werden können, müssen sie die folgenden Kriterien erfüllen:  
  
-   Die Datei muss in einem zugeordneten Ordner enthalten sein.  
  
-   Die Datei muss dem Projektmappenpaket hinzugefügt worden sein.  
  
-   Die Datei wurde in keinem anderen Projekt gefunden.  
  
 Wenn Sie auf Dateien verweisen möchten, die diese Kriterien nicht erfüllen, müssen Sie den Pfad der Datei manuell eingeben.  
  
 Erweitern Sie den Knoten **Server**, um Dateien auszuwählen, die auf dem lokalen Server, auf dem SharePoint ausgeführt wird.  Damit diese Dateien im Dialogfeld ausgewählt werden können, müssen sie die folgenden Kriterien erfüllen:  
  
-   Die Datei muss sich in einem der folgenden zugeordneten Ordner befinden: **Images**, **Layouts** oder **ControlTemplates**.  
  
-   Die Datei wurde in der SharePoint\-Inhaltsdatenbank nicht gefunden.  
  
 Wenn Sie auf Dateien verweisen möchten, die diese Kriterien nicht erfüllen, müssen Sie den Pfad der Datei manuell eingeben.  
  
 **Ordnerinhalt**  
 Zeigt eine Liste mit den Dateien des ausgewählten Ordners an.  Wählen Sie eine Datei aus, und wählen Sie die Schaltfläche **OK**, um das Dialogfeld zu schließen und die Auswahl an den Prozess zu schicken, der das Dialogfeld aufgerufen hat.  
  
 **Dateityp**  
 Ermöglicht es Ihnen, aus einer Liste von Dateien auszuwählen, die für die Aufgabe geeignet sind, die Sie ausführen.  
  
## Siehe auch  
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/de-de/9c31f93b-c8fb-4599-9b14-6194ec8c7539)  
  
  