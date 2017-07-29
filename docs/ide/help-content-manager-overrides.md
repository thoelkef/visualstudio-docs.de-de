---
title: "Überschreibungen durch den Hilfeinhalts-Manager | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c4889d40e9ca53cccf7de384e609eb959d8981f5
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="help-content-manager-overrides"></a>Überschreibungen durch den Hilfeinhalts-Manager
Sie können die Registrierung ändern, um das Standardverhalten des Help Viewers und der auf die Hilfe bezogenen Funktionen der Visual Studio-IDE zu ändern.  
  
|Aufgabe|-Registrierungsschlüssel|Wert und Definition|  
|----------|------------------|--------------------------|  
|Eindeutigen Dienstendpunkt definieren|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService: *HTTPValueForTheServiceEndpoint*.|  
|Online-/Offlinestandardeinstellungen definieren|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp – Geben Sie `0` ein, um lokale Hilfe anzugeben, und geben Sie `1` ein, um Onlinehilfe anzugeben.|  
|Eindeutigen F1-Endpunkt definieren|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|BITS-Auftragspriorität überschreiben|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\Help\v2.2|BITSPriority: Verwenden Sie einen der folgenden Werte: **foreground** (Vordergrund), **high** (hoch), **normal** oder **low** (niedrig).|  
|Online (und IDE-Onlineoption) deaktivieren|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled – Auf 1 festlegen, um Zugriff des Onlinehilfeinhalts zu deaktivieren.|  
|"Inhalt verwalten" deaktivieren|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled: Auf 1 festlegen, um die Registerkarte **Inhalt verwalten** im Help Viewer zu deaktivieren.|  
|Auf den lokalen Inhaltsspeicher auf der Netzwerkfreigabe zeigen|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath="*ContentStoreNetworkShare*"|  
|Installation von Inhalt bei erstem Start von Visual Studio-Funktion deaktivieren.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (auf einem 64-Bit-Computer)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection – Auf 1 festlegen, um Hilfefunktionen zu deaktivieren, die das beim ersten Start von Visual Studio konfiguriert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Help Viewer-Administratorhandbuch](../ide/help-viewer-administrator-guide.md)
