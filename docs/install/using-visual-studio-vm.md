---
title: Verwenden von Visual Studio auf einem virtuellen Azure-Computer | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio auf einem virtuellen Azure-Computer verwendet wird
ms.date: 01/30/2018
ms.technology: vs-acquisition
ms.topic: article
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: phillee
manager: sacalla
ms.workload:
- multiple
ms.openlocfilehash: d8e99965867d5dbc2710d6c56c5b3dc90fc16dc8
ms.sourcegitcommit: 4b4027244b8de25e30b533148804b87321d3e8a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2018
---
# <a id="top"> </a> Visual Studio-Images in Azure
Die Verwendung von Visual Studio in einem vorkonfigurierten virtuellen Azure-Computer (VM) stellt die einfachste und schnellste Möglichkeit dar, von Null zu einer ausführbereiten Entwicklungsumgebung zu gelangen.  Im [Azure Marketplace](https://portal.azure.com/) stehen Systemimages mit verschiedenen Visual Studio-Konfigurationen zur Verfügung. Starten Sie einfach einen virtuellen Computer, und schon können Sie loslegen.

Neu bei Azure? [Kostenloses Azure-Konto erstellen](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Welche Konfigurationen und Versionen sind verfügbar?
Im Azure Marketplace finden Sie Images für die aktuellsten Hauptversionen: Visual Studio 2017 und Visual Studio 2015.  Für jede Hauptversion finden Sie die ursprünglich veröffentlichte Version (auch als "RTW" bezeichnet) und die „neuesten“ aktualisierten Versionen.  Jede dieser verschiedenen Versionen ist in den Editionen Visual Studio Enterprise und Visual Studio Community erhältlich.  Wir aktualisieren diese Images mindestens jeden Monat, sodass sie die neuesten Visual Studio- und Windows-Updates enthalten.  Zwar bleiben die Namen der Images unverändert, die Beschreibung zu jedem Image beinhaltet aber dessen installierte Produktversion und das Statusdatum des Images.

|               Releaseversion              |        Editionen       |     Produktversion     |
|:------------------------------------------:|:---------------------:|:-----------------------:|
| Visual Studio 2017 – neueste (Version 15.5) | Enterprise, Community |      Version 15.5.3     |
|         Visual Studio 2017 – RTW           | Enterprise, Community |      Version 15.0.7     |
|   Visual Studio 2015 – neueste (Update 3)   | Enterprise, Community |  Version 14.0.25431.01  |
|         Visual Studio 2015 – RTW           |         Keiner          | (Aus dem Wartungsfenster gelaufen) |

> [!NOTE]
> In Übereinstimmung mit der Microsoft-Wartungsrichtlinie sind die ursprünglich veröffentlichten Versionen (die „RTW“-Versionen) von Visual Studio 2015 aus dem Wartungsfenster gelaufen.  Daher ist Visual Studio 2015 Update 3 die einzig verbleibende Version, die für die Visual Studio 2015-Produktlinie angeboten wird.

Weitere Informationen finden Sie in der [Visual Studio-Wartungsrichtlinie](https://www.visualstudio.com/en-us/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Welche Funktionen sind installiert?
Jedes Image enthält die für die betreffende Visual Studio-Edition empfohlene Featuregruppe.  Im Allgemeinen beinhaltet die Installation:

* Alle verfügbaren Workloads einschließlich der empfohlenen optionalen Komponenten für den betreffenden Workflow
* .NET 4.6.2 und .NET 4.7 SDKs, Pakete zur Festlegung von Zielversionen und Entwicklertools
* Visual F#
* GitHub-Erweiterung für Visual Studio
* LINQ zu SQL-Tools

Dies ist die Befehlszeile, die wir beim Erstellen der Images zum Installieren von Visual Studio verwenden:

```
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       add Microsoft.Net.Component.4.7.SDK ^
       add Microsoft.Net.Component.4.7.TargetingPack ^ 
       add Microsoft.Net.Component.4.6.2.SDK ^
       add Microsoft.Net.Component.4.6.2.TargetingPack ^
       add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       add Microsoft.VisualStudio.Component.FSharp ^
       add Component.GitHub.VisualStudio ^
       add Microsoft.VisualStudio.Component.LinqToSql
```

Wenn die Images ein Visual Studio-Feature nicht enthalten, das Sie benötigen, geben Sie uns entsprechendes Feedback mithilfe des Feedbacktools (obere rechte Ecke der Seite).

## <a name="what-size-vm-should-i-choose"></a>Welche VM-Größe sollte gewählt werden?
Das Bereitstellen eines neuen virtuellen Computers ist einfach, und Azure bietet die gesamte Bandbreite der VM-Größen.  Wie bei jeder Hardwareanschaffung ist es sinnvoll, die Leistung gegenüber den Kosten abzuwägen.  Da Visual Studio eine leistungsstarke Multithread-Anwendung ist, empfiehlt sich eine VM-Größe, die mindestens 2 Prozessoren und 7 GB Arbeitsspeicher enthält. In Azure übersetzt sich das in diese VM-Mindestgrößen:

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Weitere Informationen zu den aktuellen Computergrößen finden Sie unter [Größen für virtuelle Windows-Computer in Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes).

Bei Azure sind Sie nicht auf Ihre erste Wahl festgelegt – Sie können Ihre ursprüngliche Lösung neu ausbalancieren, indem Sie die Größe der VM ändern.  Sie können entweder eine neue VM mit einer passenderen Größe bereitstellen oder die Größe Ihrer vorhandenen VM auf anderer zugrundeliegender Hardware ändern.  Weitere Informationen finden Sie unter [Ändern der Größe eines virtuellen Windows-Computers](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/resize-vm).

## <a name="after-i-get-the-vm-running-then-what"></a>Wie geht es weiter, nachdem der virtuelle Computer ausgeführt wird?
Visual Studio folgt in Azure dem Modell „bringen Sie Ihre eigene Lizenz mit“ (bring your own license).  Ähnlich wie bei einer Installation auf eigener Hardware besteht also einer der ersten Schritte in der Lizenzierung Ihrer Visual Studio-Installation.  Sie können Visual Studio entsperren, indem Sie sich entweder mit einem Microsoft-Konto anmelden, das einem Visual Studio-Abonnement zugeordnet ist, oder Sie entsperren Visual Studio mit dem Product Key von Ihrem ursprünglichen Kauf.  Weitere Informationen finden Sie unter [Anmelden bei Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/signing-in-to-visual-studio) und [Entsperren von Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-unlock-visual-studio).

## <a name="after-i-build-out-the-dev-vm-how-do-i-save-capture-it-for-future-or-team-use"></a>Wie speichere (erfasse) ich den virtuellen Entwicklungscomputer nach dem Ausbau für die zukünftige Verwendung oder die Verwendung durch ein Team?

Die Bandbreite von Entwicklungsumgebungen ist riesig, und der Ausbau der komplexeren Umgebungen stellt einen echten Kostenfaktor dar.  Unabhängig von der Konfiguration Ihrer Umgebung macht Azure es Ihnen aber leicht, diese Investition zu schützen, indem es Ihren perfekt konfigurierten virtuellen Computer als Basisimage für Ihre zukünftige Nutzung speichert/erfasst – für Sie selbst und/oder für andere Mitglieder Ihres Teams.  Stellen Sie einen neuen virtuellen Computer beim Starten aus diesem Basisimage anstelle des Marketplace-Images bereit.

Kurz zusammengefasst besteht der Vorgang im Ausführen von sysprep, gefolgt vom Herunterfahren des virtuellen Computers und seinem anschließenden *Erfassen (Abbildung 1)* als Image über die Benutzeroberfläche des Azure-Portals.  Azure speichert die `.vhd`-Datei, die das Image enthält, in einem Speicherkonto Ihrer Wahl.  Anschließend wird das neue Image als Image-Ressource in der Ressourcenliste Ihres Abonnements angezeigt.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Abbildung 1) Erfassen eines Images mithilfe der Benutzeroberfläche des Azure-Portals.*</center>

Weitere Informationen finden Sie unter[Erstellen eines verwalteten Images eines generalisierten virtuellen Computers in Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource).

  **Hinweis:** Vergessen Sie nicht, sysprep für den virtuellen Computer auszuführen!  Wenn Sie diesen Schritt auslassen, kann Azure keinen virtuellen Computer aus dem Image bereitstellen.

> [!NOTE]
> Es entstehen immer noch gewisse Kosten für die Speicherung des/der Images, aber diese inkrementellen Kosten sind vermutlich unbedeutend im Vergleich mit den Arbeitskosten, die mit der Neuerstellung des virtuellen Computers von Grund auf entstehen – für jede Person in Ihrem Team, die einen virtuellen Computer benötigt.  Beispielsweise kostet die Speicherung eines 127-GB-Images, das von allen Mitgliedern Ihres Teams wiederverwendet werden kann, nur einige Euro pro Monat.  Diese Kosten sind jedoch unbedeutend im Vergleich mit den Stunden, die jeder Mitarbeiter in den Ausbau und die Validierung eines ordnungsgemäß konfigurierten Entwicklungssystems für den eigenen Gebrauch investieren müsste.

Darüber hinaus ist für Ihre Entwicklungsaufgaben oder -technologien möglicherweise mehr Skalierbarkeit erforderlich – etwa in Form von Abwandlungen von Entwicklungskonfigurationen und mehreren Computerkonfigurationen.  Sie können Azure DevTest Labs verwenden, um _Rezepte_ zu erstellen, mit denen sich die Konstruktion Ihres „goldenen Images“ automatisieren lässt und die Richtlinien für die ausgeführten virtuellen Computer Ihres Teams verwalten lassen.  [Verwenden von Azure DevTest Labs durch Entwickler](https://docs.microsoft.com/en-us/azure/devtest-lab/devtest-lab-developer-lab) stellt die beste Quelle für weitere Informationen zu DevTest Labs dar.

## <a name="next-steps"></a>Nächste Schritte
Jetzt, da Sie die vorkonfigurieren Visual Studio-Images kennen, besteht der nächste Schritt im Erstellen eines neuen virtuellen Computers:

* [Erstellen einer Windows-VM im Azure-Portal](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)
* [Übersicht über virtuelle Windows-Computer in Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/overview)
