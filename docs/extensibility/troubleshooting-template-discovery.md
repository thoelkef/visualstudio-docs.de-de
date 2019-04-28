---
title: Problembehandlung bei der vorlagenermittlung in Visual Studio | Microsoft-Dokumentation
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1ea74d3c5f3fed961a956e9a55a4930d009d530
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62432082"
---
# <a name="troubleshooting-template-installation"></a>Problembehandlung bei der Vorlageninstallation

Wenn Sie Ihre Projekt- oder Elementvorlagen Bereitstellung Probleme auftreten, können Sie die diagnoseprotokollierung aktivieren.

::: moniker range="vs-2017"

1. Erstellen Sie eine Pkgdef-Datei in die *Common7\IDE\CommonExtensions* Ordner für die Installation. Z. B. *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Erstellen Sie eine Pkgdef-Datei in die *Common7\IDE\CommonExtensions* Ordner für die Installation. Z. B. *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Fügen Sie Folgendes, um die Pkgdef-Datei:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Öffnen einer [Developer-Eingabeaufforderung](/dotnet/framework/tools/developer-command-prompt-for-vs) für die Installation und Ausführung `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Öffnen Sie Visual Studio, und starten Sie die neue Projekt- und neue Dialogfelder zum Initialisieren der beiden Bäumen Vorlage.

   Das Protokoll für die Vorlage wird nun in **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (Instanz-ID entspricht der Installations-ID der Instanz von Visual Studio). Jede Vorlage Struktur Initialisierung fügt Einträge in dieses Protokoll.

::: moniker-end

::: moniker range=">=vs-2019"

4. Öffnen Sie Visual Studio, und starten Sie den **Erstellen eines neuen Projekts** und **neues Element** Dialogfelder, um die beiden Bäumen Vorlage zu initialisieren.

   Das Protokoll für die Vorlage wird nun in **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (Instanz-ID entspricht der Installations-ID der Instanz von Visual Studio). Jede Vorlage Struktur Initialisierung fügt Einträge in dieses Protokoll.

::: moniker-end

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