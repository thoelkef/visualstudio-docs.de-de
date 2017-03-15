---
title: "Kompatibilität von Warnungen für Source Control-Plug-ins deaktivieren | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: e1dda3bd8c41efcf74a1b27f764fdfbf817f8d63
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Gewusst wie: Deaktivieren der Kompatibilität von Warnungen für Source Control-Plug-ins
Ein Benutzer möglicherweise mehrere Kompatibilität Warnungen angezeigt, beim Datenquellen-Steuerelement im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Die Warnungen angezeigt, hängt die Funktionen des Datenquellen-Steuerelements-Plug-in und können wie folgt deaktiviert werden.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Zum Deaktivieren der Warnung: "So gewährleisten optimale Quellcode-Verwaltungsanbieter mit Visual Studio..."  
  
-   Legen Sie den folgenden Registrierungseintrag (den Wert hinzufügen, falls erforderlich):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD:&00000;001  
  
     Diese Warnung wird angezeigt, für alle nicht -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] -Plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Zum Deaktivieren der Warnung: "der installierte Quellcode-Verwaltungsanbieter unterstützt nicht alle Funktionen..."  
  
-   Legen Sie die folgenden zwei Werte (die Werte hinzufügen, falls erforderlich):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD:&00000;000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD:&00000;001  
  
     Diese Warnung wird angezeigt, wenn das Datenquellen-Steuerelement, das plug-in explizit Eintrittsinvarianz für mehrere Projekte nicht unterstützt (d. h., wenn es zu einem Zeitpunkt in nur ein Datei- und Projektinformationen überprüfen kann).  
  
     Es empfiehlt sich, Reentranz zu unterstützen (`SCC_CAP_REENTRANT` Funktion); dies also entfernt diese Warnung. Wenn dies nicht möglich ist, können jedoch diese Registrierungseinträge festlegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Capability Flags](../extensibility/capability-flags.md)
