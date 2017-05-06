---
title: "Erstellen von wiederverwendbaren Steuerelementen f&#252;r Webparts oder Anwendungsseiten"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Benutzersteuerelemente"
  - "Benutzersteuerelemente [SharePoint-Entwicklung in Visual Studio], Erstellen"
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Erstellen von wiederverwendbaren Steuerelementen f&#252;r Webparts oder Anwendungsseiten
  In Visual Studio können Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden.  Diese Steuerelemente werden Benutzersteuerelemente genannt.  Weitere Informationen über Benutzersteuerelemente finden Sie unter [ASP.NET User Controls](http://msdn.microsoft.com/library/5e601b3d-bb16-4dbe-9e35-7e92a34565ca).  
  
## Erstellen eines Benutzersteuerelements  
 Um ein Benutzersteuerelement zu erstellen, fügen Sie einem **leeren SharePoint\-Projekt** ein **Benutzersteuerelement** hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Wenn Sie ein Element **Benutzersteuerelement** hinzufügen, erstellt Visual Studio einen Ordner im Projekt und fügt diesem Ordner dann mehrere Dateien hinzu.  In der folgenden Tabelle werden die einzelnen Dateien beschrieben.  
  
|Datei|**Beschreibung**|  
|-----------|----------------------|  
|Benutzersteuerelementdatei|Definiert das Benutzersteuerelement.  Entwerfen Sie das Benutzersteuerelement, indem Sie dieser Datei Steuerelemente und Markup hinzufügen.|  
|Codedatei|Enthält Code hinter dem Benutzersteuerelement.  Fügen Sie dieser Datei Code hinzu, um Ereignisse zu behandeln.|  
|Designercodedatei|Enthält vom Designer generierten Code und sollte nicht direkt bearbeitet werden.|  
  
## Entwerfen des Benutzersteuerelements  
 Entwerfen Sie das Benutzersteuerelement mit dem Visual Web Developer\-Designer in Visual Studio.  Dieser Designer wird angezeigt, wenn Sie die Benutzersteuerelementdatei im Projekt öffnen und die Registerkarte **Entwurf** auswählen.  Weitere Informationen zur Verwendung dieses Designers finden Sie unter [Visual Studio Web Development Content Map](http://msdn.microsoft.com/de-de/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
## Verwenden des Benutzersteuerelements  
 Benutzersteuerelemente werden erst in SharePoint angezeigt, wenn Sie sie in eine Anwendungsseite oder ein Webpart einschließen.  
  
 Um ein Benutzersteuerelement in eine Anwendungsseite einzuschließen, fügen Sie der Anwendungsseite eine [@ Register](http://msdn.microsoft.com/de-de/66f34922-be41-4e36-9dc8-1774d85311d1)\-Direktive hinzu, und deklarieren Sie dann das Benutzersteuerelement innerhalb eines oder mehrerer Inhaltsplatzhalter auf der Seite.  Ein Beispiel zum Ausführen dieser Aufgabe in einer Standard\-ASP.NET\-Webseite finden Sie unter [How to: Include a User Control in an ASP.NET Web Page](http://msdn.microsoft.com/library/7c3bfd74-846c-4b88-b1ef-45d75860af92).  
  
 Um ein Benutzersteuerelement in ein Webpart einzuschließen, fügen Sie der <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>\-Auflistung des Webparts das Benutzersteuerelement in der Webpartcodedatei hinzu.  Im folgenden Beispiel wird der <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>\-Auflistung eines Webparts ein Benutzersteuerelement hinzugefügt.  
  
 [!code-csharp[SP_VisualWebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1.cs#5)]
 [!code-vb[SP_VisualWebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1.vb#5)]  
  
## Debuggen eines Benutzersteuerelements  
 Um ein Benutzersteuerelement zu debuggen, stellen Sie sicher, dass das Benutzersteuerelement im SharePoint\-Projekt in einer Anwendungsseite oder einem Webpart enthalten ist.  Sie können dann Code im Benutzersteuerelement auf dieselbe Weise debuggen, wie Sie Code in einem Visual Studio\-Projekt debuggen.  
  
 Wenn Sie den Visual Studio\-Debugger starten, wird von Visual Studio die SharePoint\-Website geöffnet.  
  
 Öffnen Sie in SharePoint die Anwendungsseite, die das Benutzersteuerelement enthält.  Wenn das Benutzersteuerelement in einem Webpart enthalten ist, fügen Sie das Webpart zu einer Webpartseite in SharePoint hinzu.  
  
 Weitere Informationen zum Debuggen von SharePoint\-Projekten finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Gewusst wie: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Zeigt, wie Sie benutzerdefinierte, wiederverwendbare Steuerelemente erstellen, die von Anwendungsseiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden.|  
|[Arbeiten mit Visual Web Developer](http://msdn.microsoft.com/de-de/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Beschreibt die Verwendung des Designers, der angezeigt wird, wenn Sie im Projekt eine Webseite öffnen.|  
  
  