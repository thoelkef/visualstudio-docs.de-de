---
title: Fehlerbehebung bei der Vorlagenermittlung in Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698932"
---
# <a name="troubleshooting-template-installation"></a>Fehlerbehebung bei der Installation von Vorlagen

Wenn bei der Bereitstellung Ihrer Projekt- oder Elementvorlagen Probleme auftreten, können Sie die Diagnoseprotokollierung aktivieren.

::: moniker range="vs-2017"

1. Erstellen Sie eine pkgdef-Datei im Ordner *Common7-IDE-CommonExtensions* für Ihre Installation. Zum *Beispiel: C:-Programmdateien (x86) , Microsoft Visual Studio, 2017, Enterprise, Common7, IDE, CommonExtensions, EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Erstellen Sie eine pkgdef-Datei im Ordner *Common7-IDE-CommonExtensions* für Ihre Installation. Zum *Beispiel: C:-Programmdateien (x86) , Microsoft Visual Studio, 2019, Enterprise, Common7, IDE, CommonExtensions, EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Fügen Sie der datei pkgdef Folgendes hinzu:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Öffnen Sie eine [Entwicklereingabeaufforderung](/dotnet/framework/tools/developer-command-prompt-for-vs) `devenv /updateConfiguration`für Ihre Installation und Ausführung .

::: moniker range="vs-2017"

4. Öffnen Sie Visual Studio, und starten Sie die Dialogfelder "Neues Projekt" und "Neues Element", um beide Vorlagenstrukturen zu initialisieren.

   Das Vorlagenprotokoll wird jetzt in **%LOCALAPPDATA%-Microsoft-VisualStudio-15.0_[instanceid]-VsTemplateDiagnosticsList.csv** (Instanceid entspricht der Installations-ID Ihrer Instanz von Visual Studio). Jede Vorlagenbauminitialisierung fügt Einträge an dieses Protokoll an.

::: moniker-end

::: moniker range=">=vs-2019"

4. Öffnen Sie Visual Studio, und starten Sie die Dialogfelder **Erstellen eines neuen Projekts** und Neuer **Artikel,** um beide Vorlagenstrukturen zu initialisieren.

   Das Vorlagenprotokoll wird jetzt in **%LOCALAPPDATA%-Microsoft-VisualStudio-16.0_[instanceid]-VsTemplateDiagnosticsList.csv** (Instanceid entspricht der Installations-ID Ihrer Instanz von Visual Studio). Jede Vorlagenbauminitialisierung fügt Einträge an dieses Protokoll an.

::: moniker-end

Die Protokolldatei enthält die folgenden Spalten:

- **FullPathToTemplate**, die die folgenden Werte hat:

  - 1 für die manifestbasierte Bereitstellung

  - 0 für die datenträgerbasierte Bereitstellung

- **TemplateFileName**

- Andere Vorlageneigenschaften

> [!NOTE]
> Um die Protokollierung zu deaktivieren, entfernen Sie entweder `EnableTemplateDiscoveryLog` `dword:00000000`die pkgdef-Datei, oder ändern Sie den Wert von in , und führen Sie dann erneut aus. `devenv /updateConfiguration`

## <a name="see-also"></a>Weitere Informationen

- [Erstellen benutzerdefinierter Projekt- und Elementvorlagen](creating-custom-project-and-item-templates.md)
