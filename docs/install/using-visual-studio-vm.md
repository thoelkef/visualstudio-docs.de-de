---
title: Verwenden von Visual Studio auf einem virtuellen Azure-Computer
description: Erfahren Sie, wie Visual Studio auf einem virtuellen Azure-Computer verwendet wird
ms.date: 07/10/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 457953d161d6fd31c686199e76bdedbe548f5b8f
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38977712"
---
# <a id="top"> </a> Visual Studio-Images in Azure

Die Verwendung von Visual Studio in einem vorkonfigurierten virtuellen Azure-Computer (VM) ist eine einfache, schnelle Möglichkeit, von Null zu einer ausführbereiten Entwicklungsumgebung zu gelangen. Im [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps?search=%22visual%20studio%202017%22&page=1) stehen Systemimages mit verschiedenen Visual Studio-Konfigurationen zur Verfügung.

Neu bei Azure? [Kostenloses Azure-Konto erstellen](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Welche Konfigurationen und Versionen sind verfügbar?

Im Azure Marketplace finden Sie Images für die aktuellen Hauptversionen: Visual Studio 2017 und Visual Studio 2015. Für jede Hauptversion finden Sie die ursprünglich herausgegebene Version (RTW) und die zuletzt aktualisierten Versionen. Jede dieser Versionen ist in den Editionen Visual Studio Enterprise und Visual Studio Community erhältlich. Diese Images werden mindestens monatlich aktualisiert, sodass sie die neuesten Visual Studio- und Windows-Updates enthalten. Zwar bleiben die Namen der Images unverändert, die Beschreibung zu jedem Image beinhaltet aber dessen installierte Produktversion und das Statusdatum des Images.

| Releaseversion                                              | Editionen                     |     Produktversion     |
|:------------------------------------------------------------:|:----------------------------:|:-----------------------:|
| Visual Studio 2017: Aktuell (Version 15.7)                    |    Enterprise, Community     |      Version 15.7.5     |
| Visual Studio 2017: Die aktuelle Vorschauversion (Version 15.8, Vorschauversion 4) |    Enterprise, Community     |      Version 15.8.4     |
|         Visual Studio 2017: RTW                              |    Enterprise, Community     |      Version 15.0.15    |
|   Visual Studio 2015: Aktuell (Update 3)                      |    Enterprise, Community     |  Version 14.0.25431.01  |
|         Visual Studio 2015: RTW                              |             Keiner             | (Aus dem Wartungsfenster gelaufen) |

> [!NOTE]
> In Übereinstimmung mit der Microsoft-Wartungsrichtlinie ist die ursprünglich veröffentlichte Version (RTW) von Visual Studio 2015 aus dem Wartungsfenster gelaufen. Visual Studio 2015 Update 3 ist die einzig verbleibende Version, die für die Visual Studio 2015-Produktlinie angeboten wird.

Weitere Informationen finden Sie in der [Visual Studio-Wartungsrichtlinie](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Welche Funktionen sind installiert?

Jedes Image enthält die für die betreffende Visual Studio-Edition empfohlene Featuregruppe. Im Allgemeinen beinhaltet die Installation:

* Alle verfügbaren Workloads einschließlich der jeweils empfohlenen optionalen Komponenten
* .NET 4.6.2 und .NET 4.7 SDKs, Pakete zur Festlegung von Zielversionen und Entwicklertools
* Visual F#
* GitHub-Erweiterung für Visual Studio
* LINQ zu SQL-Tools

Wir verwenden beim Erstellen der Images folgende Befehlszeile zum Installieren von Visual Studio:

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Wenn die Images ein Visual Studio-Feature nicht enthalten, das Sie benötigen, geben Sie uns entsprechendes Feedback mithilfe des Feedbacktools in der oberen rechten Ecke der Seite.

## <a name="what-size-vm-should-i-choose"></a>Welche VM-Größe sollte gewählt werden?

Azure bietet eine umfangreiche Palette an VM-Größen. Da Visual Studio eine leistungsstarke Multithread-Anwendung ist, empfiehlt sich eine VM-Größe von mindestens zwei Prozessoren und 7 GB Arbeitsspeicher. Die folgenden VM-Größen werden für die Visual Studio-Images empfohlen:

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Weitere Informationen zu den aktuellen Computergrößen finden Sie unter [Größen für virtuelle Windows-Computer in Azure](/azure/virtual-machines/windows/sizes).

Bei Azure können Sie Ihre ursprüngliche Wahl neu ausbalancieren, indem Sie die Größe der VM ändern. Sie können entweder eine neue VM mit einer passenderen Größe bereitstellen oder die Größe Ihrer vorhandenen VM gemäß anderer zugrundeliegender Hardware ändern. Weitere Informationen finden Sie unter [Ändern der Größe eines virtuellen Windows-Computers](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Wie geht es weiter, sobald der virtuelle Computer ausgeführt wird?

Visual Studio folgt dem „Bring-your-own-License“-Modell in Azure. Wie bei einer Installation auf eigener Hardware ist also einer der ersten Schritte die Lizenzierung Ihrer Visual Studio-Installation. Sie können Visual Studio auf zwei Arten entsperren:
- Melden Sie sich mit einem Microsoft-Konto an, das einem Visual Studio-Abonnement zugeordnet ist
- Entsperren Sie Visual Studio mit dem Product Key, den Sie bei Ihrem ursprünglichen Kauf erhalten haben

Weitere Informationen finden Sie unter [Anmelden bei Visual Studio](../ide/signing-in-to-visual-studio.md) und [Entsperren von Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Wie speichere ich die Entwicklungs-VM für die zukünftige oder Teamnutzung?

Die Bandbreite von Entwicklungsumgebungen ist riesig, und der Ausbau der komplexeren Umgebungen stellt einen echten Kostenfaktor dar. Sie können Ihren konfigurierten virtuellen Computer unabhängig von Ihrer Umgebungskonfiguration für die zukünftige Verwendung oder für andere Mitglieder Ihres Teams als „Basisimage“ speichern oder erfassen. Wenn Sie dann einen neuen virtuellen Computer starten, stellen Sie ihn von diesem Basisimage statt vom Marketplace-Image aus bereit.

Kurz zusammengefasst: Verwenden Sie das Systemvorbereitungstool (Sysprep), fahren Sie den virtuellen Computer herunter, und erfassen Sie den virtuellen Computer *(Abbildung 1)* als Image über die Benutzeroberfläche des Azure-Portals. Azure speichert die `.vhd`-Datei, die das Image enthält, in einem Speicherkonto Ihrer Wahl. Anschließend wird das neue Image als Imageressource in der Ressourcenliste Ihres Abonnements angezeigt.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Abbildung 1) Erfassen eines Images über die Benutzeroberfläche des Azure-Portals*</center>

Weitere Informationen finden Sie unter [Erstellen eines verwalteten Images eines generalisierten virtuellen Computers in Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Vergessen Sie nicht, Sysprep zu verwenden, um den virtuellen Computer vorzubereiten. Wenn Sie diesen Schritt auslassen, kann Azure keinen virtuellen Computer aus dem Image bereitstellen.

> [!NOTE]
> Es entstehen immer noch gewisse Kosten für die Speicherung der Images, aber diese inkrementellen Kosten können unbedeutend sein im Vergleich mit den Kosten für den Mehraufwand, die mit der Neuerstellung des virtuellen Computers von Grund auf für jede Person in Ihrem Team, die einen virtuellen Computer benötigt, entstehen. Beispielsweise kostet die Speicherung eines 127-GB-Images, das von Ihrem gesamten Team wiederverwendet werden kann, nur einige Euro pro Monat. Diese Kosten sind jedoch unbedeutend im Vergleich mit den Stunden, die jeder Mitarbeiter in den Ausbau und die Validierung eines ordnungsgemäß konfigurierten Entwicklungssystems für den eigenen Gebrauch investieren müsste.

Darüber hinaus ist für Ihre Entwicklungsaufgaben oder -technologien möglicherweise mehr Skalierbarkeit erforderlich – etwa in Form von Abwandlungen von Entwicklungskonfigurationen und mehreren Computerkonfigurationen. Sie können Azure DevTest Labs verwenden, um _Rezepte_ zu erstellen, mit denen sich die Konstruktion Ihres „goldenen Images“ automatisieren lässt. Sie können auch DevTest-Labs verwenden, um die Richtlinien für die ausgeführten virtuellen Computer Ihres Teams zu verwalten. [Verwenden von Azure DevTest Labs durch Entwickler](/azure/devtest-lab/devtest-lab-developer-lab) stellt die beste Quelle für weitere Informationen zu DevTest Labs dar.

## <a name="next-steps"></a>Nächste Schritte

Da Sie nun die vorkonfigurieren Visual Studio-Images kennen, besteht der nächste Schritt im Erstellen eines neuen virtuellen Computers:

* [Erstellen einer Windows-VM im Azure-Portal](/azure/virtual-machines/windows/quick-create-portal)
* [Übersicht über virtuelle Windows-Computer in Azure](/azure/virtual-machines/windows/overview)
