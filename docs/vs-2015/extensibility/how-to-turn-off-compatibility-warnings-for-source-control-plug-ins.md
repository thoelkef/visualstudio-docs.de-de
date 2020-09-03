---
title: 'Vorgehensweise: Deaktivieren von Kompatibilitäts Warnungen für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4397b2710a7de4addd97bfcbdb4f8e80e2b9c70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204047"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Gewusst wie: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei der Verwendung der Quell Code Verwaltung in werden möglicherweise mehrere Kompatibilitäts Warnungen angezeigt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Welche Warnungen angezeigt werden, hängt von den Funktionen des Quellcodeverwaltungs-Plug-ins ab und kann wie hier beschrieben deaktiviert werden.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>So deaktivieren Sie die Warnung: "um eine optimale Integration der Quell Code Verwaltung in Visual Studio sicherzustellen..."  
  
- Legen Sie den folgenden Registrierungs Eintrag fest (fügen Sie ggf. den Wert hinzu):  
  
     HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol\dontdisplaycheckdotnetcompatible = DWORD: 00000001  
  
     Diese Warnung wird für alle nicht- [!INCLUDE[vsvss](../includes/vsvss-md.md)] Plug-Ins angezeigt.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>So deaktivieren Sie die Warnung: "der installierte Quell Code Verwaltungs Anbieter unterstützt nicht alle Funktionen..."  
  
- Legen Sie die folgenden beiden Registrierungs Werte fest (fügen Sie ggf. die Werte hinzu):  
  
     HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol\warnedoldmsscciprovider = DWORD: 00000000  
  
     HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol\useoldscc = DWORD: 00000001  
  
     Diese Warnung wird angezeigt, wenn das Quellcodeverwaltungs-Plug-in für mehrere Projekte nicht explizit unterstützt (d. h., wenn nur eine Datei und ein Projekt gleichzeitig eingecheckt werden können).  
  
     Es ist am besten, den erneuten eintreten ( `SCC_CAP_REENTRANT` Funktion) zu unterstützen. Dadurch wird diese Warnung entfernt. Wenn diese Unterstützung jedoch nicht möglich ist, können diese Registrierungseinträge festgelegt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionsflags](../extensibility/capability-flags.md)
