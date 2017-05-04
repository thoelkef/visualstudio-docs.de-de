---
title: "Erstellen von Anwendungsseiten f&#252;r SharePoint | Microsoft Docs"
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
  - "Anwendungsseiten [SharePoint-Entwicklung in Visual Studio], Erstellen"
  - "Anwendungsseiten [SharePoint-Entwicklung in Visual Studio], Entwickeln"
  - "SharePoint-Entwicklung in Visual Studio, Anwendungsseiten"
  - "SharePoint-Entwicklung in Visual Studio, Inhaltsseiten"
  - "SharePoint-Entwicklung in Visual Studio, Webseiten"
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Erstellen von Anwendungsseiten f&#252;r SharePoint
  Eine *Anwendungsseite* ist eine ASP.NET\-Webseite, die für die Verwendung in einer SharePoint\-Website ausgelegt ist.  Anwendungsseiten sind ein spezialisierter Typ einer ASP.NET\-Seite.  Der primäre Unterschied zwischen einer Anwendungsseite und einer ASP.NET\-Standardseite besteht darin, dass eine Anwendungsseite Inhalt enthält, der mit einer SharePoint\-Masterseite zusammengeführt wird.  Eine Masterseite aktiviert Anwendungsseiten, die dieselbe Darstellung und dasselbe Verhalten wie andere Seiten auf einer Site aufweisen.  
  
 Visual Studio ermöglicht es Ihnen, Anwendungsseiten mit einem Designer zu entwerfen.  Der Designer zeigt einen Inhaltsbereich für jeden Inhaltsplatzhalter an, der in einer Masterseite definiert wird.  Sie können die Anwendungsseite entwerfen, indem Sie Steuerelemente in diese Inhaltsbereiche ziehen.  
  
