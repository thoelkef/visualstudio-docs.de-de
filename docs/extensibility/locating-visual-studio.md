---
title: Suchen von Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 08/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5623ea382266fdbcd59bbe57b71522a7a1f4a31e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="locating-visual-studio"></a>Suchen von Visual Studio

Beginnend mit Visual Studio 2017, können Sie mehrere Instanzen der gleichen Version oder sogar Edition installieren. Dies ist hilfreich, wenn Sie neue Funktionen auf dem primären Entwicklungscomputer Beibehaltung der vorherigen Installations in der Vorschau anzeigen möchten. Aufgrund dieser Änderungen ist keine Variablen oder eines Registrierungsschlüssels Wert der einzelnen-Umgebung, die Sie verwenden können, um eine Instanz zu suchen. Stattdessen können Sie eine [COM-Abfrage-API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) Instanzen auf Grundlage der Kriterien, die relevant für die Erweiterung gefunden.

Dies ist eine schnelle, nur-Lese API mit NuGet-Pakete für systemeigenen und verwalteten Code verfügbar.

| Code | Package |
| ---- | --- |
| Systemeigen | https://NuGet.org/Packages/Microsoft.VisualStudio.Setup.Configuration.native |
| Verwaltet | https://NuGet.org/Packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Sie können eine einzelne Instanz angegebenen einen Pfad oder den aktuellen Prozess suchen oder Auflisten aller Instanzen. Finden Sie unter [unsere Beispiele](https://github.com/Microsoft/vs-setup-samples) vollständige Beispiele zur Verwendung von Visual Studio zu suchen.

## <a name="tools"></a>Tools

Um Visual Studio und anderen Tools in Buildumgebungen, PowerShell-Skripts, Installationsprogrammen und Weitere Szenarien zu suchen, haben wir eine Anzahl von open-Source-Verwaltungstools, die können Sie direkt verwenden oder verteilen zusammen mit Ihren eigenen Skripts.

| Projekt | Beschreibung |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Einfach-systemeigen Datenbankinstanzen Kriterien wie z. B. Version ausführbare Datei oder eine Vorabversion, welches Produkt installiert ist und die arbeitsauslastung installiert sind. Unterstützt auch das Suchen von Visual Studio 2010 und neueren Versionen ist, obwohl weniger Informationen, die für Visual Studio-2017 neuere, und zurückgegeben wird. Finden Sie unter der [Wiki](https://github.com/Microsoft/vswhere/wiki) Beispiele. |
| [VSSetup-cmdlets](https://github.com/Microsoft/vssetup.powershell) | PowerShell-Cmdlets unterstützt 2.0 und neuere zurückzugeben, die umfassende Informationen als Objekte können Sie Instanzen, basierend auf den gleichen Kriterien als suchen _Vswhere_ und noch mehr Eigenschaften zu Instanzen zu ermitteln. Finden Sie unter der [Wiki](https://github.com/Microsoft/vssetup.powershell/wiki) Beispiele. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Sucht automatisch nach _VSIXInstaller_ und übergibt über die Befehlszeile zum Installieren einer _VSIX_ Datei. Dies kann in Installationsprogramme nützlich sein, die keine direkte Unterstützung für die Abfrage-APIs. Finden Sie unter der [Wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) Beispiele. |

## <a name="see-also"></a>Siehe auch

* [Änderungen an Visual Studio 2017-Setup](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
