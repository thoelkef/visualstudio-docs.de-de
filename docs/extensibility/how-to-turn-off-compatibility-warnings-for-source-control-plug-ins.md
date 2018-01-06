---
title: "Kompatibilität von Warnungen für die Datenquellen-Steuerelement-Plug-ins deaktivieren | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 622c0d4a75289e5025051b339b959a6b0b56442d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Vorgehensweise: Deaktivieren der Kompatibilität von Warnungen für die Datenquellen-Steuerelement-Plug-ins
Ein Benutzer möglicherweise mehrere Kompatibilität Warnungen angezeigt, bei der Verwendung von Datenquellen-Steuerelements in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Die Warnungen angezeigt richten sich nach den Funktionen des Datenquellen-Steuerelements-Plug-in und können wie folgt deaktiviert werden.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Um die Warnung zu deaktivieren: "so sicher, dass eine optimale Integration der quellcodeverwaltung mit Visual Studio..."  
  
-   Legen Sie den folgenden Registrierungseintrag (das Hinzufügen des Werts bei Bedarf):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Diese Warnung wird angezeigt, für alle nicht-[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] -Plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Um die Warnung zu deaktivieren: "der installierten Quellcodeverwaltungsanbieter unterstützt nicht alle Funktionen..."  
  
-   Legen Sie die folgenden beiden Registrierungswerte (die Werte addiert, falls erforderlich):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Diese Warnung wird angezeigt, wenn die Datenquellen-Steuerelement-Plug-in nicht explizit Reentranz für mehrere Projekte unterstützt wird (d. h., wenn es zu einem Zeitpunkt in nur ein Datei- und Projektnamen überprüfen kann).  
  
     Es wird empfohlen, Reentranz unterstützt (`SCC_CAP_REENTRANT` Funktion); Dies wird daher diese Warnung entfernt. Wenn diese Unterstützung nicht möglich ist, können jedoch diese Registrierungseinträge festlegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionsflags](../extensibility/capability-flags.md)