## Anwendungsseiten  
 Anwendungsseiten werden von allen Websites auf dem Server gemeinsam genutzt, wohingegen eine Websiteseite spezifisch für eine Website ist.  Weitere Informationen. [SharePoint\-Seitentypen](http://go.microsoft.com/fwlink/?LinkID=211584)  
  
 Standardmäßig sind die meisten der Seiten, die angezeigt werden, wenn Sie eine SharePoint\-Website erstellen, Websiteseiten.  Eine Websiteseite kann einer SharePoint\-Seitenbibliothek hinzugefügt werden.  Benutzer können eine Websiteseite mit Tools wie dem SharePoint Designer anpassen.  Eine Websiteseite kann auch Funktionen hosten, z. B. dynamische Webparts und Webpartzonen.  
  
 Bei Anwendungsseiten ist dies nicht möglich.  Es ist jedoch empfehlenswert, eine Anwendungsseite zu erstellen, wenn die Seite benutzerdefinierten Code enthalten soll.  Obwohl Sie einer Websiteseite benutzerdefinierten Code hinzufügen können, wird die Ausführung des Codes beendet, wenn der Benutzer die Seite mit Tools wie dem SharePoint Designer anpasst.  
  
> [!NOTE]  
>  Visual Studio stellt keine Vorlagen bereit, die Sie beim Erstellen von Websiteseiten für eine SharePoint\-Website unterstützen.  Weitere Informationen finden Sie unter [SharePoint\-Seitentypen](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## Erstellen einer Anwendungsseite  
 Um eine Anwendungsseite zu erstellen, fügen Sie einem SharePoint\-Projekt ein Element **Anwendungsseite** hinzu.  Wenn Sie eine Anwendungsseite erstellen, fügt Visual Studio dem Projekt die folgenden Ordner hinzu:  
  
|Ordner|**Beschreibung**|  
|------------|----------------------|  
|Layouts|Entspricht dem virtuellen Verzeichnis \_layouts des SharePoint\-Dateisystems.|  
|Unterordner Layouts|Enthält die Dateien, aus denen die Anwendungsseite besteht.  Standardmäßig weist dieser Ordner denselben Namen auf wie das Projekt.  Sie können diesen Ordner jedoch jederzeit umbenennen.  Wenn Sie das Projekt ausführen, stellt Visual Studio diesen Ordner im virtuellen Verzeichnis \_layouts des SharePoint\-Dateisystems bereit.|  
  
 Visual Studio fügt dem Projekt die folgenden Dateien hinzu:  
  
|Datei|**Beschreibung**|  
|-----------|----------------------|  
|ASP.NET\-Seitendatei \(\*.aspx\)|Enthält XML\-Markup, das die Seite definiert.|  
|Codedatei für die Anwendungsseite|Enthält Code hinter der Anwendungsseite.  Fügen Sie dieser Datei Code hinzu, der Ereignisse behandelt.|  
|Codedatei des Anwendungsseiten\-Designers|Enthält Code, der vom Designer generiert wird.  Bearbeiten Sie diese Datei nicht direkt.|  
  
## Entwerfen und Debuggen einer Anwendungsseite  
 Entwerfen Sie den Inhalt einer Anwendungsseite mit dem Visual Web Developer\-Designer in Visual Studio.  Dieser Designer wird angezeigt, wenn Sie die Anwendungsseite im Projekt öffnen \(durch Doppelklicken darauf oder durch Öffnen des Kontextmenüs und dann **Öffnen** auswählen\).  Weitere Informationen dazu, wie Sie diesen Designer, finden Sie unter [Visual Studio Web Development Content Map](http://msdn.microsoft.com/de-de/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
> [!NOTE]  
>  Sie können die Seite nur in der Ansicht **Quelle** des Designers entwerfen.  Die **Entwurfsansicht** des Designers ist für Anwendungsseiten deaktiviert.  
  
 Sie können eine Anwendungsseite auf dieselbe Weise debuggen wie Sie andere SharePoint\-Projektelemente in Visual Studio debuggen.  Wenn Sie den Visual Studio\-Debugger starten, wird von Visual Studio die SharePoint\-Website geöffnet.  
  
 Um die Anwendungsseite anzuzeigen, müssen Sie manuell zur Position der Anwendungsseite navigieren \(beispielsweise: http:\/\/*Server\_Name*\/\_layouts\/*Project\_Name*\/ApplicationPage1.aspx\).  
  
 Weitere Informationen zum Debuggen von SharePoint\-Projekten finden Sie unter [Problembehandlung bei SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Auswählen einer Masterseite  
 Standardmäßig verweist ein Element **Anwendungsseite** auf die Masterseite der Site, mit der Sie das Projekt debuggen.  Diese Seite hat den Namen v4.master und ist auf der SharePoint\-Website im **Gestaltungsvorlagenseite** verfügbar.  
  
 Sie können explizit ändern, welche Gestaltungsvorlage von der Anwendungsseite verwendet wird, indem Sie das `MasterPageFile`\-Attribut des `Page`\-Elements der Anwendung festlegen. \(Beispiel: `MasterPageFile="~/_layouts/applicationv4.master"`\).  Sie müssen dieses Attribut sogar festlegen, wenn dynamische Masterseiten nicht auf dem SharePoint\-Server aktiviert sind.  Weitere Informationen zu Gestaltungsvorlagen in SharePoint, Sie finden. [Masterseiten](http://go.microsoft.com/fwlink/?LinkID=169281)  
  
## Siehe auch  
 [SharePoint Foundations\-Entwicklung detailliert](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Übersicht über ASP.NET\-Webseiten](../Topic/ASP.NET%20Web%20Forms%20Pages%20Overview.md)   
 [Übersicht über die Syntax von ASP.NET\-Webseiten](../Topic/ASP.NET%20Web%20Forms%20Page%20Syntax%20Overview.md)   
 [Programmieren von ASP.NET\-Webseiten](http://msdn.microsoft.com/de-de/5626c661-8057-4de8-b658-c2e35ed4b4c9)  
  
  