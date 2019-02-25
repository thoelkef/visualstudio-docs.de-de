---
title: Überschreibungen durch den Hilfeinhalts-Manager | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9dfd7f7d75a44cb28e2829e38c27b63a329eacaa
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54804465"
---
# <a name="help-content-manager-overrides"></a>Überschreibungen durch den Hilfeinhalts-Manager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Registrierung ändern, um das Standardverhalten des Help Viewers und der auf die Hilfe bezogenen Funktionen der Visual Studio-IDE zu ändern.  
  
|Aufgabe|-Registrierungsschlüssel|Wert und Definition|  
|----------|------------------|--------------------------|  
|Eindeutigen Dienstendpunkt definieren|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService: *HTTPValueForTheServiceEndpoint*.|  
|Online-/Offlinestandardeinstellungen definieren|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp – Geben Sie `0` ein, um lokale Hilfe anzugeben, und geben Sie `1` ein, um Onlinehilfe anzugeben.|  
|Eindeutigen F1-Endpunkt definieren|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|BITS-Auftragspriorität überschreiben|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\Help\v2.2|BITSPriority: Verwenden Sie einen der folgenden Werte: **foreground** (Vordergrund), **high** (hoch), **normal** oder **low** (niedrig).|  
|Online (und IDE-Onlineoption) deaktivieren|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled – Auf 1 festlegen, um Zugriff des Onlinehilfeinhalts zu deaktivieren.|  
|"Inhalt verwalten" deaktivieren|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled: Auf 1 festlegen, um die Registerkarte **Inhalt verwalten** im Help Viewer zu deaktivieren.|  
|Auf den lokalen Inhaltsspeicher auf der Netzwerkfreigabe zeigen|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath=”*ContentStoreNetworkShare*”|  
|Installation von Inhalt bei erstem Start von Visual Studio-Funktion deaktivieren.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection – Auf 1 festlegen, um Hilfefunktionen zu deaktivieren, die das beim ersten Start von Visual Studio konfiguriert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Help Viewer-Administratorhandbuch](../ide/help-viewer-administrator-guide.md)
