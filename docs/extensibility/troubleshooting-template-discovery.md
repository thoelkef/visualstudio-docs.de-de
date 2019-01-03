---
title: Problembehandlung bei der vorlagenermittlung in Visual Studio | Microsoft-Dokumentation
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39ebb7c49e5a8482ab0b2ef5c3a5257d0237b39c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836152"
---
# <a name="troubleshooting-template-installation"></a>Problembehandlung bei der Vorlageninstallation

Wenn Sie Ihre Projekt- oder Elementvorlagen Bereitstellung Probleme auftreten, können Sie die diagnoseprotokollierung aktivieren.

1. Erstellen Sie eine Pkgdef-Datei im Ordner "Common7\IDE\CommonExtensions" für die Installation (z. B. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef), mit dem folgenden Inhalt:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Öffnen Sie eine Developer-Eingabeaufforderung "für die Installation nach einer Suche in der Windows-Suche, und führen `devenv /updateConfiguration`.

1. Starten Sie Visual Studio, und starten Sie die Dialogfeldern "Neues Projekt und neues Element" zum Initialisieren der beiden Bäumen Vorlage. Das Protokoll für die Vorlage wird nun in **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (Instanz-ID entspricht der Installations-ID der Instanz von Visual Studio). Jede Vorlage Struktur Initialisierung fügt Einträge in dieses Protokoll.

Die Protokolldatei enthält die folgenden Spalten:

- **FullPathToTemplate**, der hat die folgenden Werte:

    - 1 für die Manifest-basierte Bereitstellung

    - 0 für die Datenträger-basierte Bereitstellung

- **TemplateFileName**

- Andere Eigenschaften

> [!NOTE]
> Um die Protokollierung deaktivieren möchten, entfernen Sie die Pkgdef-Datei, oder ändern Sie den Wert der `EnableTemplateDiscoveryLog` zu `dword:00000000`, und führen Sie dann `devenv /updateConfiguration` erneut aus.

## <a name="see-also"></a>Siehe auch

[Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](creating-custom-project-and-item-templates.md)