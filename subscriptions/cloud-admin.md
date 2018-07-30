---
title: Einrichten von Administratoren für Cloudabonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/28/2018
ms.topic: Get-Started-Article
description: Einrichten von Administratoren für Cloudabonnements
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a3a275ae81915ddf9eb89a59c4f90108df1f33da
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231275"
---
# <a name="setting-up-administrators-for-visual-studio-cloud-subscriptions"></a>Einrichten von Administratoren für Visual Studio-Cloudabonnements

Visual Studio-Cloudabonnements werden von Administratoren verwaltet.  Diese Personen können Abonnements zuweisen, Zuweisungen bearbeiten, Abonnements hinzufügen oder löschen und andere Verwaltungsaufgaben mit Abonnements ausführen. 

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Der Besitzer des Azure-Abonnements ist der erste Administrator 

Wenn Sie Visual Studio-Abonnements erwerben, werden Sie als Besitzer des für den Erwerb verwendeten Azure-Abonnements automatisch als Administrator für diese Abonnements eingerichtet. 

Sie können Cloudabonnements über den [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) erwerben. Sie können sich dazu aber auch an einen Cloudlösungsanbieter wenden.  Bei einem Kauf über den Visual Studio Marketplace wird Ihnen am Ende des Einkaufs eine Option zum Verwalten von Benutzern angeboten.  Wenn Sie diese Option auswählen, gelangen Sie zum Verwaltungsportal für Visual Studio Abonnements: [https://manage.visualstudio.com](https://manage.visualstudio.com).

Nachdem Sie die Abonnements erworben haben, können Sie das [Verwaltungsportal](https://manage.visualstudio.com) jederzeit besuchen.  Melden Sie sich einfach beim Portal an, und wählen Sie oben links das entsprechende Azure-Abonnement aus. 

Als Besitzer des Azure-Abonnements, mit dem die Cloudabonnements erworben wurden, können Sie auch weitere Administratoren zuweisen.

## <a name="adding-administrators"></a>Hinzufügen von Administratoren

So fügen Sie Administratoren hinzu
1. Stellen Sie eine Verbindung mit dem Azure-Portal unter [portal.azure.com](https://portal.azure.com) her.
2. Melden Sie sich mit dem Konto an, das Sie verwendet haben, um die Visual Studio-Cloudabonnements zu erwerben.
3. Scrollen Sie im linken Navigationsbereich nach unten bis zu **Kostenverwaltung + Abrechnung**.
4. Wählen Sie in der Liste **Meine Abonnements** das Azure-Abonnement aus, das Sie für den Kauf verwendet haben.
5. Klicken Sie im oberen Bereich der Liste im linken Navigationsbereich auf **Zugriffssteuerung**.  
6. Klicken Sie oben auf der Seite auf die Registerkarte **Hinzufügen**. 
7. Klicken Sie im eingeblendeten Bereich auf der rechten Seite auf den Namen des Abonnenten, den Sie zu einem Administrator machen möchten.
8. Klicken Sie oben im Bereich auf die Dropdownliste **Rolle**, scrollen Sie nach unten, und wählen Sie **Benutzerzugriffsadministrator** aus.
9. Klicken Sie auf **Speichern**.
Der gewünschten Abonnent wird nun in der Mitte der Seite angezeigt, und die Rolle wird als „Benutzerzugriffsadministrator“ angegeben.  

Der neue Administrator kann sich jetzt beim [Verwaltungsportal](https://manage.visualstudio.com) anmelden, das gleiche Azure-Abonnement, das für den Kauf der Cloudabonnements verwendet wurde, aus der Liste oben links auf der Seite auswählen und damit beginnen, diese Abonnements zu verwalten. 

> [!NOTE]
> Wenn Sie feststellen, dass die Benutzer zum Bearbeiten Ihrer Cloudabonnements Zugriff haben, den Sie nicht als Administratoren eingerichtet haben, haben diese Benutzer möglicherweise Rollen im zugrunde liegenden Azure-Abonnement, die es ihnen ermöglichen, Abonnements zu verwalten.  Diese Rollen umfassen: Besitzer, Mitwirkender, Dienstadministrator oder Co-Administrator.  Weitere Informationen finden Sie unter https://docs.microsoft.com/vsts/billing/add-backup-billing-managers?view=vsts

Weitere Informationen zu Visual Studio-Cloudabonnements finden Sie unter [Übersicht](vscloud-overview.md) im Thema „Kaufen von Cloudabonnements“. Besuchen Sie den Visual Studio Marketplace unter [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription), um Visual Studio-Abonnements zu erwerben. 

