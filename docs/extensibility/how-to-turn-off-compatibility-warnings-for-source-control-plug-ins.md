---
title: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b1dca06ca82e467080f4bcd88a3b10c691345344
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888345"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Gewusst wie: Deaktivieren von kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins
Ein Benutzer möglicherweise mehrere kompatibilitätswarnungen angezeigt, wenn es sich bei Verwendung der quellcodeverwaltung in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Die Warnungen dargestellt richten sich nach den Funktionen von das Quellcodeverwaltungs-Plug-in und können wie folgt deaktiviert werden.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Zum Deaktivieren der Warnung: "So stellen Sie sicher die optimale quellcodeverwaltung mit Visual Studio zu"  
  
- Legen Sie den folgenden Registrierungseintrag (den Wert hinzufügen, falls erforderlich):  
  
   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**  
  
   Diese Warnung wird angezeigt, für alle nicht-[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] -Plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Zum Deaktivieren der Warnung: "die installierte quellcodeverwaltung unterstützt nicht alle Funktionen, die"  
  
-   Legen Sie die folgenden zwei Werte (die Werte hinzufügen, falls erforderlich):  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**  
  
    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**  
  
     Diese Warnung wird angezeigt, wenn das Quellcodeverwaltungs-Plug-in explizit Eintrittsinvarianz für mehrere Projekte nicht unterstützt (d. h., wenn sie in nur ein Datei- und Projektinformationen zu einem Zeitpunkt überprüfen kann).  
  
     Es wird empfohlen, die Unterstützung von Eintrittsinvarianz (`SCC_CAP_REENTRANT` Funktion); Dies wird daher diese Warnung entfernen. Allerdings ist diese Unterstützung nicht möglich, können diese Registrierungseinträge festgelegt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionsflags](../extensibility/capability-flags.md)