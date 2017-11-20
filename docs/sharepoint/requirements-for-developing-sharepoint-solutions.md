---
title: "Anforderungen für die Entwicklung von SharePoint-Lösungen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a29eee363f3ad886d9ea6a13ee43475fba2e9448
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Anforderungen für die Entwicklung von SharePoint-Lösungen
  Sie müssen die folgenden erforderlichen Komponenten auf dem System installieren, bevor Sie die in Visual Studio enthaltenen SharePoint-Entwicklungstools für Lösungen verwenden können:  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]oder eine Edition von Visual Studio Application Lifecycle Management (ALM).  
  
    -   Die [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]- oder [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]-Funktion oder beide bei Installation von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]auf 64-Bit-Systemen installiert [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] oder 64-Bit- [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
     oder  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]auf 64-Bit-Systemen installiert [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] oder 64-Bit- [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.  
  
> [!NOTE]  
>  Während offiziell nur Serverbetriebssysteme von SharePoint unterstützt werden, sind zwei Clientbetriebssysteme zugelassen: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] und [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1. Weitere Informationen finden Sie unter [Installationshandbuch für SharePoint Server 2010 Developer Arbeitsstation](http://go.microsoft.com/fwlink/?LinkID=164557).  
  
 Business Data Connectivity (BDC)-Modell-Projekttypen erfordern, dass [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] auf dem System installiert ist.  
  
 Um SharePoint-Lösungen in Visual Studio zu entwickeln, müssen Sie SharePoint auf dem gleichen Computer wie Visual Studio installieren. Auch unterstützen die SharePoint-Entwicklertools nur eine eigenständige SharePoint-Konfiguration; sie unterstützen keine (Remote-)Farmkonfiguration.  
  
> [!NOTE]  
>  SharePoint-Projekte in Visual Studio unterstützen nur [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. Wenn Sie [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] für ein neues SharePoint-Projekt auswählen, wird trotzdem [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)] als Zielversion verwendet.  
  
 Weitere Informationen zum Installieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], finden Sie unter [installieren Sie Visual Studio](../install/install-visual-studio.md).  
  
## <a name="vista-and-windows-7-user-account-control-uac"></a>Benutzerkontensteuerung von Windows Vista und Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] enthalten eine Sicherheitsfunktion, die als Benutzerkontensteuerung (UAC) bezeichnet wird. Zum Entwickeln von SharePoint-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unter [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] und [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] muss [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aufgrund der Benutzerkontensteuerung als Systemadministrator ausgeführt werden. Öffnen Sie auf dem Desktop das Kontextmenü für [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], und wählen Sie dann **als Administrator ausführen**.  
  
 Um die desktopverknüpfung immer als Administrator ausführen zu konfigurieren, öffnen Sie das Kontextmenü, wählen Sie **Eigenschaften**, wählen Sie die **erweitert** Schaltfläche und wählen Sie dann die **als Administrator ausführen**  Kontrollkästchen.  
  
 Weitere Informationen finden Sie unter [verstehen und Konfigurieren der Benutzerkontensteuerung in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). und [Windows 7-Benutzerkontensteuerung](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Überlegungen zu SharePoint-Berechtigungen  
 Bei der Entwicklung von SharePoint-Lösungen benötigen Sie ausreichende Berechtigungen, um SharePoint-Lösungen auszuführen und zu debuggen. Bevor Sie eine SharePoint-Lösung testen können, führen Sie die folgenden Schritte aus, um sicherzustellen, dass Sie über die erforderlichen Berechtigungen verfügen:  
  
1.  Fügen Sie Ihr Benutzerkonto als Administrator für das System hinzu.  
  
2.  Fügen Sie Ihr Benutzerkonto als Farmadministrator für den SharePoint-Server hinzu.  
  
    1.  Wählen Sie in der SharePoint-Zentraladministration die **Administratorgruppe der Farm verwalten** Link.  
  
    2.  Auf der **Farmadministratoren** Seite, und wählen Sie die **neu** Schaltfläche.  
  
3.  Fügen Sie das Benutzerkonto zur Gruppe "WSS_ADMIN_WPG" hinzu.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte &#40; SharePoint-Entwicklung in Visual Studio &#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  