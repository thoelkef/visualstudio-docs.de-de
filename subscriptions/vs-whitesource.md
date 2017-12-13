---
title: WhiteSource Bolt-Vorteil
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Erfahren Sie, wie Sie das WhiteSource Bolt-Abonnement aktivieren, das in Ihrem Visual Studio-Abonnement enthalten ist.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: c1976d9eaa6ef18978a9e9d5453c3080741223d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
#  <a name="activating-the-whitesource-bolt-benefit-in-visual-studio-subscriptions"></a>Aktivieren des WhiteSource Bolt-Vorteils in Visual Studio-Abonnements

Bestimmen und schließen Sie Schwachstellen in Open-Source-Komponenten, und erzeugen Sie umfassende Bestands- und Lizenzberichte zu allen Open-Source-Komponenten in Ihrem Build.  Ihr Enterprise-Abonnement enthält ein kostenloses Abonnement für sechs Monate. 

1.  Klicken Sie im unteren Bereich der Kachel „Vorteile“ auf den Link **Code abrufen**, um den WhiteSource Bolt-Vorteil zu nutzen.    

![Kachel „WhiteSource Bolt-Vorteil“](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Sie erhalten eine Benachrichtigung, die den Aktivierungscode anzeigt.  **Kopieren Sie den Code in die Zwischenablage**, und klicken Sie auf **Activate** (Aktivieren). 

![WhiteSource Bolt-Vorteil: Code ](_img\vs-whitesource\vs-whitesource-code.png)

3.  Klicken Sie auf der WhiteSource-Webseite auf die Schaltfläche **Aktivieren**, und scrollen Sie zum Bereich **Activate your account** (Konto aktivieren) der Seite herunter.  

![WhiteSource Bolt-Vorteil: Aktivierung](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  Im Abschnitt **Activate your account** (Konto aktivieren) der Seite werden Sie durch vier Schritte geführt:
- [Installieren](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) Sie die WhiteSource Bolt-Erweiterung von Microsoft Visual Studio Marketplace. Wenn Sie nicht über die Berechtigungen zum Installieren von Erweiterungen verfügen, besuchen Sie [diese Seite](https://www.visualstudio.com/en-us/docs/marketplace/get-vsts-extensions#request).

    Klicken Sie auf die grüne Schaltfläche **Installieren**, wenn Sie VSTS verwenden oder bei Team Foundation Server auf die Schaltfläche **Herunterladen**.  In diesem Beispiel wird VSTS verwendet. 

![WhiteSource-Vorteil: Erweiterung installieren](_img\vs-whitesource\vs-whitesource-download-install.png)

- Wählen Sie dann das VSTS-Konto aus, das Sie verwenden möchten, und klicken Sie auf **Bestätigen**.  (Wenn Sie VSTS nicht eingerichtet haben, besuchen Sie die Seite [Vorteile](https://my.visualstudio.com/benefits), und aktivieren Sie Ihren VSTS-Vorteil.)

![WhiteSource-Vorteil: Konto bestätigen](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- Sie erhalten eine Bestätigung, dass die Erweiterung installiert wurde und einsatzbereit ist.  Klicken Sie auf **Erste Schritte**, um zur Seite „Fortfahren“ von WhiteSource Bolt zurückzukehren.  

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
