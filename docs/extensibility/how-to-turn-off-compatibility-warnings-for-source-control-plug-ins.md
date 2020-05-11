---
title: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-Ins | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710728"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Gewusst wie: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-Ins
Ein Benutzer kann mehrere Kompatibilitätswarnungen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sehen, wenn die Quellcodeverwaltung in verwendet wird. Die angezeigten Warnungen hängen von den Funktionen des Quellcodeverwaltungs-Plug-Ins ab und können wie hier beschrieben deaktiviert werden.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>So deaktivieren Sie die Warnung: "Um eine optimale Quellcodeverwaltungsintegration mit Visual Studio sicherzustellen"

- Legen Sie den folgenden Registrierungseintrag fest (bei Bedarf den Wert hinzufügen):

   **HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl-DontDisplayCheckDotNETCompatible = dword:00000001**

   Diese Warnung wird für[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] alle Nicht-Plug-Ins angezeigt.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>So deaktivieren Sie die Warnung: "Der installierte Quellcodeverwaltungsanbieter unterstützt nicht alle Funktionen"

- Legen Sie die folgenden beiden Registrierungswerte fest (bei Bedarf werden die Werte hinzugefügt):

     **HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl-WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl-UseOldSCC = dword:00000001**

     Diese Warnung wird angezeigt, wenn das Quellcodeverwaltungs-Plug-In die Wiedereintrittsfähigkeit für mehrere Projekte nicht explizit unterstützt (d. h., wenn es jeweils nur eine Datei und ein Projekt einchecken kann).

     Es ist am besten, Wiedereintritt zu unterstützen (Fähigkeit);`SCC_CAP_REENTRANT` Dadurch wird diese Warnung entfernt. Wenn diese Unterstützung jedoch nicht möglich ist, können diese Registrierungseinträge festgelegt werden.

## <a name="see-also"></a>Weitere Informationen
- [Fähigkeitsflags](../extensibility/capability-flags.md)
