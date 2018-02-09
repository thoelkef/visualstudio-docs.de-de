---
title: 'Gewusst wie: Erneutes Senden von Abonnementzuweisungs-E-Mails aus dem VLSC | Microsoft-Dokumentation'
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 12/29/2017
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to a subscriber from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 7162435044a578a94249774305f2c6b8b6438219
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-vlsc"></a>Erneutes Senden von Abonnementzuweisungs-E-Mails aus dem VLSC:

Wenn ein Abonnement einem Abonnenten im VLSC zugewiesen wurde und der Abonnent das erneute Senden der Zuweisungs-E-Mail anfordert, können Sie hierzu die E-Mail-Daten des Abonnenten bearbeiten und dann wieder in die ursprüngliche Adresse ändern. Dadurch wird das erneute Senden der Zuweisungs-E-Mail automatisch ausgelöst.

Befolgen Sie die folgenden Anweisungen, um die Zuweisungs-E-Mail erneut zu senden:


1. Rufen Sie das Volume Licensing Service Center (VLSC) auf, und melden Sie sich an.
2. Klicken Sie auf der VLSC-Administratorseite auf **Abonnements** und dann auf **Visual Studio-Abonnements**.
3. Klicken Sie auf die mit dem Visual Studio-Abonnement verknüpfte **Vertragsnummer**.
4. Klicken Sie in der **Suchleiste** auf den Abwärtspfeil.  
5. Suchen Sie über das Feld „E-Mail-Adresse“ nach dem Abonnenten.
6. Klicken Sie in der Ergebnisliste auf den **Nachnamen** des Abonnenten.
7. Klicken Sie auf **Bearbeiten**.
8. Nehmen Sie eine Bearbeitung am Abonnement vor. Welche Änderung Sie vornehmen, spielt keine Rolle – es muss nur etwas geändert werden.  Entfernen Sie z.B. ein Zeichen aus der E-Mail-Adresse des Abonnenten, wie etwa das „m“ aus „.com“. Klicken Sie auf die Schaltfläche **Speichern**.
9. Sobald die Daten gespeichert sind, klicken Sie erneut auf die Schaltfläche **Bearbeiten**, und korrigieren Sie das fehlende Zeichen in der E-Mail. Klicken Sie auf **Speichern**.
   
So erkennt das VLSC, dass Änderungen am Abonnement vorgenommen wurden, und sendet die Zuweisungs-E-Mail erneut an die im Portal aufgelistete E-Mail-Adresse. 

> [!NOTE]
> - Neu zugewiesene Abonnements generieren die Zuweisungs-E-Mail automatisch. Das oben Beschriebene ist nur erforderlich, wenn ein Benutzer eine neue Zuweisungs-E-Mail-Benachrichtigung anfordert, oder die Benachrichtigung aus irgendeinem Grund nicht gesendet wurde.
> - Dieses Verfahren ist nicht erforderlich, um Zuweisungs-E-Mails für Abonnements erneut zu senden, die über „https://manage.visualstudio.com“ zugewiesen wurden.  Um Zuweisungs-E-Mails erneut an Abonnenten im Portal zu senden, wählen Sie die Abonnenten einfach aus und klicken am oberen Rand der Liste der Abonnenten auf die Schaltfläche **Erneut senden**.  