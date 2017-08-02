---
title: "Veröffentlichen einer Python-App in Azure App Service über Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85031f91-3a65-463b-a678-1e69f1b843e6
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 0163d1279b41ef8fecf9ca774cd3e67f0f47f1b1
ms.lasthandoff: 03/07/2017

---

# <a name="publishing-to-azure-app-service"></a>Veröffentlichen in Azure App Service

Sie können mit den folgenden Schritten schnell eine Python-Website in Visual Studio erstellen und sie in Azure App Service veröffentlichen:

- [Erstellen eines Azure-Abonnements](#create-an-azure-subscription)
- [Erstellen und Testen des anfänglichen Projekts](#create-and-test-the-initial-project)
- [Veröffentlichen in Azure App Service](#publish-to-azure-app-service)

Eine kurze exemplarische Vorgehensweise dieses Prozesses finden Sie unter [Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (Visual Studio-Python-Tutorial: Erstellen einer Website) (youtube.com, 3 Min. 10 Sek.). 

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk] 

## <a name="create-an-azure-subscription"></a>Erstellen eines Azure-Abonnements

Die Veröffentlichung in Azure erfordert ein Azure-Abonnement, oder verwenden Sie eine temporäre Website.

Beginnen Sie für Abonnements mit einem [kostenlosen vollwertigen Azure-Konto](https://azure.microsoft.com/en-us/free/), das mit einem großzügigen Guthaben für Azure-Dienste verbunden ist. Erwägen Sie auch die Anmeldung für die Mitgliedschaft bei [Visual Studio Developer Essentials](https://azure.microsoft.com/en-us/pricing/member-offers/vs-dev-essentials/), wo Sie ein ganzes Jahr lang jeden Monat ein Guthaben von 25 $ erhalten.

So erstellen Sie eine temporäre Website in Azure App Service, ohne dass ein Azure-Abonnement erforderlich ist:

1. Öffnen Sie in Ihrem Browser [try.azurewebsites.net](https://try.azurewebsites.net).
1. Wählen Sie **Web-App** als App-Typ und dann **Weiter**.
1. Wählen Sie **Leere Website** als Vorlage und dann **Erstellen >**.
1. Melden Sie sich mit den Anmeldedaten eines sozialen Netzwerks Ihrer Wahl an, und nach kurzer Zeit ist Ihre Website unter der angezeigten URL bereit.
1. Wählen Sie **Veröffentlichungsprofil herunterladen**, und speichern Sie die `.publishsettings`-Datei, die Sie später verwenden werden.

## <a name="create-and-test-the-initial-project"></a>Erstellen und Testen des anfänglichen Projekts

1. Wählen Sie in Visual Studio **Datei > Neu > Projekt**, suchen Sie nach „Bottle“, wählen Sie das **Bottle-Webprojekt**, und klicken Sie auf **OK**.    

1. Wenn Sie aufgefordert werden, externe Pakete zu installieren, wählen Sie **In einer virtuellen Umgebung installieren**. Beachten Sie das Steuerelement **Erforderliche Pakete anzeigen** am unteren Rand des Dialogfelds, das anzeigt, welche Pakete installiert werden:

  ![Installieren erforderlicher Pakete](~/docs/python/media/tutorials-common-external-packages.png)

1. Wählen Sie Ihren bevorzugten Basisinterpreter für die virtuelle Umgebung aus (z.B. **Python 2.7** oder **Python 3.4**), und klicken Sie auf **Erstellen**:

  ![Hinzufügen einer virtuellen Umgebung beim Erstellen eines Projekts](~/docs/python/media/tutorials-common-add-virtual-environment.png)

1. Sobald das Projekt erstellt ist, testen Sie es lokal durch Auswahl von **Debuggen > Debuggen starten** oder Drücken von F5. Standardmäßig verwendet die Anwendung ein Repository im Arbeitsspeicher, das nicht konfiguriert werden muss. Alle Daten gehen verloren, wenn der Webserver angehalten wird.

1. Klicken Sie auf verschiedene Punkte in der Anwendung, um ihren Ablauf zu sehen.

1. Wenn Sie fertig sind, beenden Sie den Debugger (**Debuggen > Debuggen beenden** oder UMSCHALT+F5).

## <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**. 

1. Wählen Sie im Dialogfeld **Veröffentlichen** **Microsoft Azure App Service**:

  ![Veröffentlichen in Azure – Schritt 1](~/docs/python/media/tutorials-common-publish-1.png)

1. Wählen Sie ein Ziel aus:

    - Wenn Sie ein Azure-Abonnement haben, wählen Sie **Microsoft Azure App Service** als Veröffentlichungsziel, wählen Sie dann im folgenden Dialogfeld einen vorhandenen App Service aus, oder wählen Sie **Neu**, um einen neuen zu erstellen.
    - Wenn Sie eine temporäre Website von „try.azurewebsites.net“ verwenden, wählen Sie **Importieren** als Veröffentlichungsziel, suchen Sie dann nach der `.publishsettings`-Datei, die von der Website heruntergeladen wurde, und wählen Sie **OK**.

1. Die App Service-Details werden im Dialogfeld **Veröffentlichen** auf der Registerkarte **Verbindung** unten angezeigt.

  ![Veröffentlichen in Azure – Schritt 2](~/docs/python/media/tutorials-common-publish-2.png)

1. Wählen Sie **Weiter >** nach Bedarf, um zusätzliche Einstellungen zu überprüfen. Wenn Sie planen, [Ihren Python-Code in Azure remote zu debuggen](debugging-azure-remote.md), müssen Sie für **Konfiguration** **Debuggen** festlegen.
1. Wählen Sie **Veröffentlichen**. Sobald Ihre Anwendung in Azure bereitgestellt ist, öffnet Ihr Standardbrowser diese Website. 
