---
title: "Überschreibungen durch den Hilfeinhalts-Manager | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 143bc6af5aa42eb480d5eff736633c2df6e68979
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="help-content-manager-overrides"></a>Überschreibungen durch den Hilfeinhalts-Manager
Sie können das Standardverhalten von Help Viewer und von Hilfefunktionen der Visual Studio-IDE ändern. Einige Optionen werden durch Erstellen einer [PKGDEF](https://blogs.msdn.microsoft.com/visualstudio/2009/12/18/whats-a-pkgdef-and-why/)-Datei angegeben, um verschiedene Registrierungsschlüsselwerte festzulegen. Andere werden direkt in der Registrierung festgelegt.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Steuern des Help Viewer-Verhaltens mithilfe der PKGDEF-Datei

1. Erstellen Sie eine PKGDEF-Datei mit `[$RootKey$\Help]` als erste Zeile.

2. Fügen Sie beliebige oder alle Registrierungsschlüsselwerte in verschiedenen Zeilen hinzu, die in der Tabelle unten dargestellt sind, z.B. `“UseOnlineHelp”=dword:00000001`.

3. Kopieren Sie die Datei nach %ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<Edition\>\Common7\IDE\CommonExtensions.

4. Führen Sie `devenv /updateconfiguration` in einer Developer-Eingabeaufforderung aus.

### <a name="registry-key-values"></a>Registrierungsschlüsselwerte
|Registrierungsschlüsselwert|Typ|Daten|Beschreibung|  
|------------------|----|----|-----------|  
|NewContentAndUpdateService|string|\<HTTP-URL für den Dienstendpunkt\>|Definiert einen eindeutigen Dienstendpunkt|
|UseOnlineHelp|dword|`0`, um lokale Hilfe anzugeben, `1`, um Onlinehilfe anzugeben|Definiert die Online-oder Offlinehilfe (Standard)|
|OnlineBaseUrl|string|\<HTTP-URL für den Dienstendpunkt\>|Definiert einen eindeutigen F1-Endpunkt|
|OnlineHelpPreferenceDisabled|dword|`0` zum Aktivieren oder `1` zum Deaktivieren der Präferenzoptionen für die Onlinehilfe|Deaktiviert die Präferenzoption für die Onlinehilfe|
|DisableManageContent|dword|`0` zum Aktivieren oder `1` zum Deaktivieren der Registerkarte **Inhalt verwalten** in Help Viewer|Deaktiviert die Registerkarte „Inhalt verwalten“|
|DisableFirstRunHelpSelection|dword|`0` zum Aktivieren oder `1` zum Deaktivieren von Hilfefunktionen, die beim ersten Start von Visual Studio konfiguriert werden|Deaktiviert die Installation von Inhalt beim ersten Start von Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Beispielinhalt der PKGDEF-Datei
```
[$RootKey$\Help]
“NewContentAndUpdateService”=”https://some.service.endpoint”
“UseOnlineHelp”=dword:00000001
“OnlineBaseUrl”=”https://some.service.endpoint”
“OnlineHelpPreferenceDisabled”=dword:00000000
“DisableManageContent”=dword:00000000
“DisableFirstRunHelpSelection”=dword:00000001
```

## <a name="using-registry-editor-to-change-help-viewer-behavior"></a>Verwenden des Registrierungs-Editors zum Ändern des Help Viewer-Verhaltens
Die folgenden zwei Verhalten können durch Festlegen von Registrierungsschlüsselwerten im Registrierungs-Editor gesteuert werden.  
  
|Aufgabe|-Registrierungsschlüssel|Wert|Daten|  
|----------|-----|------|----|
|BITS-Auftragspriorität überschreiben|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3 (auf einem 64-Bit-Computer)|BITSPriority|**Vordergrund**, **hoch**, **regulär** oder **niedrig**|
|Auf den lokalen Inhaltsspeicher auf der Netzwerkfreigabe zeigen|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|
  
## <a name="see-also"></a>Siehe auch
[Help Viewer-Administratorhandbuch](../ide/help-viewer-administrator-guide.md)  
[Befehlszeilenargumente für den Hilfeinhalts-Manager](../ide/command-line-arguments-for-the-help-content-manager.md)  
[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)  
[Ändern von Isolated Shell mithilfe der PKGDEF-Datei](../extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)