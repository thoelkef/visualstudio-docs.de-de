---
title: WhiteSource Bolt-Vorteil | Microsoft-Dokumentation
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/11/2017
Ms.topic: Get-Started-Article
Description: Learn how to activate the WhiteSource Bolt subscription included with your Visual Studio subscription.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: fe8e731e26765ec17b56383e04362efa25b2f141
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt in Visual Studio-Abonnements

## <a name="overview"></a>Übersicht

Bestimmen und schließen Sie Schwachstellen in Open-Source-Komponenten, und erzeugen Sie umfassende Bestands- und Lizenzberichte zu allen Open-Source-Komponenten in Ihrem Build.  Ausgewählte Visual Studio-Abonnements bieten sechs Monate lang kostenlosen Zugriff. 

## <a name="eligibility"></a>Berechtigung

| Abonnementstufe/Programm                                                  | Vorteil               | Erneuerbar?                                                         |
|-------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------|
| Visual Studio Enterprise Standard                                             | 6 Monate              | Ja                                                                |
| Visual Studio Enterprise – Jahresabonnement                                               | 6 Monate              | Ja                                                                |
| Visual Studio Enterprise – Monatsabonnement                                              | Nicht verfügbar         |                                                                    |
| Visual Studio Professional Standard                                           | Nicht verfügbar         |                                                                    |
| Visual Studio Professional – Jahresabonnement                                             | Nicht verfügbar         |                                                                    | 
| Visual Studio Professional – Monatsabonnement                                            | Nicht verfügbar         |                                                                    |
| Visual Studio Test Pro                                                        | Nicht verfügbar         |                                                                    |
| MSDN Platforms                                                                | Nicht verfügbar         |                                                                    |
| Visual Studio Dev Essentials                                                  | Nicht verfügbar         |                                                                    |
| Visual Studio Enterprise – NFR<sup>1</sup>                                               | Nicht verfügbar         |                                                                    |
| Visual Studio Enterprise – FTE                                                | Nicht verfügbar         |                                                                    |
| Visual Studio Enterprise – Microsoft Partner Network                          | 6 Monate              | Ja                                                                |
| Visual Studio Professional – Microsoft Partner Network                        | Nicht verfügbar         |                                                                    |
| Visual Studio Enterprise – Imagine (Standard)                                 | Nicht verfügbar         |                                                                    |
| Visual Studio Enterprise – Imagine (Premium)                                  | Nicht verfügbar         |                                                                    |
| Visual Studio Enterprise – BizSpark                                           | Nicht verfügbar         |                                                                    |
| Microsoft Certified Trainer – Software & Dienste                             | Nicht verfügbar         |                                                                    |
| Microsoft Certified Trainer – Software & Dienste für Entwickler                   | Nicht verfügbar         |                                                                    |

<sup>1</sup> *Umfasst Not for Resale (NFR), Microsoft Valued Partner (MVP), Region Director (RD), Visual Studio Industry Partner (VSIP)*  

Sie wissen nicht genau, welches Abonnement Sie verwenden?  Besuchen Sie die Website [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs), um alle Abonnements anzuzeigen, die Ihrer E-Mail-Adresse zugewiesen sind. Wenn nicht alle Ihrer Abonnements angezeigt werden, sind möglicherweise einige Abonnements einer anderen E-Mail-Adresse zugewiesen.  Sie müssen sich mit der entsprechenden E-Mail-Adresse anmelden, um diese Abonnements anzuzeigen. 

## <a name="activation-steps"></a>Aktivierungsschritte

1.  Um Ihren WhiteSource Bolt-Vorteil zu aktivieren, melden Sie sich auf [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) an.

