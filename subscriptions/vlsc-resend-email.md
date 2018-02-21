---
title: "Visual Studio-Abonnements – Erneutes Senden von Zuweisungs-E-Mails aus dem VLSC"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend subscription assignment emails from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 338ae08ee1f3e6a819a1faea7bd095c9acd8ecd2
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/16/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-within-volume-license-service-center-vlsc"></a>Erneutes Senden von Zuweisungs-E-Mails aus dem Volume Licensing Service Center (VLSC)

Gelegentlich wird ein Abonnent, dem ein Abonnement zugewiesen wurde, einen Administrator bitten, die Benachrichtigungs-E-Mail für die Zuweisung des Abonnements erneut zu senden.  Im neuen Portal für die Abonnementverwaltung, https://manage.visualstudio.com, ist dies ein einfacher Vorgang.  Wenn Ihre Organisation jedoch weiterhin das Volume Licensing Service Center (VLSC) nutzt, steht keine Funktion für das automatische erneute Senden der Benachrichtigungs-E-Mail zur Verfügung.  

Um die Benachrichtigungs-E-Mail für die Zuweisung aus dem VLSC erneut zu senden, muss Ihr Administrator auf die folgende Problemumgehung zurückgreifen:

## <a name="resending-the-assignment-email"></a>Erneutes Senden der E-Mail für die Zuweisung

Damit im VLSC eine neue Benachrichtigung generiert wird, müssen Sie die E-Mail-Informationen zum Abonnenten einmalig ändern und in derselben Transaktion wieder in die ursprüngliche E-Mail-Adresse ändern. Dies löst im VLSC dieselbe Reaktion aus wie bei der Zuweisung eines neuen Abonnements, und die E-Mail für die Zuweisung wird erneut gesendet.

1.  Rufen Sie das [Volume Licensing Service Center (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) auf, und melden Sie sich an.
2.  Klicken Sie auf die Registerkarte **Abonnements** und anschließend auf **Visual Studio-Abonnements**.
3.  Klicken Sie auf die mit dem Visual Studio-Abonnement verknüpfte **Vertragsnummer**.
4.  Klicken Sie in der Suchleiste auf den Abwärtspfeil. 
5.  Suchen Sie über das Feld **E-Mail-Adresse** nach dem Abonnenten.
6.  Suchen Sie den Abonnenten in den Suchergebnissen, und klicken Sie auf den Nachnamen. 
7.  Klicken Sie auf **Bearbeiten**.
8.  Nehmen Sie eine Bearbeitung am Abonnement vor. Entfernen Sie z.B. ein Zeichen aus der E-Mail-Adresse des Abonnenten. Klicken Sie auf die Schaltfläche **Speichern**.
9.  Klicken Sie nach dem Speichern der Informationen erneut auf **Bearbeiten**, machen Sie die soeben vorgenommene Änderung wieder rückgängig, und klicken Sie auf **Speichern**.  

Dies bewirkt, dass das Abonnement als eine neue Zuweisung betrachtet wird, und die Benachrichtigungs-E-Mail für die Zuweisung wird erneut an den Abonnenten gesendet.  