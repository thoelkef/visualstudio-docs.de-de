---
title: Problembehandlung bei der Ermittlung der Vorlage in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 72663d56844fcc34164e9408ab14c8ead234683e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="troubleshooting-template-installation"></a>Problembehandlung bei der Vorlageninstallation

Wenn Sie Ihre Projekt- oder Elementvorlagen Bereitstellung Probleme auftreten, können Sie die diagnoseprotokollierung aktivieren.

1. Erstellen Sie eine Pkgdef-Datei im Ordner "Common7\IDE\CommonExtensions" für die Installation (z. B. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef), mit dem folgenden Inhalt:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Öffnen Sie "Developer-Eingabeaufforderung" für die Installation von in Windows Search gesucht, und führen `devenv /updateConfiguration`.

1. Starten Sie Visual Studio, und starten Sie die Dialogfenster des neues Projekt und neues Element zum Initialisieren der beiden Strukturen Vorlage. Das Protokoll für die Vorlage wird nun in **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (Instanceid entspricht die Installations-ID Ihrer Instanz von Visual Studio). Jede Vorlage Struktur Initialisierung fügt Einträge in dieses Protokoll.

Die Protokolldatei enthält die folgenden Spalten:

- **FullPathToTemplate**, dem hat die folgenden Werte:

    - 1 für die Manifest-basierte Bereitstellung

    - 0 für Datenträger-basierte Bereitstellung

- **TemplateFileName**

- Andere Vorlageneigenschaften

> [!NOTE]
> Um die Protokollierung deaktivieren möchten, entfernen Sie die Pkgdef-Datei, oder ändern Sie den Wert der `EnableTemplateDiscoveryLog` auf `dword:00000000`, und führen Sie `devenv /updateConfiguration` erneut aus.

## <a name="see-also"></a>Siehe auch

[Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](creating-custom-project-and-item-templates.md)