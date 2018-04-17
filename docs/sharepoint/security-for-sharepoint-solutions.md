---
title: Sicherheit für SharePoint-Lösungen | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 471de3ab69a969f5153723658c628d659038c3a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="security-for-sharepoint-solutions"></a>Sicherheit für SharePoint-Lösungen
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umfasst die folgenden Funktionen, mit denen die Sicherheit von SharePoint-Anwendungen zu verbessern.  
  
## <a name="safe-control-entries"></a>Einträge für sicheres Steuerelement  
 In jeder SharePoint-Projektelements erstellt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügt über eine **Einträge für sicheres Steuerelement** steuerelementauflistung der Eigenschaft, ein sicheres darstellt. Die **sichere** Untereigenschaften ermöglicht Ihnen das Festlegen der Steuerelemente, die Sie sicheren berücksichtigen. Weitere Informationen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) und [angeben sicherer Webparts](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers-Attribut  
 Standardmäßig können nur Anwendungen, die das Laufzeitsystem Code Access Security (CAS) vollständig vertrauenswürdig sind, eine freigegebene verwaltete Codeassembly zugreifen. Markieren einer voll vertrauenswürdigen Assembly mit dem AllowPartiallyTrustedCallers-Attribut kann teilweise vertrauenswürdige Assemblys, darauf zuzugreifen.  
  
 AllowPartiallyTrustedCallers-Attribut wird auf alle SharePoint-Lösung, die im globalen Systemassemblycache bereitgestellt wurde hinzugefügt ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Dies schließt sandkastenlösungen oder Lösungen, die für die SharePoint-Anwendung-Verzeichnis "bin" bereitgestellt. Weitere Informationen finden Sie unter [Version 1 Sicherheitsänderungen für das Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) und [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## <a name="safe-against-script-property"></a>Safe für Script-Eigenschaft  
 *Script-Injection* ist das Einfügen von potenziell bösartigen Code in Steuerelementen oder Webseiten. Zum Schutz von SharePoint 2010-Websites für Script-Injection nicht Contributors anzeigen oder Bearbeiten von Webparts oder ihre Eigenschaften in der Standardeinstellung. Dieses Verhalten wird durch eine SafeControl-Attribut, die mit der Bezeichnung "SafeAgainstScript" gesteuert. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], legen Sie dieses Attribut in einem Projektelement **Einträge für sicheres Steuerelement** Untereigenschaften **sicher für Skript**. Weitere Informationen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) und [wie: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## <a name="vista-and-windows-7-user-account-control"></a>Vista und Windows 7 Benutzerkontensteuerung  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] enthalten eine Sicherheitsfunktion, die als Benutzerkontensteuerung (UAC) bezeichnet. Zum Entwickeln von SharePoint-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unter [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] muss [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aufgrund der Benutzerkontensteuerung als Systemadministrator ausgeführt werden. Aus der **starten** Menü öffnen Sie das Kontextmenü für [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], und wählen Sie dann **als Administrator ausführen**.  
  
 So konfigurieren Sie die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Verknüpfung immer als Administrator ausführen, öffnen Sie das Kontextmenü, wählen **Eigenschaften**, wählen Sie die **erweitert** Schaltfläche der **Eigenschaften**(Dialogfeld), und wählen Sie dann die **als Administrator ausführen** Kontrollkästchen.  
  
 Weitere Informationen finden Sie unter [verstehen und Konfigurieren der Benutzerkontensteuerung in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). und [Windows 7-Benutzerkontensteuerung](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Überlegungen zu SharePoint-Berechtigungen  
 Bei der Entwicklung von SharePoint-Lösungen benötigen Sie ausreichende Berechtigungen, um SharePoint-Lösungen auszuführen und zu debuggen. Bevor Sie eine SharePoint-Lösung testen können, führen Sie die folgenden Schritte aus, um sicherzustellen, dass Sie über die erforderlichen Berechtigungen verfügen:  
  
1.  Fügen Sie Ihr Benutzerkonto als Administrator für das System hinzu.  
  
2.  Fügen Sie Ihr Benutzerkonto als Farmadministrator für den SharePoint-Server hinzu.  
  
    1.  Wählen Sie in SharePoint 2010-Zentraladministration die **Administratorgruppe der Farm verwalten** Link.  
  
    2.  Auf der **Farmadministratoren** Seite, und wählen Sie die **neu** Menüoption  
  
3.  Fügen Sie das Benutzerkonto zur Gruppe "WSS_ADMIN_WPG" hinzu.  
  
## <a name="additional-security-resources"></a>Zusätzliche Ressourcen  
 Weitere Informationen zu Sicherheitsproblemen finden Sie hier.  
  
### <a name="visual-studio-security"></a>Visual Studio-Sicherheit  
  
-   [Sicherheit und Benutzerberechtigungen](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Sicherheit im einheitlichen als auch .NET Framework-Code](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Sicherheit in .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>SharePoint-Sicherheit  
  
-   [SharePoint Foundation-Verwaltung und Sicherheit](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Ressourcencenter für SharePoint-Sicherheit](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Sichern von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Verbesserung Webanwendungssicherheit: Bedrohungen und Gegenmaßnahmen](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>Allgemeine Sicherheit  
  
-   [MSDN Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Building Secure ASP.NET Applications: Authentifizierung, Autorisierung und sichere Kommunikation](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Anforderungen für die Entwicklung von SharePoint-Projektmappen](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  