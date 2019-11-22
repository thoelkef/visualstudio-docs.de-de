---
title: 'Erste Schritte mit PTVS: Erstellen einer Website in Azure | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 288fb24c9c1c4ddee1cb59a968e717531e274af1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300582"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>Erste Schritte mit PTVS: Erstellen einer Website in Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beginnen Sie ganz schnell und einfach damit, eine Python-Website in Azure zu erstellen.  
  
 Sie können diese Anweisungen in einem sehr kurzen [YouTube-Video](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) ansehen.  
  
 Starten Sie mit dem Dialogfeld „Neues Projekt...“, und wählen Sie aus den Python-Projekten das Bottle Web Project aus.  Diese [Bottle](http://bottlepy.org/docs/dev/index.html)-Vorlage ist eine Startwebsite, die auf dem [Bootstrap-Framework](https://getbootstrap.com/) basiert.  Wenn Sie das Projekt erstellen, fordert Visual Studio Sie auf, Abhängigkeiten (in diesem Fall "Bottle") in einer virtuellen Umgebung installieren.  Da Sie die Bereitstellung für eine Azure-Website durchführen, müssen Sie die Abhängigkeiten in einer virtuellen Umgebung hinzufügen, um den ordnungsgemäßen Betrieb Ihrer Website zu gewährleisten.  Sie müssen Ihre Umgebung auf Python 2.7 oder 3.4 (32 Bit) basieren.  Nachdem Sie das Projekt erstellt haben, drücken Sie auf F5, um die Website lokal auszuführen.  
  
 Es ist ganz einfach, die Website in Azure auszuprobieren.  Wenn Sie kein Azure-Abonnement besitzen, können Sie [try.azurewebsites.net](https://trywebsites.azurewebsites.net/) verwenden.  Diese Website bietet eine einfache Möglichkeit, Azure-Websites eine Stunde lang auszuprobieren. Die Anmeldung kann einfach mit den Anmeldedaten für ein soziales Netzwerk erfolgen.  Sie benötigen keine Kreditkarte.  Wählen Sie in der Dropdownliste "Sprache ändern" die leere Websitevorlage aus, und wählen Sie "Erstellen".  Wählen Sie unter "Arbeiten mit der Webanwendung" die Option "Veröffentlichungsprofil herunterladen", und speichern Sie die Datei zur Verwendung mit Visual Studio.  Sie können die Bereitstellung auch über Git aus einem anderen Betriebssystem durchführen.  
  
 Wechseln Sie zurück zu Visual Studio und dem von Ihnen erstellten Projekt.  Wählen Sie im Projektmappen-Explorer den Projektknoten aus, klicken Sie auf die Schaltfläche mit dem Zeiger nach rechts, und wählen Sie "Veröffentlichen" aus.  Wenn Sie über ein Azure-Abonnement verfügen, können Sie im Dialogfeld auf "Microsoft Azure-Websites" klicken, um Ihre Websites von dort zu verwalten.  Wählen Sie für diese exemplarische Vorgehensweise die Option "Importieren" aus, um das Veröffentlichungsprofil zu importieren, das Sie gerade heruntergeladen haben.  Da das Veröffentlichungsprofil alle erforderlichen Informationen enthält, können Sie die Option "Veröffentlichen" wählen.  In wenigen Sekunden wird ein neues Browserfenster geöffnet, und Ihre Website ist live in der Azure-Cloud gehostet.  
  
 Einfache Websites stellen kein Problem dar. Informationen zu größeren und komplexeren Webanwendungen in Azure finden Sie im [Video mit detaillierten Informationen](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) sowie in weiteren Videos in diesem Kanal (Links dazu finden Sie oben rechts auf den Seiten mit den Videos für den Einstieg bzw. mit detaillierten Informationen sowie auf dieser Seite unten).  
  
 Sie können diese Anweisungen in einem sehr kurzen [YouTube-Video](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) ansehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiki-Dokumentation](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [PTVS-Videos: Einstieg und ausführliche Erläuterungen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
