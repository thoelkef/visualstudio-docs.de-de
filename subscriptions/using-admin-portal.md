---
title: Erste Schritte im Verwaltungsportal für Abonnements | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Erfahren Sie, wie Sie die Visual Studio-Abonnements Ihrer Organisation mit dem Verwaltungsportal für Abonnements verwalten.
ms.openlocfilehash: f3b11a0a0977fff8a6c89f565adffb1cac49e2ad
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605711"
---
# <a name="get-started-with-the-visual-studio-subscriptions-administration-portal"></a>Erste Schritte im Verwaltungsportal für Visual Studio-Abonnements
Beachten Sie beim Verwenden des Portals zur Verwaltung von Visual Studio-Abonnements Folgendes:
- **Visual Studio-Abonnements werden pro Benutzer lizenziert.** Die einzelnen Abonnenten können die Software zu Entwicklungs- und Testzwecken auf so vielen Computer wie nötig installieren.
- **Weisen Sie jedem Abonnenten nur eine Abonnementstufe zu**, entsprechend dem vom Unternehmen erworbenen Visual Studio-Abonnement. Wenn bei Ihnen Abonnenten vorhanden sind, denen mehrere Abonnementstufen zugewiesen sind, bearbeiten Sie die Einstellungen, sodass ihnen nur noch eine Stufe zugewiesen ist.
- **Die Abonnementstufe eines Abonnenten muss aktualisiert werden**, wenn für das Abonnement ein Upgrade (nach dem Kauf einer Step-up-Lizenz) oder eine Lizenzerneuerung mit einer niedrigeren Abonnementstufe erfolgt.
- **Weisen Sie ein Abonnement nicht mehreren Abonnenten zu.** Abonnements müssen benannten Personen zugewiesen werden.  Die Zuweisung von Abonnements zu Teams ist nicht zulässig.  Sie müssen jeder Person, die alle oder einige der Abonnementvorteile nutzt (Software für Entwicklung und Tests, Microsoft Azure, E-Learning usw.), ein Abonnement zuweisen.

## <a name="access-to-the-portal"></a>Zugriff auf das Portal
Wenn Sie der primäre Kontakt für die Vereinbarung Ihrer Organisation sind, erhalten Sie automatisch Zugriff auf das Portal, sobald der Volumenlizenzvertrag in Kraft getreten ist. Sie erhalten eine vom System ausgelöste Willkommens-E-Mail, in der Sie darüber informiert werden, welche E-Mail-Adresse für die Anmeldung beim Portal verwendet werden muss. Sobald Sie angemeldet sind, haben Sie automatisch Berechtigungen als Superadministrator und können Abonnements und andere Administratoren verwalten. 

## <a name="administrator-roles"></a>Administratorrollen
Im neuen Portal zur Verwaltung von Visual Studio-Abonnements für Volumenlizenz-Kunden existieren zwei verschiedene Rollen. Diese Rollen entsprechen den jetzigen Rollen des „primären Ansprechpartners“ und des „Abonnementverwalters“ im VLSC.

**Superadministratoren:** Nach dem ersten Einrichten einer Organisation erhält der primäre Ansprechpartner standardmäßig die Befugnisse eines Superadministrators. Der primäre Kontakt kann weitere Superadministratoren oder Administratoren zuweisen. Ein Superadministrator kann andere Administratoren sowie Abonnenten hinzufügen und entfernen. Wenn im System mehr als zwei Superadministratoren existieren, kann jeder Superadministrator alle anderen bis auf die letzten zwei löschen, da diese aus Sicherheitsgründen nicht gelöscht werden können.

**Administratoren:** Administratoren können nur durch einen Superadministrator eingerichtet werden. Administratoren können Abonnenten innerhalb der Vereinbarungen verwalten, die der Superadministrator diesen zuweist.

## <a name="the-subscribers-page"></a>Die Seite „Abonnenten“
Sobald Sie Abonnements zugewiesen haben, erhalten Sie auf der Registerkarte „Abonnenten“ ausführliche Informationen zu Ihren Abonnenten, z.B.:
- Die Vor- und Nachnamen der einzelnen Abonnenten
- Die E-Mail-Adresse dieses Benutzers
- Die Abonnementstufe, die ihm zugewiesen wurde
- Das Datum, an dem das Abonnement zugewiesen wurde
- Das Ablaufdatum des Abonnements
- Eine optionale Beschreibung in Textform
- Ein Hinweis, ob „Downloads für Abonnenten“ aktiviert oder deaktiviert wurde
- Das Land, in dem der Benutzer sich befindet
- Die Sprache, in der der Benutzer die durch das Verwaltungsportal versendete Zuweisungs-E-Mail erhalten möchte
- Ein optionales Feld für eine weitere E-Mail-Adresse, die zur E-Mail-Kommunikation, aber nicht zum Einloggen genutzt wird

Auf dieser Seite können Sie links zusätzliche Informationen zur Anzahl der in Ihrer Organisation für jede Vereinbarung erworbenen, zugewiesenen und noch verfügbaren Abonnementlizenzen einsehen.
> [!div class="mx-imgBorder"]
> ![Seite „Abonnenten“ des Portals zur Verwaltung von Visual Studio-Abonnements](_img/using-admin-portal/subscribers-page.png)

## <a name="the-details-page"></a>Die Seite „Details“
Weitere Informationen zu der Vereinbarung, die Ihnen gerade angezeigt wird, erhalten Sie auf der Registerkarte „Details“. Dort werden Vereinbarungsstatus, Einkaufskonto, Organisationsdetails, Superadministratoren und weitere relevante Informationen angezeigt.
> [!div class="mx-imgBorder"]
> ![Details-Seite des Portals zur Verwaltung von Visual Studio-Abonnements](_img/using-admin-portal/details-page.png)

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu den Aufgaben von Administratoren:
- [Übersicht über die Aufgaben eines Administrators](admin-responsibilities.md)
- [Inventory of pre-production environment (Inventur der Präproduktionsumgebung)](admin-inventory.md)
- [Verwalten von großen Teams und externen Vertragspartnern](manage-teams.md)
- [Nachverfolgen von Benutzerzuweisungen und Verarbeiten von Bestellungen](assignments-orders.md)
- Verwenden des Berichts [Maximum Usage](maximum-usage.md) (Maximale Auslastung) zum Nachverfolgen von Kaufverpflichtungen
