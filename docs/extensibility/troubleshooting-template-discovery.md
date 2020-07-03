---
title: Problembehandlung bei der Vorlagen Ermittlung in Visual Studio | Microsoft-Dokumentation
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5225c741206e6a43ff024a5f184404f1ac2bc63
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904493"
---
# <a name="troubleshooting-template-installation"></a>Problembehandlung der Vorlagen Installation

Wenn bei der Bereitstellung der Projekt-oder Element Vorlagen Probleme auftreten, können Sie die Diagnoseprotokollierung aktivieren.

::: moniker range="vs-2017"

1. Erstellen Sie eine pkgdef-Datei im Ordner *Common7\IDE\CommonExtensions* für die Installation. Beispiel: *c:\Programme (x86) \Microsoft Visual studio\2017\enterprise\common7\ide\commonextensions\enablepkgdeflogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Erstellen Sie eine pkgdef-Datei im Ordner *Common7\IDE\CommonExtensions* für die Installation. Beispiel: *c:\Programme (x86) \Microsoft Visual studio\2019\enterprise\common7\ide\commonextensions\enablepkgdeflogging.pkgdef*.

::: moniker-end

2. Fügen Sie der pkgdef-Datei Folgendes hinzu:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Öffnen Sie eine [Developer-Eingabeaufforderung](/dotnet/framework/tools/developer-command-prompt-for-vs) für die-Installation, und führen Sie aus `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Öffnen Sie Visual Studio, und starten Sie die Dialogfelder Neues Projekt und neues Element, um beide Vorlagen Strukturen zu initialisieren.

   Das Vorlagen Protokoll wird jetzt in **%LocalAppData%\microsoft\visualstudio\15.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** angezeigt (die InstanceId entspricht der Installations-ID Ihrer Instanz von Visual Studio). Jede Vorlagen Struktur Initialisierung fügt Einträge an dieses Protokoll an.

::: moniker-end

::: moniker range=">=vs-2019"

4. Öffnen Sie Visual Studio, und starten Sie die Dialogfelder **Neues Projekt** und **Neues Element** erstellen, um beide Vorlagen Strukturen zu initialisieren.

   Das Vorlagen Protokoll wird jetzt in **%LocalAppData%\microsoft\visualstudio\16.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** angezeigt (die InstanceId entspricht der Installations-ID Ihrer Instanz von Visual Studio). Jede Vorlagen Struktur Initialisierung fügt Einträge an dieses Protokoll an.

::: moniker-end

Die Protokolldatei enthält die folgenden Spalten:

- **Fullpathto Template**mit den folgenden Werten:

  - 1 für die manifestressourcenbasierte Bereitstellung

  - 0 für Datenträger basierte Bereitstellung

- **Templatefilename**

- Weitere Vorlagen Eigenschaften

> [!NOTE]
> Um die Protokollierung zu deaktivieren, entfernen Sie entweder die pkgdef-Datei, oder ändern Sie den Wert von `EnableTemplateDiscoveryLog` in `dword:00000000` , und führen Sie dann `devenv /updateConfiguration` erneut aus.

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefinierten Projekt-und Element Vorlagen](creating-custom-project-and-item-templates.md)
