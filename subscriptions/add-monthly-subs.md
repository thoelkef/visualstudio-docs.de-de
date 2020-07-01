---
title: Hinzufügen neuer Visual Studio-Monatsabonnements zum Verwaltungsportal für Abonnements| Microsoft-Dokumentation
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 06/23/2020
ms.topic: conceptual
description: Erfahren Sie, wie Sie neu erworbene Visual Studio-Monatsabonnements zum Verwaltungsportal für Abonnements hinzufügen
ms.openlocfilehash: abe0b7a84f0979de4bc1f59b6f82144c804c8c7e
ms.sourcegitcommit: 60315ba949aca1ff06fe431dbcbcfb0fedc1e8d3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85307094"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Hinzufügen neuer Visual Studio-Monatsabonnements zum Verwaltungsportal für Abonnements
Wenn Sie unter Verwendung eines Azure-Abonnements neue Visual Studio-Monatsabonnements erwerben, müssen Sie diese gegebenenfalls zum Verwaltungsportal für Abonnements hinzufügen, um sie Benutzern zuweisen zu können.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Woher weiß ich, ob ich meine Abonnements hinzufügen muss?
Ob bzw. welche Schritte zum Hinzufügen von Monatsabonnements ausgeführt werden müssen, hängt von der Art der Abonnements ab, über die Ihre Organisation bereits verfügt, sowie davon, ob Sie ein neuer Administrator sind.
- Wenn Sie sich als neuer Administrator erstmalig beim Verwaltungsportal für Abonnements anmelden, überprüfen wir, für welche Azure-Abonnements Sie über die Berechtigung „Benutzerzugriffsadministrator“ verfügen.  Wenn Monatsabonnements gefunden werden, werden sie automatisch hinzugefügt. 
- Wenn Sie zuvor Monatsabonnements hinzugefügt oder verwaltet haben, überprüfen wir bei jeder Anmeldung, ob neue Monatsabonnements vorhanden sind. 
- Wenn Sie bereits Administrator von Abonnements sind, die über die Volumenlizenzierung erworben wurden, jedoch noch keine Monatsabonnements hinzugefügt oder verwaltet haben, müssen Sie diese Abonnements über die unten beschriebenen Schritte hinzufügen.

## <a name="how-to-add-monthly-subscriptions"></a>Hinzufügen von Monatsabonnements
1. Melden Sie sich beim Verwaltungsportal für Abonnements unter <https://manage.visualstudio.com> an
1. Wählen Sie auf der Registerkarte **Abonnenten verwalten** die Dropdownliste **Neuer Vertrag** aus 
1. Wählen Sie in der Liste **Neue Monatsabonnements**  aus
   > [!div class="mx-imgBorder"]
   > ![Dropdownliste zum Hinzufügen neuer Monatsabonnements](_img/add-monthly-subs/add-subs-drop-down.png)
1. Das System sucht nach Azure-Abonnements, für die Sie über die Berechtigung „Benutzerzugriffsadministrator“ verfügen, und importiert die Visual Studio-Abonnements, die mit diesen Azure-Abonnements erworben wurden.
1. Wenn keine Azure-Abonnements gefunden werden, für die Sie über die Berechtigung „Benutzerzugriffsadministrator“ verfügen, bzw. wenn entsprechende Azure-Abonnements, jedoch keine Visual Studio-Abonnements gefunden werden, wird die folgende Meldung angezeigt:
   > [!div class="mx-imgBorder"]
   > ![Keine neuen Monatsabonnements gefunden](_img/add-monthly-subs/no-subs-found.png)
1. Wenn neue Monatsabonnements gefunden werden, wird eine Bestätigungsmeldung angezeigt
   > [!div class="mx-imgBorder"]
   > ![Bestätigungsmeldung für das Hinzufügen von Abonnements](_img/add-monthly-subs/subs-added-confirmation.png)

## <a name="things-to-keep-in-mind"></a>Bitte beachten
- Die Option zum Hinzufügen neuer Monatsabonnements ist erst verfügbar, wenn Sie erstmalig ein solches Abonnement erwerben.  Nachdem Sie Monatsabonnements hinzugefügt haben, überprüfen wir jedes Mal, wenn Sie sich beim Portal anmelden, ob neue Abonnements vorhanden sind. 
- Wenn neue Abonnements gefunden werden, sind diese möglicherweise bereits Abonnenten zugewiesen.  Der Grund dafür ist, dass auch andere Administratoren auf das Azure-Abonnement zugreifen können, und diese Administratoren die neuen Visual Studio-Abonnements bereits Benutzern zugewiesen haben.  Nachdem Sie die Abonnements zu Ihrem Portal hinzugefügt haben, können Sie sie verwalten. 

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie Abonnements hinzugefügt haben, können Sie sie Benutzern zuweisen.  Dazu haben Sie verschiedene Möglichkeiten:
- [Zuweisen von Abonnements zu einzelnen Benutzern](assign-license.md)
- [Zuweisen von Abonnements zu mehreren Benutzern](assign-license-bulk.md)
- [Zuweisen bestimmter Abonnements zu bestimmten Benutzern](assign-guid.md)

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentation zu Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Microsoft 365](https://docs.microsoft.com/microsoft-365/)
