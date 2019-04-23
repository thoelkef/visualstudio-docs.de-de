---
title: Sicherheit für SharePoint-Lösungen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31bcd41dc1a6fd7f314c7d701f52c3728dd2ee8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040453"
---
# <a name="security-for-sharepoint-solutions"></a>Sicherheit für SharePoint-Lösungen
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umfasst die folgenden Funktionen zur Erhöhung die Sicherheit von SharePoint-Anwendungen.

## <a name="safe-control-entries"></a>Einträge für sicheres Steuerelement
 Jede SharePoint-Projektelement in erstellt [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügt über eine **Einträge für sicheres Steuerelement** Eigenschaft, die eine sichere darstellt controls-Auflistung. Die **sicher** Untereigenschaften können Sie die Steuerelemente angeben, die Sie sicheren berücksichtigen. Weitere Informationen finden Sie unter [Geben Sie Paket und die Bereitstellung in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) und [angeben sicherer Webparts](http://go.microsoft.com/fwlink/?LinkId=177521).

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers-Attribut
 Standardmäßig können nur Anwendungen, die von das Laufzeitsystem Code Access Security (CAS) vertraut sind, eine freigegebene verwaltete Codeassembly zugreifen. Markieren einer voll vertrauenswürdigen Assembly mit dem AllowPartiallyTrustedCallers-Attribut kann teilweise vertrauenswürdige Assemblys, darauf zuzugreifen.

 Das AllowPartiallyTrustedCallers-Attribut wird jede SharePoint-Lösung, die nicht in den globalen Assemblycache des Systems bereitgestellt wurde hinzugefügt ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Dies schließt die Sandbox-Lösungen oder Lösungen, die für die Bin-Verzeichnis der SharePoint-Anwendung bereitgestellt. Weitere Informationen finden Sie unter [Version 1 Sicherheitsänderungen für das Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) und [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

## <a name="safe-against-script-property"></a>Sicher vor Skript (Eigenschaft)
 *Script-Injection* ist das Einfügen von potenziell bösartigem Code in Steuerelementen oder Webseiten. Um SharePoint 2010-Websites für Script-Injection zu schützen, können nicht die Contributors anzeigen oder Bearbeiten von Webparts oder ihre Eigenschaften standardmäßig. Dieses Verhalten wird durch eine SafeControl-Attribut, die mit der Bezeichnung "SafeAgainstScript" gesteuert. In [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], legen Sie dieses Attribut in einem Projektelement **Einträge für sicheres Steuerelement** Untereigenschaften **sicher für Skript**. Weitere Informationen finden Sie unter [Geben Sie Paket und die Bereitstellung in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) und [Vorgehensweise: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Vista und Windows 7 Benutzerkontensteuerung
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] enthalten eine Sicherheitsfunktion, die als Benutzerkontensteuerung (UAC) bezeichnet. Zum Entwickeln von SharePoint-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unter [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] muss [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aufgrund der Benutzerkontensteuerung als Systemadministrator ausgeführt werden. Von der **starten** Menü öffnen Sie das Kontextmenü für [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], und wählen Sie dann **als Administrator ausführen**.

 So konfigurieren Sie die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Verknüpfung immer als Administrator ausführen, öffnen Sie das Kontextmenü, wählen Sie **Eigenschaften**, wählen Sie die **erweitert** Schaltfläche der **Eigenschaften**(Dialogfeld), und wählen Sie dann die **als Administrator ausführen** Kontrollkästchen.

 Weitere Informationen finden Sie unter [verstehen und Konfigurieren der Benutzerkontensteuerung in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). und [Windows 7-Benutzerkontensteuerung](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Überlegungen zur SharePoint-Berechtigungen
 Bei der Entwicklung von SharePoint-Lösungen benötigen Sie ausreichende Berechtigungen, um SharePoint-Lösungen auszuführen und zu debuggen. Bevor Sie eine SharePoint-Lösung testen können, führen Sie die folgenden Schritte aus, um sicherzustellen, dass Sie über die erforderlichen Berechtigungen verfügen:

1. Fügen Sie Ihr Benutzerkonto als Administrator für das System hinzu.

2. Fügen Sie Ihr Benutzerkonto als Farmadministrator für den SharePoint-Server hinzu.

    1. Wählen Sie in SharePoint 2010-Zentraladministration die **verwalten Sie die Gruppe "Farmadministratoren"** Link.

    2. Auf der **Farmadministratoren** Seite die **neu** Menüoption

3. Fügen Sie das Benutzerkonto zur Gruppe "WSS_ADMIN_WPG" hinzu.

## <a name="additional-security-resources"></a>Zusätzliche Sicherheitsressourcen
 Weitere Informationen zu Sicherheitsproblemen finden Sie hier.

### <a name="visual-studio-security"></a>Visual Studio-Sicherheit

- [Sicherheit und Benutzerberechtigungen](http://go.microsoft.com/fwlink/?LinkId=177503)

- [Sicherheit in systemeigenem Code und .NET Framework-Code](http://go.microsoft.com/fwlink/?LinkId=177504)

- [Sicherheit in .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>SharePoint-Sicherheit

- [SharePoint Foundation-Verwaltung und Sicherheit](http://go.microsoft.com/fwlink/?LinkId=177501)

- [Ressourcencenter für SharePoint-Sicherheit](http://go.microsoft.com/fwlink/?LinkId=177498)

- [Sichern von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)

- [Erhöhen der Sicherheit von Webanwendungen: Bedrohungen und Gegenmaßnahmen](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>Allgemeine Sicherheit

- [MSDN Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)

- [Erstellen von Secure ASP.NET-Anwendungen: Authentifizierung, Autorisierung und sichere Kommunikation](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>Siehe auch

- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)