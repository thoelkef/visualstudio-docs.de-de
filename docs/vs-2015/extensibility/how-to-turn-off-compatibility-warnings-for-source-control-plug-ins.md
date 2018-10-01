---
title: 'Vorgehensweise: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cfa9ed4b06f8a2f567f6446f85f35e3f0cde244
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515587"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Vorgehensweise: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [aktivieren aus Kompatibilitätswarnungen für Quellcodeverwaltung-Plug-ins](https://docs.microsoft.com/visualstudio/extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins).  
  
Ein Benutzer möglicherweise mehrere kompatibilitätswarnungen angezeigt, wenn es sich bei Verwendung der quellcodeverwaltung in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Die Warnungen dargestellt richten sich nach den Funktionen von das Quellcodeverwaltungs-Plug-in und können wie folgt deaktiviert werden.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Zum Deaktivieren der Warnung: "So stellen Sie sicher eine optimale quellcodeverwaltung mit Visual Studio …"  
  
-   Legen Sie den folgenden Registrierungseintrag (den Wert hinzufügen, falls erforderlich):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Diese Warnung wird angezeigt, für alle nicht-[!INCLUDE[vsvss](../includes/vsvss-md.md)] -Plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Zum Deaktivieren der Warnung: "die installierte quellcodeverwaltung unterstützt nicht alle Funktionen, die..."  
  
-   Legen Sie die folgenden zwei Werte (die Werte hinzufügen, falls erforderlich):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Diese Warnung wird angezeigt, wenn das Quellcodeverwaltungs-Plug-in explizit Eintrittsinvarianz für mehrere Projekte nicht unterstützt (d. h., wenn sie in nur ein Datei- und Projektinformationen zu einem Zeitpunkt überprüfen kann).  
  
     Es wird empfohlen, die Unterstützung von Eintrittsinvarianz (`SCC_CAP_REENTRANT` Funktion); Dies wird daher diese Warnung entfernen. Allerdings ist diese Unterstützung nicht möglich, können diese Registrierungseinträge festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionsflags](../extensibility/capability-flags.md)

