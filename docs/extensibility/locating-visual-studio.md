---
title: Finden von Visual Studio | Microsoft-Dokumentation
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c13146d0d48dc176417040bcb756bf8069ad3c3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907308"
---
# <a name="locate-visual-studio"></a>Suchen Sie Visual Studio

Ab Visual Studio 2017, können Sie mehrere Instanzen der gleichen Version oder sogar Edition installieren. Dies ist hilfreich, wenn Sie neue Funktionen auf dem primären Entwicklungscomputer Vorschau anzeigen, während die vorherige Installation beibehalten möchten. Aufgrund dieser Änderungen müssen Sie kein Variablen oder eines Registrierungsschlüssels Wert der einzigen Umgebung, die Sie verwenden können, finden Sie eine Instanz vorhanden ist. Sie können stattdessen eine [COM-Abfrage-API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) Instanzen basierend auf Kriterien, die relevant für Ihre Erweiterung zu finden.

Dies ist eine schnelle, nur-Lese API mit NuGet-Pakete für systemeigenen und verwalteten Code verfügbar.

| Code | Package |
| ---- | --- |
| Systemeigen | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Verwaltet | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Sie können eine einzelne Instanz erhalten einen Pfad oder den aktuellen Prozess suchen oder alle Instanzen aufgelistet. Finden Sie unter [unserer Beispiele](https://github.com/Microsoft/vs-setup-samples) für vollständige Beispiele für Visual Studio zu suchen.

## <a name="tools"></a>Tools

Um Visual Studio und anderen Tools in Buildumgebungen, PowerShell-Skripts, Installationsprogramme und weitere Szenarios zu finden, gibt es eine Reihe von Open-Source-Tools, die können Sie direkt verwenden oder verteilen, die zusammen mit Ihren eigenen Skripts.

| Projekt | Beschreibung |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Einzeldatei-Native ausführbare Instanzen erfüllt die Kriterien wie z. B. Version gefunden oder Vorabversion, welches Produkt installiert ist und welche Workloads installiert sind. Unterstützt auch das Visual Studio 2010 und neueren, suchen, obwohl weniger Informationen mit, die für Visual Studio 2017 und höher zurückgegeben wurde. Finden Sie unter den [Wiki](https://github.com/Microsoft/vswhere/wiki) Beispiele. |
| [VSSetup-cmdlets](https://github.com/Microsoft/vssetup.powershell) | PowerShell-Cmdlets unterstützt 2.0 und höher, die umfassende Informationen können Sie Instanzen basierend auf den gleichen Kriterien wie als Objekte zurückgeben _Vswhere_ und sogar noch mehr Eigenschaften zu Instanzen zu ermitteln. Finden Sie unter den [Wiki](https://github.com/Microsoft/vssetup.powershell/wiki) Beispiele. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Sucht automatisch nach _VSIX-Installationsprogramm_ und übergibt Sie der Befehlszeile durch Installieren einer **VSIX* Datei. Diese Funktion kann in Installationsprogramme nützlich sein, die keine direkte Unterstützung für die Abfrage-APIs haben. Finden Sie unter den [Wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) Beispiele. |

## <a name="see-also"></a>Siehe auch

* [Änderungen an Visual Studio 2017-setup](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
