---
title: Überschreibungen durch den Hilfeinhalts-Manager
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b881ee7a782d7c5f90a447c1719bb88afd1d332
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56314597"
---
# <a name="help-content-manager-overrides"></a>Überschreibungen durch den Hilfeinhalts-Manager

Sie können das Standardverhalten von Help Viewer und der Hilfefeatures der Visual Studio-IDE ändern. Einige Optionen werden durch Erstellen einer [PKGDEF](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)-Datei angegeben, um verschiedene Registrierungsschlüsselwerte festzulegen. Andere werden direkt in der Registrierung festgelegt.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Steuern des Help Viewer-Verhaltens mithilfe der PKGDEF-Datei

1. Erstellen Sie eine *PKGDEF-Datei* mit `[$RootKey$\Help]` als erste Zeile.

2. Fügen Sie beliebige oder alle Registrierungsschlüsselwerte in verschiedenen Zeilen hinzu, die in der Tabelle unten dargestellt sind, z.B. `"UseOnlineHelp"=dword:00000001`.

3. Kopieren Sie die Datei nach *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<Edition\>\Common7\IDE\CommonExtensions*.

4. Führen Sie `devenv /updateconfiguration` in einer Developer-Eingabeaufforderung aus.

### <a name="registry-key-values"></a>Registrierungsschlüsselwerte

|Registrierungsschlüsselwert|Typ|Daten|Beschreibung|
|------------------|----|----|-----------|
|NewContentAndUpdateService|string|\<HTTP-URL für den Dienstendpunkt\>|Definiert einen eindeutigen Dienstendpunkt|
|UseOnlineHelp|dword|`0`, um lokale Hilfe anzugeben, `1`, um Onlinehilfe anzugeben|Definiert die Online-oder Offlinehilfe (Standard)|
|OnlineBaseUrl|string|\<HTTP-URL für den Dienstendpunkt\>|Definiert einen eindeutigen F1-Endpunkt|
|OnlineHelpPreferenceDisabled|dword|`0` zum Aktivieren oder `1` zum Deaktivieren der Präferenzoptionen für die Onlinehilfe|Deaktiviert die Präferenzoption für die Onlinehilfe|
|DisableManageContent|dword|`0` zum Aktivieren oder `1` zum Deaktivieren der Registerkarte **Inhalt verwalten** in Help Viewer|Deaktiviert die Registerkarte **Inhalt verwalten**|
|DisableFirstRunHelpSelection|dword|`0` zum Aktivieren oder `1` zum Deaktivieren von Hilfefunktionen, die beim ersten Start von Visual Studio konfiguriert werden|Deaktiviert die Installation von Inhalt beim ersten Start von Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Beispielinhalt der PKGDEF-Datei

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Verwenden des Registrierungs-Editors zum Ändern des Help Viewer-Verhaltens

Die folgenden zwei Verhalten können durch Festlegen von Registrierungsschlüsselwerten im Registrierungs-Editor gesteuert werden.

|Aufgabe|-Registrierungsschlüssel|Wert|Daten|
|----------|-----|------|----|
|BITS-Auftragspriorität überschreiben|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3 (auf einem 64-Bit-Computer)|BITSPriority|**Vordergrund**, **hoch**, **regulär** oder **niedrig**|
|Auf den lokalen Inhaltsspeicher auf der Netzwerkfreigabe zeigen|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Siehe auch

- [Help Viewer-Administratorleitfaden](../help-viewer/administrator-guide.md)
- [Befehlszeilenargumente für den Hilfeinhalts-Manager](../help-viewer/command-line-arguments.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)