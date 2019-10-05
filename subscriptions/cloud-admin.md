---
title: Einrichten von Administratoren für Cloudabonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: lank
ms.date: 07/17/2019
ms.topic: conceptual
description: Einrichten von Administratoren für Cloudabonnements
ms.openlocfilehash: 62a350e6061444e3c75878dfd89739011c4641d5
ms.sourcegitcommit: 57866dd72fd0e15ce61128df70729b427a2d02eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315208"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>Einrichten von Administratoren für Visual Studio-Cloudabonnements

Visual Studio-Cloudabonnements werden von Administratoren verwaltet. Diese Personen können Abonnements zuweisen, Zuweisungen bearbeiten, Abonnements hinzufügen oder löschen und andere Verwaltungsaufgaben mit Abonnements ausführen.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Der Besitzer des Azure-Abonnements ist der erste Administrator

Wenn Sie Visual Studio-Abonnements erwerben, werden Sie als Besitzer des für den Erwerb verwendeten Azure-Abonnements automatisch als Administrator für diese Abonnements eingerichtet.

Sie können Cloudabonnements über den [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) erwerben. Sie können sich dazu aber auch an einen Cloudlösungsanbieter wenden. Bei einem Kauf über den Visual Studio Marketplace wird Ihnen am Ende des Einkaufs eine Option zum Verwalten von Benutzern angeboten. Wenn Sie diese Option auswählen, gelangen Sie zum Verwaltungsportal für Visual Studio Abonnements: [https://manage.visualstudio.com](https://manage.visualstudio.com).

Nachdem Sie die Abonnements erworben haben, können Sie das [Verwaltungsportal](https://manage.visualstudio.com) jederzeit aufrufen. Melden Sie sich einfach beim Portal an, und wählen Sie oben links das entsprechende Azure-Abonnement aus.

Als Besitzer des Azure-Abonnements, mit dem die Cloudabonnements erworben wurden, können Sie auch weitere Administratoren zuweisen.

## <a name="add-administrators"></a>Hinzufügen von Administratoren

So fügen Sie Administratoren hinzu

1. Stellen Sie eine Verbindung mit dem Azure-Portal unter [portal.azure.com](https://portal.azure.com) her.
2. Melden Sie sich mit dem Konto an, das Sie verwendet haben, um die Visual Studio-Cloudabonnements zu erwerben.
3. Scrollen Sie im linken Navigationsbereich nach unten bis zu **Kostenverwaltung + Abrechnung**.
4. Wählen Sie in der Liste **Meine Abonnements** das Azure-Abonnement aus, das Sie für den Kauf verwendet haben.
5. Klicken Sie im oberen Bereich der Liste im linken Navigationsbereich auf **Zugriffssteuerung**.
6. Klicken Sie oben auf der Seite auf die Registerkarte **Hinzufügen**.
7. Klicken Sie auf **Rollenzuweisung hinzufügen**.
8. Klicken Sie oben rechts auf die Dropdownliste **Rolle**, scrollen Sie nach unten, und wählen Sie **Benutzerzugriffsadministrator** aus.
9. Scrollen Sie in der Benutzerliste zu dem Benutzer, den Sie als Administrator festlegen möchten, und wählen Sie ihn aus. 
10. Klicken Sie auf **Speichern**.
11. Klicken Sie auf die Registerkarte **Rollenzuweisungen**, um zu überprüfen, ob der ausgewählte Benutzer nun als Benutzerzugriffsadministrator aufgeführt wird.

Der neue Administrator kann sich jetzt beim [Verwaltungsportal](https://manage.visualstudio.com) anmelden und dann das gleiche Azure-Abonnement, das für den Kauf der Cloudabonnements verwendet wurde, aus der Liste oben links auf der Seite auswählen und damit beginnen, die Abonnements zu verwalten.

> [!NOTE]
> Wenn Sie feststellen, dass die Benutzer zum Bearbeiten Ihrer Cloudabonnements Zugriff haben, den Sie nicht als Administratoren eingerichtet haben, haben diese Benutzer möglicherweise Rollen im zugrunde liegenden Azure-Abonnement, die es ihnen ermöglichen, Abonnements zu verwalten. Zu diesen Rollen gehören: Besitzer, Mitwirkender, Dienstadministrator oder Co-Admin. Weitere Informationen finden Sie unter [Hinzufügen von Rechnungs-Managern](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts).

Weitere Informationen zu Visual Studio-Cloudabonnements finden Sie in der [Übersicht](vscloud-overview.md) des Marketplace. Besuchen Sie den Visual Studio Marketplace unter [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription), um Visual Studio-Abonnements zu erwerben.
