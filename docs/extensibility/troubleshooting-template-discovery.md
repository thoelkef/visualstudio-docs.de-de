---
title: Problembehandlung bei der vorlagenermittlung in Visual Studio | Microsoft-Dokumentation
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e84ff96381fb29a1728ad43df4ff558abd17243
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689837"
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

- [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](creating-custom-project-and-item-templates.md)