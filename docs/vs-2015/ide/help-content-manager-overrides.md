---
title: Überschreibungen durch den Hilfeinhalts-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2fae83a05b3f6f8774e7ed119483274f22c4ddc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514481"
---
# <a name="help-content-manager-overrides"></a>Überschreibungen durch den Hilfeinhalts-Manager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [unterstützen Inhalts-Manager-Außerkraftsetzungen](https://docs.microsoft.com/visualstudio/ide/help-content-manager-overrides).  
  
Sie können die Registrierung ändern, um das Standardverhalten des Help Viewers und der auf die Hilfe bezogenen Funktionen der Visual Studio-IDE zu ändern.  
  
|Aufgabe|-Registrierungsschlüssel|Wert und Definition|  
|----------|------------------|--------------------------|  
|Eindeutigen Dienstendpunkt definieren|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService: *HTTPValueForTheServiceEndpoint*.|  
|Online-/Offlinestandardeinstellungen definieren|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp – Geben Sie `0` ein, um lokale Hilfe anzugeben, und geben Sie `1` ein, um Onlinehilfe anzugeben.|  
|Eindeutigen F1-Endpunkt definieren|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|BITS-Auftragspriorität überschreiben|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\Help\v2.2|BITSPriority: Verwenden Sie einen der folgenden Werte: **foreground** (Vordergrund), **high** (hoch), **normal** oder **low** (niedrig).|  
|Online (und IDE-Onlineoption) deaktivieren|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled – Auf 1 festlegen, um Zugriff des Onlinehilfeinhalts zu deaktivieren.|  
|"Inhalt verwalten" deaktivieren|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled: Auf 1 festlegen, um die Registerkarte **Inhalt verwalten** im Help Viewer zu deaktivieren.|  
|Auf den lokalen Inhaltsspeicher auf der Netzwerkfreigabe zeigen|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath = "*ContentStoreNetworkShare*"|  
|Installation von Inhalt bei erstem Start von Visual Studio-Funktion deaktivieren.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection – Auf 1 festlegen, um Hilfefunktionen zu deaktivieren, die das beim ersten Start von Visual Studio konfiguriert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Help Viewer-Administratorhandbuch](../ide/help-viewer-administrator-guide.md)



