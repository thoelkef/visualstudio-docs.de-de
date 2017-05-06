---
title: "Anforderungen f&#252;r die Entwicklung von SharePoint-L&#246;sungen"
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
  - "SharePoint-Entwicklung in Visual Studio, Voraussetzungen"
  - "SharePoint-Entwicklung in Visual Studio, Anforderungen"
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Anforderungen f&#252;r die Entwicklung von SharePoint-L&#246;sungen
  Sie müssen die folgenden erforderlichen Komponenten auf dem System installieren, bevor Sie die in Visual Studio enthaltenen SharePoint\-Entwicklungstools für Lösungen verwenden können:  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] oder eine Edition der Anwendungslebenszyklus\-Verwaltung \(Application Lifecycle Management, ALM\) von Visual Studio.  
  
    -   Die [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]\- oder [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\-Funktion oder beide bei Installation von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] unter [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] \(64\-Bit\) oder [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 \(64\-Bit\).  
  
     oder  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] unter [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] \(64\-Bit\) oder [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 \(64\-Bit\).  
  
> [!NOTE]  
>  Während offiziell nur Serverbetriebssysteme von SharePoint unterstützt werden, sind zwei Clientbetriebssysteme zugelassen: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] und [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1.  Weitere Informationen finden Sie im [Installationshandbuch für die Entwicklungsumgebung für SharePoint 2010](http://go.microsoft.com/fwlink/?LinkID=164557).  
  
 Business Data Connectivity \(BDC\)\-Modell\-Projekttypen erfordern, dass [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] auf dem System installiert ist.  
  
 Um SharePoint\-Lösungen in Visual Studio zu entwickeln, müssen Sie SharePoint auf dem gleichen Computer wie Visual Studio installieren.  Auch unterstützen die SharePoint\-Entwicklertools nur eine eigenständige SharePoint\-Konfiguration; sie unterstützen keine \(Remote\-\)Farmkonfiguration.  
  
> [!NOTE]  
>  SharePoint\-Projekte in Visual Studio unterstützen nur [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].  Wenn Sie [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] für ein neues SharePoint\-Projekt auswählen, wird trotzdem [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)] als Zielversion verwendet.  
  
 Weitere Informationen zum Installieren von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] finden Sie unter [Installieren von Visual Studio](../Topic/Installing%20Visual%20Studio.md).  
  
## Benutzerkontensteuerung von Windows Vista und Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] enthalten eine Sicherheitsfunktion, die als Benutzerkontensteuerung \(User Account Control, UAC\) bezeichnet wird.  Zum Entwickeln von SharePoint\-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unter [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] muss [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aufgrund der Benutzerkontensteuerung als Systemadministrator ausgeführt werden.  Öffnen Sie auf dem Desktop das Kontextmenü für [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], und wählen Sie dann **Als Administrator ausführen**.  
  
 Um die Desktopverknüpfung so zu konfigurieren, dass die Ausführung immer als Administrator erfolgt, öffnen Sie das Kontextmenü, klicken Sie auf **Eigenschaften**, klicken Sie auf die Schaltfläche **Erweitert**, und aktivieren Sie dann das Kontrollkästchen **Als Administrator ausführen**.  
  
 Weitere Informationen finden Sie unter [Verstehen und Konfigurieren der Benutzerkontensteuerung in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476) und [Windows 7\-Benutzerkontensteuerung](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Überlegungen zu SharePoint\-Berechtigungen  
 Bei der Entwicklung von SharePoint\-Lösungen benötigen Sie ausreichende Berechtigungen, um SharePoint\-Lösungen auszuführen und zu debuggen.  Bevor Sie eine SharePoint\-Lösung testen können, führen Sie die folgenden Schritte aus, um sicherzustellen, dass Sie über die erforderlichen Berechtigungen verfügen:  
  
1.  Fügen Sie Ihr Benutzerkonto als Administrator für das System hinzu.  
  
2.  Fügen Sie Ihr Benutzerkonto als Farmadministrator für den SharePoint\-Server hinzu.  
  
    1.  Klicken Sie in der SharePoint\-Zentraladministration auf den Link **Farmadministratorgruppe verwalten**.  
  
    2.  Wählen Sie auf der Seite **Farmadministratoren** die Schaltfläche **Neu** aus.  
  
3.  Fügen Sie das Benutzerkonto zur Gruppe "WSS\_ADMIN\_WPG" hinzu.  
  
## Siehe auch  
 [Getting Started &#40;SharePoint Development in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  