2.  Suchen Sie im Abschnitt „Tools“ die Kachel „WhiteSource“, und klicken Sie im unteren Bereich der Kachel mit den Vorteilen auf den Link **Code abrufen**.    

    ![Kachel „WhiteSource Bolt-Vorteil“](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Sie erhalten eine Benachrichtigung, die den Aktivierungscode anzeigt.  **Kopieren Sie den Code in die Zwischenablage**, und klicken Sie auf **Activate** (Aktivieren). 

    ![WhiteSource Bolt-Vorteil: Code ](_img\vs-whitesource\vs-whitesource-code.png)

3.  Klicken Sie auf der WhiteSource-Webseite auf die Schaltfläche **Aktivieren**, und scrollen Sie zum Bereich **Activate your account** (Konto aktivieren) der Seite herunter.  

    ![WhiteSource Bolt-Vorteil: Aktivierung](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  Im Abschnitt **Activate your account** (Konto aktivieren) der Seite werden Sie durch vier Schritte geführt:
    - [Installieren](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) Sie die WhiteSource Bolt-Erweiterung von Microsoft Visual Studio Marketplace. Wenn Sie nicht über die Berechtigungen zum Installieren von Erweiterungen verfügen, besuchen Sie [diese Seite](https://www.visualstudio.com/docs/marketplace/get-vsts-extensions#request).

    Klicken Sie auf die grüne Schaltfläche **Installieren**, wenn Sie VSTS verwenden oder bei Team Foundation Server auf die Schaltfläche **Herunterladen**.  In diesem Beispiel wird VSTS verwendet. 

    ![WhiteSource-Vorteil: Erweiterung installieren](_img\vs-whitesource\vs-whitesource-download-install.png)

    - Wählen Sie dann das VSTS-Konto aus, das Sie verwenden möchten, und klicken Sie auf **Bestätigen**.  (Wenn Sie VSTS nicht eingerichtet haben, besuchen Sie die Seite [Vorteile](https://my.visualstudio.com/benefits), und aktivieren Sie Ihren VSTS-Vorteil.)

    ![WhiteSource-Vorteil: Konto bestätigen](_img\vs-whitesource\vs-whitesource-confirm-account.png)

    - Sie erhalten eine Bestätigung, dass die Erweiterung installiert wurde und einsatzbereit ist.  Klicken Sie auf **Los geht‘s**, um zur WhiteSource Bolt-Seite zurückzukehren und fortzufahren.  

    ![WhiteSource-Vorteil: Installation abgeschlossen](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Öffnen Sie Ihr VSTS-Projektdashboard (Visual Studio Team Services), klicken Sie auf das Menü **Build und Release**, und wählen Sie **WhiteSource Bolt** aus.

    ![WhiteSource-Vorteil: Erweiterung hinzufügen](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. Fügen Sie den Aktivierungscode aus der Kachel „WhiteSource Bolt-Vorteil“ ein, und klicken Sie auf **Aktivieren**. Jeder Aktivierungscode kann nur für die Aktivierung eines Projekts verwendet werden. 

    ![WhiteSource Bolt-Vorteil: Aktivierungscode](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  Die Aktivierung ist nun abgeschlossen, und für Ihr Abonnement verbleiben 180 Tage. 

8.  Sie müssen die WhiteSource Bolt-Erweiterung als einen der Buildschritte hinzufügen.  Dies wird in einem Video erläutert, das auf der Seite [WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) verfügbar ist.  

9. Sobald Sie den Build ausgeführt haben, werden folgende umfassende Berichte und Dashboards automatisch generiert:
    - Dashboard „Sicherheitsrisiken“
    - Bericht zu Sicherheitsrisiken
    - Bericht zu veralteten Bibliotheken
    - Dashboard „Lizenzrisiken und Konformität“
    - Bericht zum Bestand

## <a name="faq"></a>FAQ
*Hier nach Updates suchen*

## <a name="support-resources"></a>Supportressourcen
-  Benötigen Sie Hilfe bei WhiteSource Bolt?  Chatten Sie unter https://www.whitesourcesoftware.com/vse_whitesource_bolt/ live mit einem WhiteSource Bolt-Mitarbeiter. 
-  Wenn Sie Unterstützung bei Vertrieb, Abonnements, Konten und Abrechnung für Visual Studio-Abonnements benötigen, wenden Sie sich an den [Abonnementsupport](https://www.visualstudio.com/subscriptions/support/) für Visual Studio.
-  Haben Sie eine Frage zu Visual Studio IDE, Visual Studio Team Services oder anderen Visual Studio-Produkten oder -Diensten?  Besuchen Sie die [Visual Studio-Supportwebsite](https://www.visualstudio.com/support/). 

