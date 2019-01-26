---
title: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d90ab2553eb69a5ea429dec3848c2aecd5fa86a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978801"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Vorgehensweise: Deaktivieren von kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins
Ein Benutzer möglicherweise mehrere kompatibilitätswarnungen angezeigt, wenn es sich bei Verwendung der quellcodeverwaltung in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Die Warnungen dargestellt richten sich nach den Funktionen von das Quellcodeverwaltungs-Plug-in und können wie folgt deaktiviert werden.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Um die Warnung zu deaktivieren: "So stellen Sie sicher die optimale quellcodeverwaltung mit Visual Studio zu"  
  
- Legen Sie den folgenden Registrierungseintrag (den Wert hinzufügen, falls erforderlich):  
  
   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**  
  
   Diese Warnung wird angezeigt, für alle nicht-[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] -Plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Um die Warnung zu deaktivieren: "Die installierte quellcodeverwaltung unterstützt nicht alle Funktionen, die"  
  
-   Legen Sie die folgenden zwei Werte (die Werte hinzufügen, falls erforderlich):  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**  
  
    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**  
  
     Diese Warnung wird angezeigt, wenn das Quellcodeverwaltungs-Plug-in explizit Eintrittsinvarianz für mehrere Projekte nicht unterstützt (d. h., wenn sie in nur ein Datei- und Projektinformationen zu einem Zeitpunkt überprüfen kann).  
  
     Es wird empfohlen, die Unterstützung von Eintrittsinvarianz (`SCC_CAP_REENTRANT` Funktion); Dies wird daher diese Warnung entfernen. Allerdings ist diese Unterstützung nicht möglich, können diese Registrierungseinträge festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionsflags](../extensibility/capability-flags.md)