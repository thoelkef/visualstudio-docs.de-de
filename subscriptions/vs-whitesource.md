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
ms.openlocfilehash: 0c2eed9efdcca076c20a240d60b4d38cdda23019
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31199400"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt in Visual Studio-Abonnements

Bestimmen und schließen Sie Schwachstellen in Open-Source-Komponenten, und erzeugen Sie umfassende Bestands- und Lizenzberichte zu allen Open-Source-Komponenten in Ihrem Build.  Ausgewählte Visual Studio-Abonnements bieten sechs Monate lang kostenlosen Zugriff. 

## <a name="activation-steps"></a>Aktivierungsschritte

1.  Melden Sie sich unter [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) an, um Ihren WhiteSource Bolt-Vorteil zu aktivieren.

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

## <a name="eligibility"></a>Berechtigung
| Abonnementstufe                                                 |     Channels                                            | Vorteil                                                          | Erneuerbar?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard, jährliche Cloud)   | VL, Azure, Retail, NFR ausgewählt<sup>1</sup> | 6 Monate       |  Ja          |
| Visual Studio Professional (Standard, Cloudabonnement mit jährlicher Laufzeit) | VL, Azure, Retail                                       | Nicht verfügbar                                                           |NA         |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Nicht verfügbar                                             |  NA         |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Nicht verfügbar                                              | NA         |
| Visual Studio Dev Essentials | NA  | Nicht verfügbar |NA |
| Visual Studio Enterprise, Visual Studio Professional (Cloudabonnement mit monatlicher Laufzeit) | Azure                                       | Nicht verfügbar                                                           |NA|

<sup>1</sup> *Umfasst: Microsoft Partner Network (Enterprise).  Umfasst nicht: Not for Resale (NFR), Visual Studio Industry Partner (VSIP), FTE, MCT Software & Services (Developer), BizSpark, Imagine, Microsoft Valued Partner (MVP), Region Director (RD), MCT Software & Services, Microsoft Partner Network (Professional).*

Sie wissen nicht genau, welches Abonnement Sie verwenden?  Stellen Sie eine Verbindung mit [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) her, um alle Abonnements anzuzeigen, die Ihrer E-Mail-Adresse zugewiesen sind. Wenn nicht alle Ihrer Abonnements angezeigt werden, sind möglicherweise einige Abonnements einer anderen E-Mail-Adresse zugewiesen.  Sie müssen sich mit der entsprechenden E-Mail-Adresse anmelden, um diese Abonnements anzuzeigen. 


## <a name="support-resources"></a>Supportressourcen
-  Benötigen Sie Hilfe bei WhiteSource Bolt?  Chatten Sie unter https://www.whitesourcesoftware.com/vse_whitesource_bolt/ live mit einem Mitarbeiter von WhiteSource Bolt. 
-  Wenn Sie Unterstützung bei Vertrieb, Abonnements, Konten und Abrechnung für Visual Studio-Abonnements benötigen, wenden Sie sich an den [Abonnementsupport](https://www.visualstudio.com/subscriptions/support/) für Visual Studio.
-  Haben Sie eine Frage zu Visual Studio IDE, Visual Studio Team Services oder anderen Visual Studio-Produkten oder -Diensten?  Besuchen Sie die [Visual Studio-Supportwebsite](https://www.visualstudio.com/support/). 

