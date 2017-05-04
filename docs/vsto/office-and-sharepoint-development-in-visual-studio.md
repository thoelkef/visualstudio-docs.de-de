---
title: "Office and SharePoint Development in Visual Studio | Microsoft Docs"
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
  - "Office applications [Office development in Visual Studio], about developing applications"
  - "Office development in Visual Studio"
  - "Office projects"
  - "Visual Studio Tools for Office, see Office development in Visual Studio"
  - "Office applications [Office development in Visual Studio]"
  - "Office Business Applications"
  - "applications [Office development in Visual Studio]"
  - "programming [Office development in Visual Studio]"
  - "VSTO, see Office development in Visual Studio"
  - "Office, development with Visual Studio"
ms.assetid: 2ddec047-263a-4901-a54c-a15fc8472329
caps.latest.revision: 88
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 87
---
# Office and SharePoint Development in Visual Studio
  Sie können Microsoft Office und SharePoint erweitern, indem Sie eine einfache App oder ein Add\-In erstellen, die Benutzer im [Office Store](https://store.office.com/) oder einem Unternehmenskatalog herunterladen, oder indem sie eine.NET Framework\-basierte Lösung erstellen, die von Benutzern auf einem Computer installiert wird.  
  
 In diesem Thema:  
  
-   [Erstellen von Add-Ins für Office und SharePoint](#Apps)  
  
-   [Erstellen eines VSTO-Add-Ins](#Add-ins)  
  
-   [Erstellen einer SharePoint-Lösung](#Solutions)  
  
##  <a name="Apps"></a> Erstellen von Add\-Ins für Office und SharePoint  
 Office 2013 und SharePoint 2013 stellen ein neues Add\-In\-Modell vor, das Ihnen hilft, Add\-Ins als Erweiterungen von Office und SharePoint zu erstellen, zu verteilen und damit Geld zu verdienen.  Diese Add\-Ins können in Office oder SharePoint online ausgeführt werden, und Benutzer können von vielen Geräten mit ihnen interagieren.  
  
 Erfahren Sie, wie Sie das neue [Office\-Add\-In\-Modell](https://msdn.microsoft.com/library/office/jj220082.aspx) verwenden können, um die Office\-Erfahrungen Ihrer Benutzer zu erweitern.  
  
 Diese Add\-Ins belegen nur wenig Arbeitsspeicher im Vergleich zu VSTO\-Add\-Ins und \-Projektmappen, und Sie können sie mithilfe von fast allen Web\-Technologien wie HTML5, JavaScript, CSS3 und XML\-Programmierung erstellen.  Verwenden Sie zu Beginn die Office Developer Tools in Visual Studio oder das einfache, webbasierte Tool mit dem Codenamen Napa Office 365\-Entwicklungstools, mit dessen Hilfe Sie Projekte erstellen, Code schreiben und Ihre Add\-Ins in einem Browser ausführen können.  
  
 ![Konzeptmodell für Apps für Office und SharePoint](../vsto/media/officeandsharepointapps2015.png "Konzeptmodell für Apps für Office und SharePoint")  
  
 **Weitere Informationen**  
  
|An|Siehe|  
|--------|-----------|  
|Weitere Informationen zu den Napa Office 365\-Entwicklungstools:|[Napa Office 365\-Entwicklungstools](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
### Erstellen eines Office Add\-Ins  
 Um die Funktionalität von Office zu erweitern, erstellen Sie ein Office\-Add\-In. Es handelt sich im Grunde um eine Webseite, die in einer Office\-Anwendung wie Excel, Word, Outlook und PowerPoint gehostet wird. Ihre Anwendung kann zu Dokumenten, Arbeitsblättern, e\-Mail\-Nachrichten, Terminen, Präsentationen und Projekten Funktionalität hinzufügen.  
  
 Sie können Ihre Anwendung im Office Store verkaufen.  Im [Office Store](https://store.office.com/) können Sie Ihre Add\-Ins einfach verkaufen, Updates verwalten und die Telemetrie nachverfolgen. Sie können Ihre Anwendung für Benutzer über einen Anwendungskatalog in SharePoint oder auf dem Exchange Server veröffentlichen.  
  
 Die folgende Anwendung für Office zeigt Arbeitsblatt\-Daten in einer Bing\-Karte.  
  
 ![Inhalts-App für Office](../vsto/media/appforoffice.png "Inhalts-App für Office")  
  
 **Weitere Informationen**  
  
|An|Siehe|  
|--------|-----------|  
|Erfahren Sie mehr über Office\-Add\-Ins, und erstellen Sie dann eins.|[Office\-Add\-Ins](http://msdn.microsoft.com/office/dn448457)|  
|Vergleichen Sie die verschiedenen Möglichkeiten, mit denen Sie Office erweitern können, und entscheiden Sie, ob Sie eine Anwendung oder ein Office\-Add\-In verwenden möchten.|[Roadmap für Office\-Add\-Ins, VSTO und VBA](http://blogs.msdn.com/b/officeapps/archive/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba.aspx)|  
|Weitere Informationen zu den Napa Office 365\-Entwicklungstools:|[Napa Office 365\-Entwicklungstools](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
### Erstellen eines SharePoint\-Add\-Ins  
 Um SharePoint für Ihre Benutzer zu erweitern, erstellen Sie ein SharePoint\-Add\-In. Es handelt sich im Grunde um, eine kleine, leicht bedienbare, eigenständige Anwendung, die für Ihre Benutzer oder Unternehmen einen Bedarf deckt.  
  
 Sie können Ihre App für SharePoint im [Office Store](https://store.office.com/) verkaufen. Sie können Ihr Add\-In für Benutzer auch über einen Add\-In\-Katalog in SharePoint veröffentlichen.  Websitebesitzer können Ihr Add\-In ohne einen Farmserver oder Websiteauflistungsadministrator auf ihren SharePoint\-Websites installieren, aktualisieren und deinstallieren.  
  
 Hier ist ein Beispiel für eine Anwendung für SharePoint, mit dem Benutzer Kontakte verwalten können.  
  
 ![Geschäftskontaktmanager-App für SharePoint](../vsto/media/appforsharepoint.png "Geschäftskontaktmanager-App für SharePoint")  
  
 **Weitere Informationen**  
  
|An|Siehe|  
|--------|-----------|  
|Erfahren Sie mehr über SharePoint\-Add\-Ins, und erstellen Sie dann eins.|[SharePoint\-Add\-Ins](https://msdn.microsoft.com/library/office/fp179930.aspx)|  
|Vergleichen Sie Add\-Ins für SharePoint mit herkömmlichen SharePoint\-Lösungen.|[SharePoint\-Add\-Ins im Vergleich mit SharePoint\-Lösungen](http://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Wählen Sie aus, ob Sie SharePoint\-Add\-In oder eine SharePoint\-Lösung erstellen möchten.|[Entscheiden zwischen SharePoint\-Add\-Ins und SharePoint\-Lösungen](https://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Weitere Informationen zu den Napa Office 365\-Entwicklungstools:|[Napa Office 365\-Entwicklungstools](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
##  <a name="Add-ins"></a> Erstellen eines VSTO\-Add\-Ins  
 Erstellen Sie ein VSTO\-Add\-In für Office 2007 oder Office 2010 oder eine Erweiterung für Office 2013 und Office 2016 mit Office\-Add\-Ins, die über das übliche Maß hinausreichen. VSTO\-Add\-Ins können nur auf dem Desktop ausgeführt werden. Benutzer müssen VSTO\-Add\-Ins installieren, da in der Regel die Bereitstellung und der Support schwieriger sind.  Allerdings kann das VSTO\-Add\-In stärker in Office integriert werden. Sie können z. B. die Office\-Multifunktionsleiste Registerkarten und Steuerelemente hinzufügen und erweiterte Automatisierung\-Aufgaben wie das Zusammenführen von Dokumenten oder das Ändern von Diagrammen durchführen. Sie können das .NET Framework einsetzen und C\# und Visual Basic zur Interaktion mit Office\-Objekten verwenden.  
  
 Es folgt ein Beispiel dazu, welche Möglichkeiten ein VSTO\-Add\-In bietet. Dieses VSTO\-Add\-In fügt Menübandsteuerelemente, einen benutzerdefinierten Aufgabenbereich und ein Dialogfeld zu PowerPoint hinzu.  
  
 ![PowerPoint-Add-In-Lösung](../vsto/media/powerpointaddin.png "PowerPoint-Add-In-Lösung")  
  
 **Weitere Informationen**  
  
|An|Lesen|  
|--------|-----------|  
|Vergleichen Sie die verschiedenen Möglichkeiten, mit denen Sie Office erweitern können, und entscheiden Sie, ob Sie ein VSTO\-Add\-In oder ein Office\-Add\-In verwenden möchten.|[Roadmap für Office\-Add\-Ins, VSTO und VBA](http://blogs.msdn.com/b/officeapps/archive/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba.aspx)|  
|Erstellen eines VSTO\-Add\-Ins|[Mit Visual Studio erstellte VSTO\-Add\-Ins](https://msdn.microsoft.com/library/jj620922.aspx)|  
  
##  <a name="Solutions"></a> Erstellen einer SharePoint\-Lösung  
 Erstellen einer SharePoint\-Lösung für SharePoint Foundation 2010 und SharePoint Server 2010 oder als Erweiterung von SharePoint 2013 und SharePoint 2016 mit einem SharePoint\-Add\-In, das über das übliche Maß hinausgeht.  
  
 SharePoint\-Lösungen erfordern lokale SharePoint\-Farm\-Server. Administratoren müssen sie installieren, und da Lösungen in SharePoint ausgeführt werden, können sie die Leistung des Servers beeinträchtigen. Allerdings bieten Lösungen einen tieferen Zugriff auf SharePoint\-Objekte. Wenn Sie eine SharePoint\-Lösung erstellen, können Sie außerdem das .NET Framework und C\# und Visual Basic für die Interaktion mit SharePoint\-Objekte verwenden.  
  
 **Weitere Informationen**  
  
|An|Siehe|  
|--------|-----------|  
|Vergleichen Sie SharePoint\-Lösungen und SharePoint\-Add\-Ins.|[SharePoint\-Add\-Ins im Vergleich mit SharePoint\-Lösungen](http://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Erstellen Sie eine SharePoint\-Lösung.|[Erstellen von SharePoint-Lösungen](../sharepoint/create-sharepoint-solutions.md)|  
  
  