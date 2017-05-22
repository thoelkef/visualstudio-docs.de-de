---
title: "Installieren von Visual Studio in Umgebungen mit niedriger Bandbreite oder unzuverlässigem Netzwerk | Microsoft-Dokumentation"
description: "Beschreibt die Funktionsweise des Visual Studio-Installationsprogramms in Umgebungen mit unzuverlässigem Netzwerk und erläutert das Herunterladen von Installationsdateien vor dem Starten der Installation."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 9dbe70bce6c246416df64de304b06cd211320f2a
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Installieren von Visual Studio 2017 in Umgebungen mit niedriger Bandbreite oder unzuverlässigem Netzwerk
Wir haben das neue Visual Studio 2017-Installationsprogramm so gestaltet, dass es bei einer Vielzahl von Netzwerk- und Computerbedingungen gut funktioniert.

- Die Dateien, die Sie für die Installation von Visual Studio benötigen, werden an ein globales Übermittlungsnetzwerk verteilt, sodass Sie sie von einem lokalen Server abrufen können.
- Währen des Installationsvorgangs probieren wir drei Downloadtechnologien (WebClient, BITS und WinInet) aus, um Störungen durch Antiviren- und Proxysoftware zu minimieren.
- Das neue workloadbasierte Modell bedeutet, dass Sie weniger installieren müssen als bei früheren Versionen von Visual Studio.

Aus diesem Grund empfehlen wir Ihnen, den neuen Webinstaller auszuprobieren, der Ihnen bestimmt gefallen wird. Doch wenn Sie sicher sein möchten, dass die Installationsdateien vor dem Start der Installation von Visual Studio erfolgreich heruntergeladen wurden, stehen wir Ihnen zur Seite. Sie können über die Befehlszeile einen lokalen Cache der Dateien erstellen, die Sie vor Beginn der Installation benötigen.

Gehen Sie folgendermaßen vor:

## <a name="download-the-visual-studio-bootstrapper"></a>Herunterladen des Visual Studio-Bootstrappers
Beginnen Sie mit dem Herunterladen des Visual Studio-Bootstrappers für die ausgewählte Edition von Visual Studio.

Ihre Setupdatei, &mdash;oder genauer gesagt eine Bootstrapperdatei &mdash;, entspricht einer der folgenden.

| Edition                    | Datei                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio-Community    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>Erstellen eines lokalen Installationscaches
Zum Erstellen eines lokalen Layouts öffnen Sie eine Eingabeaufforderung, und rufen einen der Befehle in den folgenden Beispielen auf. Bei den hier aufgeführten Beispiele wird davon ausgegangen, dass Sie den Visual Studio Community-Bootstrapper heruntergeladen haben. Passen Sie den Befehl nach Bedarf für Ihre Edition an.

- Führen Sie für die .NET-Web- und .NET-Desktopentwicklung Folgendes aus:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
  ```
- Führen Sie für die .NET-Desktop- und Office-Entwicklung Folgendes aus:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
  ```
- Führen Sie für die C++-Desktopentwicklung Folgendes aus:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
  ```

- Führen Sie zum Erstellen eines vollständigen lokalen Layouts mit alle Features (was lange dauert, weil wir _sehr viele_ Features bieten!) Folgendes aus:
  ```
  vs_community.exe --layout c:\vs2017layout --lang en-US
  ```

Wenn Sie eine andere Sprache als Englisch installieren möchten, ändern Sie `en-US` in ein Gebietsschema in der Liste am unteren Rand dieser Seite. Verwenden Sie diese [Liste verfügbarer Komponenten und Workloads](workload-and-component-ids.md), um bei Bedarf Ihren Installationscache weiter anzupassen.

## <a name="install-from-the-local-cache"></a>Installieren aus dem lokalen Cache
Wenn eine Installation aus einem lokalen Installationscache erfolgt, verwenden wir die lokalen Versionen aller dieser Dateien. Doch wenn Sie während der Installation Komponenten auswählen, die sich nicht im Cache befinden, versuchen wir, diese aus dem Internet herunterzuladen.

Um sicherzustellen, dass Sie nur die Dateien installieren, die Sie heruntergeladen haben, verwenden Sie dieselben Befehlszeilenoptionen, die Sie zum Erstellen des Layoutcaches verwendet haben. Wenn Sie z. B. einen Layoutcache mit dem folgenden Befehl erstellt haben:

```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Verwenden Sie diesen Befehl, um die Installation auszuführen:

```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>Liste der Gebietsschemas
| **Gebietsschema** | **Sprache** |
| ----------------------- | --------------- |  
| cs-CZ | Tschechisch |
| de-DE | Deutsch |
| en-US | Englisch |
| es-ES | Spanisch |
| fr-FR | Französisch |
| it-IT | Italienisch |
| ja-JP | Japanisch |
| ko-KR | Koreanisch |
| pl-PL | Polnisch |
| pt-BR | Portugiesisch (Brasilien) |
| ru-RU | Russisch |
| tr-TR | Türkisch |
| zh-CN | Chinesisch (vereinfacht) |
| zh-TW | Chinesisch (traditionell) |

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

