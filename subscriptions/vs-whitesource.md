---
title: WhiteSource Bolt-Vorteil | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 12/19/2018
ms.topic: Get-Started-Article
description: Erfahren Sie, wie Sie das WhiteSource Bolt-Abonnement aktivieren, das in Ihrem Visual Studio-Abonnement enthalten ist.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: d9f4db463dad3ee2fbb216284791018dc504d7b6
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739983"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt in Visual Studio-Abonnements

Bestimmen und schließen Sie Schwachstellen in Open-Source-Komponenten, und erzeugen Sie umfassende Bestands- und Lizenzberichte zu allen Open-Source-Komponenten in Ihrem Build. Einige Visual Studio-Abonnements bieten sechs Monate lang kostenlosen Zugriff.

## <a name="activation-steps"></a>Aktivierungsschritte

1. Melden Sie sich unter [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) an, um Ihren WhiteSource Bolt-Vorteil zu aktivieren.

2. Suchen Sie im Abschnitt „Tools“ die Kachel „WhiteSource“, und klicken Sie im unteren Bereich der Kachel mit den Vorteilen auf den Link **Code abrufen**.
   > [!div class="mx-imgBorder"]
   > ![Kachel des Vorteils „WhiteSource Bolt“](_img/vs-whitesource/vs-whitesource-tile.png)

3. Sie erhalten eine Benachrichtigung, die den Aktivierungscode anzeigt.  **Kopieren Sie den Code in die Zwischenablage**, und klicken Sie auf **Activate** (Aktivieren).
   > [!div class="mx-imgBorder"]
   > ![WhiteSource Bolt-Vorteil: Code](_img/vs-whitesource/vs-whitesource-code.png)

4. Klicken Sie auf der WhiteSource-Webseite auf die Schaltfläche **Aktivieren**, und scrollen Sie zum Bereich **Activate your account** (Konto aktivieren) der Seite herunter.
   > [!div class="mx-imgBorder"]
   > ![WhiteSource Bolt-Vorteil: Aktivierung](_img/vs-whitesource/vs-whitesource-activate-page-cropped.png)

5. Im Abschnitt **Activate your account** (Konto aktivieren) der Seite werden Sie durch vier Schritte geführt:

   - [Installieren](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) Sie die WhiteSource Bolt-Erweiterung von Microsoft Visual Studio Marketplace. Wenn Sie nicht über die nötigen Berechtigungen zum Installieren von Erweiterungen verfügen, finden Sie weitere Informationen unter [Installieren kostenloser Erweiterungen für Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts).


~~~
Click the green **Install** button if you are using Azure DevOps Services, or the **Download** button for Team Foundation Server.  For this example, we will use Azure DevOps Services.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Extension](_img\vs-whitesource\vs-whitesource-download-install.png)

