---
title: Problembehandlung bei Office-Projektmappensicherheit | Microsoft Docs
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
helpviewer_keywords: security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2ab3571da02fa56cd905369ee44e372aedea4e36
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="troubleshooting-office-solution-security"></a>Problembehandlung bei Office-Projektmappensicherheit
  Dieses Thema enthält Tipps zur Lösung von allgemeinen Problemen, die beim Absichern von Office-Projektmappen auftreten können.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Vertrauenswürdige Lösungen von eingeschränkte Sites nicht installiert werden  
 Benutzer können keine Lösung aus eine Webadresse installieren, wenn die Website in Internet Explorer-Zone eingeschränkter Sites aufgeführt ist. Dies gilt auch, wenn die Projektmappe mit einem vertrauenswürdigen Zertifikat signiert ist.  
  
 Die URL des Bereitstellungsmanifests kann in einer von fünf Zonen kategorisiert werden:  
  
-   Arbeitsplatz  
  
-   Internet  
  
-   Lokales intranet  
  
-   Vertrauenswürdige sites  
  
-   Eingeschränkte sites  
  
 Wenn Sie der Speicherort des Bereitstellungsmanifests Zone eingeschränkter Sites zugewiesen wurde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] die Projektmappe nicht installiert. Wenn der Speicherort bekannt ist und kann kann als vertrauenswürdig eingestuft, und der Benutzer entfernen Sie den Speicherort aus der Zone eingeschränkter Sites installieren die Lösung. Informationen zum Verwalten von Zonen finden Sie unter [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Lösungen können nicht vom Netzwerk-Dateifreigaben oder Websites installiert werden, wenn die verstärkte Sicherheitskonfiguration für InternetExplorer oder InternetExplorer 7 installiert ist  
 Internet Explorer Enhanced Security Configuration (IEESC) in Windows Server 2003 und höher, und InternetExplorer 7 und höher, schränkt die Möglichkeit von Benutzern zum Durchsuchen des Internets erheblich. Wenn Benutzer versuchen, die von einer Freigabe oder Web Netzwerkspeicherort Office-Projektmappen installieren, erhalten sie möglicherweise die folgende Fehlermeldung angezeigt: "benutzerdefinierte Funktionen in dieser Anwendung funktioniert nicht, weil das Zertifikat zum Signieren des Bereitstellungsmanifests für *SolutionName* ist nicht vertrauenswürdig. Wenden Sie sich an Ihren Administrator für weitere Unterstützung zu erhalten."  
  
 Mit IEESC und InternetExplorer 7 und höher Wenn die URL des Bereitstellungsmanifests in der Internetzone kategorisiert werden, muss das Manifest ein Zertifikat von einem vertrauenswürdigen Herausgeber oder die Lösung kann nicht installiert werden. Das Standardverhalten werden ohne IEESC stellen eine Entscheidung über die Vertrauenswürdigkeit der Endbenutzer aufgefordert.  
  
 Verwalten die Auswirkungen der IEESC und Internet Explorer 7 und höher zu identifizieren, Websites und Universal naming Convention (UNC)-Pfade, die Sie vertrauen und einer vertrauenswürdigen Sicherheitszonen ("Lokales Intranet" oder "Vertrauenswürdige Sites") hinzufügen. Informationen zum Verwalten von Zonen finden Sie unter [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  