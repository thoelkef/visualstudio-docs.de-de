---
title: Löschen von Abonnementzuweisungen im Verwaltungsportal für Visual Studio-Abonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 06/16/2020
ms.topic: how-to
description: Erfahren Sie, wie Administratoren Abonnementzuweisungen löschen können.
ms.openlocfilehash: 4f952f574132afbd405c82c75fcddfc952bffb48
ms.sourcegitcommit: b8ce85a6d9c7fcceaad0fba625202f5ecf8f368c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2020
ms.locfileid: "87434267"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Löschen von Zuweisungen in Visual Studio-Abonnements
Wenn ein Abonnent kein Visual Studio-Abonnement mehr benötigt (wenn er z.B. ein Unternehmen verlässt, ein Projekt abgeschlossen ist, oder wenn er eine neue Rolle übernimmt), können Sie das entsprechende Abonnement entfernen und es einem anderen Benutzer zuweisen. Beachten Sie, dass bei der Neuzuweisung eines Abonnements nicht alle Abonnementvorteile zurückgesetzt werden.  Der neue Benutzer kann noch nicht in Anspruch genommene Schlüssel in Anspruch nehmen und sich bereits in Anspruch genommene Schlüssel ansehen. Anspruchseinschränkungen werden **nicht** zurückgesetzt.  Für Organisationen mit Enterprise Agreements (EA) werden jegliche Vorteile zurückgesetzt, die der ursprüngliche Benutzer genutzt hat, wie z.B. Pluralsight-Schulung. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Löschen einer Abonnementzuweisung
1. Klicken Sie auf den Namen des zu entfernenden Abonnenten. Um mehrere Abonnenten zum Entfernen auszuwählen, können Sie auf den Kreis links neben dem Namen des Abonnenten klicken und jeden Abonnenten einzeln auszuwählen.  Alternativ können Sie die **STRG**-Taste gedrückt halten und auf jeden Abonnenten klicken, den Sie entfernen möchten. Um einen Bereich von Abonnenten zu entfernen, klicken Sie auf den ersten, drücken die **UMSCHALTTASTE** und klicken auf den letzten.  Drücken Sie **STRG+A**, um alle Abonnenten auszuwählen und zu entfernen. 
2. Klicken Sie auf **Löschen**, um den ausgewählten Abonnenten bzw. die ausgewählten Abonnenten zu löschen.
3. Bestätigen Sie den Löschvorgang mit **OK**.
   > [!div class="mx-imgBorder"]
   > ![Abonnenten löschen](_img/delete-license/delete-subscribers.png "Wählen Sie die Benutzer aus, die Sie löschen möchten, und klicken Sie auf „Löschen“. Sie können die STRG- und die UMSCHALT-Taste verwenden, um mehrere Abonnenten auszuwählen.")

   > [!NOTE]
   > Eine Massenlöschung unter Verwendung einer Vorlage ist nicht verfügbar. Für Organisationen, die Abonnementzuweisungen über Azure Active Directory-Sicherheitsgruppen verwalten, finden Sie in [diesem Artikel](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) weitere Informationen darüber, wie Löschungen durchgeführt werden.  

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentation zu Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
- Müssen Sie ein Abonnement ändern, ohne es zu löschen?  Erfahren Sie mehr über das [Bearbeiten von Abonnements](edit-license.md).
- Um ein bestimmtes Abonnement zu finden, informieren Sie sich unter [Suchen nach einem Abonnement](search-license.md).
- Müssen Sie eine Liste all Ihrer Abonnements erstellen?  Informationen dazu finden Sie unter [Exportieren von Abonnements](exporting-subscriptions.md).