- Next, select the Azure DevOps organization you want to use and click **Confirm**.  (If you have not yet set up Azure DevOps Services, visit the [Benefits](https://my.visualstudio.com/benefits) page and activate your Azure DevOps Services benefit.)

> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Confirm Account](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- You’ll receive a confirmation that the extension is installed and ready to use.  Click **Get started** to return to the WhiteSource Bolt page and continue.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Complete](_img\vs-whitesource\vs-whitesource-install-complete.png)
~~~

5. Öffnen Sie das Dashboard Ihres Azure DevOps-Projekts, klicken Sie auf das Menü **Azure Pipelines**, und wählen Sie **WhiteSource Bolt** aus.
   > [!div class="mx-imgBorder"]
   > ![WhiteSource-Vorteil: Erweiterung hinzufügen](_img/vs-whitesource/vs-whitesource-installed-cropped.png)

6. Fügen Sie den Aktivierungscode aus der Kachel „WhiteSource Bolt-Vorteil“ ein, und klicken Sie auf **Aktivieren**. Jeder Aktivierungscode kann nur für die Aktivierung eines Projekts verwendet werden.
   > [!div class="mx-imgBorder"]
   > ![WhiteSource Bolt-Vorteil: Aktivierungscode](_img/vs-whitesource/vs-whitesource-activate-code-cropped.png)

7. Die Aktivierung ist nun abgeschlossen, und für Ihr Abonnement verbleiben 180 Tage.

8. Sie müssen die WhiteSource Bolt-Erweiterung als einen der Buildschritte hinzufügen.  Dies wird in einem Video erläutert, das auf der Seite [WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) verfügbar ist.

9. Sobald Sie den Build ausgeführt haben, werden folgende umfassende Berichte und Dashboards automatisch generiert:
    - Dashboard „Sicherheitsrisiken“
    - Bericht zu Sicherheitsrisiken
    - Bericht zu veralteten Bibliotheken
    - Dashboard „Lizenzrisiken und Konformität“
    - Bericht zum Bestand

## <a name="eligibility"></a>Berechtigung

| Abonnementstufe                                                 |     Channels                                            | Vorteil                                                          | Erneuerbar?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, Retail, NFR ausgewählt<sup>1</sup> | 6 Monate       |  Ja          |
| Visual Studio Professional (Standard) | VL, Azure, Retail                                       | Nicht verfügbar                                                           |NA         |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Nicht verfügbar                                             |  NA         |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Nicht verfügbar                                              | NA         |
| Visual Studio Dev Essentials | NA  | Nicht verfügbar |NA |
| Visual Studio Enterprise, Visual Studio Professional (Cloudabonnement mit monatlicher Laufzeit) | Azure                                       | Nicht verfügbar                                                           |NA|

<sup>1</sup> *Umfasst:  Microsoft Partner Network (Enterprise).  Umfasst nicht: Not for Resale (NFR), Visual Studio Industry Partner (VSIP), FTE, MCT Software & Services (Developer), BizSpark, Imagine, Microsoft Valued Professional (MVP), Region Director (RD), MCT Software & Services, Microsoft Partner Network (Professional).*


> [!NOTE]
> In Cloud-Abonnements enthaltene Jahresabonnements von Visual Studio Professional und Visual Studio Enterprise werden von Microsoft nicht mehr angeboten. An den vorhandenen Funktionen und der Möglichkeit, Abonnements zu erneuern, erhöhen, verringern oder zu kündigen, wird sich nichts ändern. Neuen Kunden wird empfohlen, die verschiedenen Optionen für den Erwerb von Visual Studio unter [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) zu vergleichen.


Sie wissen nicht genau, welches Abonnement Sie verwenden?  Stellen Sie eine Verbindung mit [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) her, um alle Abonnements anzuzeigen, die Ihrer E-Mail-Adresse zugewiesen sind. Wenn nicht alle Ihrer Abonnements angezeigt werden, sind möglicherweise einige Abonnements einer anderen E-Mail-Adresse zugewiesen.  Sie müssen sich mit der entsprechenden E-Mail-Adresse anmelden, um diese Abonnements anzuzeigen.

## <a name="support-resources"></a>Supportressourcen

-  Benötigen Sie Hilfe bei WhiteSource Bolt?  Chatten Sie unter https://www.whitesourcesoftware.com/vse_whitesource_bolt/ live mit einem Mitarbeiter von WhiteSource Bolt.
-  Wenn Sie Unterstützung bei Vertrieb, Abonnements, Konten und Abrechnung für Visual Studio-Abonnements benötigen, wenden Sie sich an den [Abonnementsupport](https://visualstudio.microsoft.com/subscriptions/support/) für Visual Studio.
-  Haben Sie Fragen zur Visual Studio-IDE, zu Azure DevOps Services oder zu anderen Visual Studio-Produkten oder -Diensten?  Besuchen Sie die [Visual Studio-Supportwebsite](https://visualstudio.microsoft.com/support/).