---
title: Problembehandlung bei Office-projektmappensicherheit
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f2cb978ddd62c3e274133e2d209c2634783c708
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871233"
---
# <a name="troubleshoot-office-solution-security"></a>Problembehandlung bei Office-projektmappensicherheit
  Dieses Thema enthält Tipps zum Beheben von gängigen Problemen, die beim Sichern von Office-Projektmappen auftreten können.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Vertrauenswürdige Lösungen können nicht von eingeschränkten Sites installiert werden  
 Benutzer können nicht vom Web aus eine Lösung installieren, wenn die Website in Internet Explorer-Zone eingeschränkter Sites aufgeführt ist. Dies gilt auch, wenn die Projektmappe mit einem vertrauenswürdigen Zertifikat signiert ist.  
  
 Die URL des Bereitstellungsmanifests kann in einer der fünf Zonen eingeteilt werden:  
  
- Arbeitsplatz  
  
- Internet  
  
- Lokales intranet  
  
- Vertrauenswürdige sites  
  
- Eingeschränkte sites  
  
  Wenn der Speicherort des Bereitstellungsmanifests zur Zone eingeschränkter Sites zugewiesen wurde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] die Projektmappe nicht installiert. Wenn der Speicherort bekannt ist und kann kann als vertrauenswürdig eingestuft, und der Benutzer entfernen den Speicherort aus der Zone eingeschränkter Sites installieren die Lösung. Weitere Informationen zum Verwalten von Zonen, finden Sie unter [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Lösungen können nicht von Netzwerkdateifreigaben oder Websites installiert werden, wenn die verstärkte Sicherheitskonfiguration für Internet Explorer oder Internet Explorer 7 installiert ist  
 Internet Explorer Enhanced Security Configuration (IEESC) in Windows Server 2003 und höher und InternetExplorer 7 und höher, schränkt die Möglichkeit von Benutzern zum Durchsuchen des Internets erheblich. Wenn Benutzer versuchen, installieren Sie Office-Projektmappen aus einer Netzwerkdatei freigeben oder Webspeicherort, sie erhalten möglicherweise die folgende Fehlermeldung angezeigt: "Benutzerdefinierte Funktionen können in dieser Anwendung funktioniert nicht, da das Zertifikat zum Signieren des Bereitstellungsmanifests für verwendet *SolutionName* ist nicht vertrauenswürdig. Wenden Sie sich an Ihren Administrator um Hilfe zu erhalten."  
  
 Mit IEESC und InternetExplorer 7 und höher Wenn die URL des Bereitstellungsmanifests in der Internetzone kategorisiert werden, muss das Manifest ein Zertifikat von einem vertrauenswürdigen Herausgeber oder die Projektmappe kann nicht installiert werden. Standardmäßig werden ohne IEESC stellen eine Entscheidung über die Vertrauenswürdigkeit der Endbenutzer aufgefordert.  
  
 Verwalten der Auswirkungen von IEESC und Internet Explorer 7 und höher zu identifizieren, Websites und Universal naming Convention (UNC)-Pfade, die Sie vertrauen und Hinzufügen eines vertrauenswürdigen Sicherheitszonen (lokales Intranet oder vertrauenswürdige Sites). Weitere Informationen zum Verwalten von Zonen, finden Sie unter [ClickOnce konfigurieren vertrauenswürdiger Herausgeber](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
