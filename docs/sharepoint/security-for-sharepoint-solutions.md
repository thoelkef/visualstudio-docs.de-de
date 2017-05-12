---
title: "Sicherheit f&#252;r SharePoint-L&#246;sungen"
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
  - "Sicherheit [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Sicherheit"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Sicherheit f&#252;r SharePoint-L&#246;sungen
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält die folgenden Funktionen zur Erhöhung der Sicherheit von SharePoint\-Anwendungen.  
  
## Einträge für sicheres Steuerelement  
 Jedes in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellte SharePoint\-Projektelement verfügt über eine Eigenschaft vom Typ **Einträge für sicheres Steuerelement**, die für eine Auflistung sicherer Steuerelemente steht.  Mithilfe der untergeordneten Eigenschaft **Sicher** können die Steuerelemente angegeben werden, die Sie für sicher halten.  Weitere Informationen finden Sie unter [Angeben sicherer Webparts](http://go.microsoft.com/fwlink/?LinkId=177521)[Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## AllowPartiallyTrustedCallers\-Attribut  
 Standardmäßig kann nur von Anwendungen, die im Laufzeit\-Codezugriffssicherheitssystem \(CAS\) als voll vertrauenswürdig gelten, auf eine freigegebene verwaltete Codeassembly zugegriffen werden.  Durch Markieren einer voll vertrauenswürdigen Assembly mit dem AllowPartiallyTrustedCallers\-Attribut wird teilweise vertrauenswürdigen Assemblys der Zugriff auf die Assembly ermöglicht.  
  
 Das AllowPartiallyTrustedCallers\-Attribut wird jeder SharePoint\-Lösung hinzugefügt, die nicht im globalen Assemblycache \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\) des Systems bereitgestellt wird.  Dies gilt auch für Sandkastenlösungen oder Lösungen, die im Verzeichnis "Bin" der SharePoint\-Anwendung bereitgestellt werden.  Weitere Informationen finden Sie und [Sicherheits\-Änderungen der Versions\-1 für. Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## Eigenschaft "Sicher vor Skripteinschleusung"  
 Der Begriff *Skripteinschleusung* bezeichnet das Einfügen von potenziell bösartigem Code in Steuerelemente oder Webseiten.  Zum Schutz von SharePoint 2010\-Websites vor Skripteinschleusungen können Mitwirkende standardmäßig keine Webparts oder deren Eigenschaften anzeigen oder bearbeiten.  Dieses Verhalten wird von einem SafeControl\-Attribut mit der Bezeichnung "SafeAgainstScript" gesteuert.  Legen Sie dieses Attribut in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unter **Einträge für sicheres Steuerelement** in der untergeordneten Eigenschaft **Sicher vor Skripteinschleusung** eines Projektelements fest.  Weitere Informationen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) und [Gewusst wie: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## Benutzerkontensteuerung von Windows Vista und Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] enthalten eine Sicherheitsfunktion, die als Benutzerkontensteuerung \(User Account Control, UAC\) bezeichnet wird.  Zum Entwickeln von SharePoint\-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unter [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] muss [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aufgrund der Benutzerkontensteuerung als Systemadministrator ausgeführt werden.  Wählen Sie im Menü **Starten** öffnen Sie das Kontextmenü für [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], und wählen Sie dann **Als Administrator ausführen** aus.  
  
 Um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zu konfigurieren kürzte ab um immer ausgeführt werden während Administrator, das Kontextmenü öffnen, dann **Eigenschaften** auswählen, die Schaltfläche **Erweitert** im Dialogfeld **Eigenschaften** und das Kontrollkästchen **Als Administrator ausführen** aktivieren.  
  
 Weitere Informationen finden Sie unter [Verstehen und Konfigurieren der Benutzerkontensteuerung in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476) und [Windows 7\-Benutzerkontensteuerung](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Überlegungen zu SharePoint\-Berechtigungen  
 Bei der Entwicklung von SharePoint\-Lösungen benötigen Sie ausreichende Berechtigungen, um SharePoint\-Lösungen auszuführen und zu debuggen.  Bevor Sie eine SharePoint\-Lösung testen können, führen Sie die folgenden Schritte aus, um sicherzustellen, dass Sie über die erforderlichen Berechtigungen verfügen:  
  
1.  Fügen Sie Ihr Benutzerkonto als Administrator für das System hinzu.  
  
2.  Fügen Sie Ihr Benutzerkonto als Farmadministrator für den SharePoint\-Server hinzu.  
  
    1.  In der SharePoint 2010\-Zentraladministration Wählen Sie den Link **Farmadministratorgruppe verwalten** aus.  
  
    2.  Auf der Seite **Farmadministratoren** wählen Sie die Menüoptionen **Neu** aus  
  
3.  Fügen Sie das Benutzerkonto zur Gruppe "WSS\_ADMIN\_WPG" hinzu.  
  
## Zusätzliche Sicherheitsressourcen  
 Weitere Informationen zu Sicherheitsproblemen finden Sie auf den folgenden Seiten:  
  
### Visual Studio\-Sicherheit  
  
-   [Sicherheit und Benutzerberechtigungen](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Sicherheit in systemeigenem und in .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Sicherheit in .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### SharePoint\-Sicherheit  
  
-   [SharePoint Foundations\-Verwaltung und Sicherheit](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [SharePoint\-Sicherheits\-Ressourcen\-Mittelpunkt](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Sichern von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Verbessern der Sicherheit von Webanwendungen: Bedrohungen und entsprechende Gegenmaßnahmen](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### Allgemeine Sicherheit  
  
-   [MSDN\-Sicherheits\-Entwicklungs\-Lebenszyklus](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Erstellen sicherer ASP.NET\-Anwendungen: Authentifizierung, Autorisierung und sichere Kommunikation](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  