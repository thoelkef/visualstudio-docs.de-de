---
title: WhiteSource Bolt-Vorteil | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/11/2017
ms.topic: Get-Started-Article
description: Erfahren Sie, wie Sie das WhiteSource Bolt-Abonnement aktivieren, das in Ihrem Visual Studio-Abonnement enthalten ist.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a7c384a8bc4b84aea4982bd195b0d92820c68ecb
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542350"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt in Visual Studio-Abonnements

Bestimmen und schließen Sie Schwachstellen in Open-Source-Komponenten, und erzeugen Sie umfassende Bestands- und Lizenzberichte zu allen Open-Source-Komponenten in Ihrem Build. Einige Visual Studio-Abonnements bieten sechs Monate lang kostenlosen Zugriff.

## <a name="activation-steps"></a>Aktivierungsschritte

1.  Melden Sie sich unter [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) an, um Ihren WhiteSource Bolt-Vorteil zu aktivieren.

2.  Suchen Sie im Abschnitt „Tools“ die Kachel „WhiteSource“, und klicken Sie im unteren Bereich der Kachel mit den Vorteilen auf den Link **Code abrufen**.
    > [!div class="mx-imgBorder"]
    > ![Kachel des Vorteils „WhiteSource Bolt“](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Sie erhalten eine Benachrichtigung, die den Aktivierungscode anzeigt.  **Kopieren Sie den Code in die Zwischenablage**, und klicken Sie auf **Activate** (Aktivieren).
    > [!div class="mx-imgBorder"]
    > ![WhiteSource Bolt-Vorteil: Code](_img\vs-whitesource\vs-whitesource-code.png)

3.  Klicken Sie auf der WhiteSource-Webseite auf die Schaltfläche **Aktivieren**, und scrollen Sie zum Bereich **Activate your account** (Konto aktivieren) der Seite herunter.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource Bolt-Vorteil: Aktivierung](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  Im Abschnitt **Activate your account** (Konto aktivieren) der Seite werden Sie durch vier Schritte geführt:

    - [Installieren](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) Sie die WhiteSource Bolt-Erweiterung von Microsoft Visual Studio Marketplace. Wenn Sie nicht über die nötigen Berechtigungen zum Installieren von Erweiterungen verfügen, finden Sie weitere Informationen unter [Installieren kostenloser Erweiterungen für Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts).


    Klicken Sie auf die grüne Schaltfläche **Installieren**, wenn Sie Azure DevOps Services verwenden, oder auf die Schaltfläche **Herunterladen**, wenn Sie Team Foundation Server nutzen.  In diesem Beispiel verwenden wir Azure DevOps Services.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource-Vorteil: Erweiterung installieren](_img\vs-whitesource\vs-whitesource-download-install.png)

    - Wählen Sie als Nächstes das gewünschte Azure DevOps-Unternehmen aus, und klicken Sie auf **Bestätigen**.  (Wenn Sie Azure DevOps Services noch nicht eingerichtet haben, rufen Sie die Seite [Vorteile](https://my.visualstudio.com/benefits) auf, und aktivieren Sie Ihren Azure DevOps Services-Vorteil.)

    > [!div class="mx-imgBorder"]
    > ![WhiteSource-Vorteil: Konto bestätigen](_img\vs-whitesource\vs-whitesource-confirm-account.png)

    - Sie erhalten eine Bestätigung, dass die Erweiterung installiert wurde und einsatzbereit ist.  Klicken Sie auf **Los geht‘s**, um zur WhiteSource Bolt-Seite zurückzukehren und fortzufahren.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource-Vorteil: Installation abgeschlossen](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Öffnen Sie das Dashboard Ihres Azure DevOps-Projekts, klicken Sie auf das Menü **Azure Pipelines**, und wählen Sie **WhiteSource Bolt** aus.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource-Vorteil: Erweiterung hinzufügen](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. Fügen Sie den Aktivierungscode aus der Kachel „WhiteSource Bolt-Vorteil“ ein, und klicken Sie auf **Aktivieren**. Jeder Aktivierungscode kann nur für die Aktivierung eines Projekts verwendet werden.
    > [!div class="mx-imgBorder"]
    > ![WhiteSource Bolt-Vorteil: Aktivierungscode](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  Die Aktivierung ist nun abgeschlossen, und für Ihr Abonnement verbleiben 180 Tage.

8.  Sie müssen die WhiteSource Bolt-Erweiterung als einen der Buildschritte hinzufügen.  Dies wird in einem Video erläutert, das auf der Seite [WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) verfügbar ist.

9. Sobald Sie den Build ausgeführt haben, werden folgende umfassende Berichte und Dashboards automatisch generiert:
    - Dashboard „Sicherheitsrisiken“
    - Bericht zu Sicherheitsrisiken
    - Bericht zu veralteten Bibliotheken
    - Dashboard „Lizenzrisiken und Konformität“
    - Bericht zum Bestand

## <a name="eligibility"></a>Berechtigung

| Abonnementstufe                                                 |     Channels                                            | Vorteil                                                          | Erneuerbar?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard, Cloudabonnement mit jährlicher Laufzeit)   | VL, Azure, Retail, NFR ausgewählt<sup>1</sup> | 6 Monate       |  Ja          |
| Visual Studio Professional (Standard, Cloudabonnement mit jährlicher Laufzeit) | VL, Azure, Retail                                       | Nicht verfügbar                                                           |NA         |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Nicht verfügbar                                             |  NA         |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Nicht verfügbar                                              | NA         |
| Visual Studio Dev Essentials | NA  | Nicht verfügbar |NA |
| Visual Studio Enterprise, Visual Studio Professional (Cloudabonnement mit monatlicher Laufzeit) | Azure                                       | Nicht verfügbar                                                           |NA|

<sup>1</sup> *Umfasst: Microsoft Partner Network (Enterprise).  Umfasst nicht: Not for Resale (NFR), Visual Studio Industry Partner (VSIP), FTE, MCT Software & Services (Developer), BizSpark, Imagine, Microsoft Valued Partner (MVP), Region Director (RD), MCT Software & Services, Microsoft Partner Network (Professional).*

Sie wissen nicht genau, welches Abonnement Sie verwenden?  Stellen Sie eine Verbindung mit [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) her, um alle Abonnements anzuzeigen, die Ihrer E-Mail-Adresse zugewiesen sind. Wenn nicht alle Ihrer Abonnements angezeigt werden, sind möglicherweise einige Abonnements einer anderen E-Mail-Adresse zugewiesen.  Sie müssen sich mit der entsprechenden E-Mail-Adresse anmelden, um diese Abonnements anzuzeigen.

## <a name="support-resources"></a>Supportressourcen

-  Benötigen Sie Hilfe bei WhiteSource Bolt?  Chatten Sie unter https://www.whitesourcesoftware.com/vse_whitesource_bolt/ live mit einem Mitarbeiter von WhiteSource Bolt.
-  Wenn Sie Unterstützung bei Vertrieb, Abonnements, Konten und Abrechnung für Visual Studio-Abonnements benötigen, wenden Sie sich an den [Abonnementsupport](https://visualstudio.microsoft.com/subscriptions/support/) für Visual Studio.
-  Haben Sie Fragen zur Visual Studio-IDE, zu Azure DevOps Services oder zu anderen Visual Studio-Produkten oder -Diensten?  Besuchen Sie die [Visual Studio-Supportwebsite](https://visualstudio.microsoft.com/support/).