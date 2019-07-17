---
title: Verwenden des Administratorportals | Visual Studio Marketplace
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: conceptual
description: Erfahren Sie, wie Sie mithilfe des Administratorportals die Visual Studio-Abonnements Ihrer Organisation verwalten können.
ms.openlocfilehash: 6da1f0ce52e810a7652dd306ff5a6e44404b76f7
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67784790"
---
# <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>Verwenden des Administratorportals für Visual Studio-Abonnements

Beachten Sie beim Verwenden des Portals zur Verwaltung von Visual Studio-Abonnements Folgendes:

- **Visual Studio-Abonnements werden pro Benutzer lizenziert.** Die einzelnen Abonnenten können die Software zu Entwicklungs- und Testzwecken auf so vielen Computer wie nötig installieren.
- **Weisen Sie jedem Abonnenten nur eine Abonnementstufe zu**, entsprechend dem vom Unternehmen erworbenen Visual Studio-Abonnement. Wenn bei Ihnen Abonnenten vorhanden sind, denen mehrere Abonnementstufen zugewiesen sind, bearbeiten Sie die Einstellungen, sodass ihnen nur noch eine Stufe zugewiesen ist.
- **Die Abonnementstufe eines Abonnenten muss aktualisiert werden**, wenn für das Abonnement ein Upgrade (nach dem Kauf einer Step-up-Lizenz) oder eine Lizenzerneuerung mit einer niedrigeren Abonnementstufe erfolgt.
- **Weisen Sie ein Abonnement nicht mehreren Abonnenten zu.** Sie müssen jeder Person, die alle oder einige der Abonnementvorteile nutzt (Software für Entwicklung und Tests, Microsoft Azure, E-Learning usw.), ein Abonnement zuweisen.

## <a name="administrator-roles"></a>Administratorrollen

Im neuen Portal zur Verwaltung von Visual Studio-Abonnements für Volumenlizenz-Kunden existieren zwei verschiedene Rollen. Diese Rollen entsprechen den jetzigen Rollen des „primären Ansprechpartners“ und des „Abonnementverwalters“ im VLSC.

**Superadministratoren:** Nach dem ersten Einrichten einer Organisation erhält der primäre Ansprechpartner standardmäßig die Befugnisse eines Superadministrators. Der primäre Ansprechpartner kann dann weitere Superadministrator- oder Administratorrollen zuweisen. Ein Superadministrator kann andere Administratoren sowie Abonnenten hinzufügen und entfernen. Wenn im System mehr als zwei Superadministratoren existieren, kann jeder Superadministrator alle anderen bis auf die letzten zwei löschen, da diese aus Sicherheitsgründen nicht gelöscht werden können.

**Administratoren:** Administratoren können nur durch einen Superadministrator eingerichtet werden. Administratoren können Abonnenten innerhalb der Vereinbarungen verwalten, die der Superadministrator diesen zuweist.

## <a name="getting-started"></a>Erste Schritte

Damit Sie die Abonnements Ihrer Organisation über das Administratorportal verwalten können, müssen Sie Ihre Organisation zunächst in das Portal einbinden.  Sobald Sie das Onboarding abgeschlossen haben, machen Sie sich mit den Abonnenten- und Detailseiten vertraut, denn dort finden Sie die Tools und Informationen, die Sie für die Verwaltung Ihrer Abonnements benötigen.

### <a name="onboarding"></a>Onboarding

Sobald Ihre Organisation in das Portal zur Verwaltung von Visual Studio-Abonnements aufgenommen werden kann, werden die primären Ansprechpartner per E-Mail gebeten, den Onboardingprozess abzuschließen. Unten sind die zum Aufnehmen in das neue Portal erforderlichen Schritte genannt. Wenn Sie gerne schrittweise durch den Prozess geführt werden möchten, sehen Sie sich dieses [Video zum Administrator-Onboarding](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting) an, oder lesen Sie sich diesen [Supportartikel](https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "Visual Studio-Abonnements: Administrator-Migrationsprozess") durch.

1. **Die eigene öffentliche Kundennummer ermitteln und sich damit anmelden:**
    - Die E-Mail an die primären Ansprechpartner enthält jeweils einen persönlichen Link sowie die letzten drei Ziffern ihrer persönlichen öffentlichen Kundennummer (Public Customer Number, PCN). * 
    - Der primäre Ansprechpartner muss sich im VLSC anmelden, um die gesamte PCN zu erhalten. Dort stehen Anweisungen zum Ermitteln der PCN zur Verfügung. 
    - Nachdem die primären Ansprechpartner ihre jeweilige PCN ermittelt haben, müssen sie auf ihre persönlichen Links klicken, woraufhin sie zum Anmelden aufgefordert werden. Diese können sich mit ihrem Geschäfts-, Schul- oder Unikonto (sofern Ihre Organisation bei AAD registriert ist) oder einem Microsoft-Konto (MSA) einloggen (wenn Ihre Organisation nicht bei AAD registriert ist). 
    - Als Nächstes müssen sie die PCN eingeben. 
2. **Ihre Administratoren einrichten** Nach dem Eingeben der PCN werden sie im neuen System als Superadministratoren registriert und können weitere Superadministratoren und Administratoren (vormals „Abonnementverwalter“) hinzufügen. Dieser Vorgang sollte abgeschlossen worden sein, bevor Ihre Organisation migriert wird, um einem Zugriffsverlust vorzubeugen. 
3. **Auf das neue Portal zur Verwaltung von Abonnements zugreifen**  Nach der Migration Ihrer Organisation werden die neu hinzugefügten Superadministratoren und Administratoren per E-Mail gebeten, auf das neue Portal zuzugreifen und die Abonnements zu verwalten.  

> [!NOTE]
> Wenn die primären Kontakte oder Ansprechpartner mehr als eine E-Mail erhalten, bedeutet dies, dass sie mehrere PCNs besitzen. Sie müssen den Prozess mithilfe der persönlichen Links für die PCN abschließen, die jeweils in den E-Mails genannt werden.*

Wenn Sie dem neuen Portal zur Verwaltung von Visual Studio-Abonnements hinzugefügt werden müssen und nicht sicher sind, wer Ihr primärer Ansprechpartner ist, finden Sie diese Informationen nach dem Anmelden bei dem [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx). Lesen Sie das Thema [Ermitteln Ihres primären Kontakts](find-primary-contact.md), um eine Anleitung zum Ermitteln Ihres primären Ansprechpartners im VLSC zu erhalten.
Wenn Sie bereits Administratorrechte besitzen, können Sie direkt zum [Portal zur Verwaltung von Visual Studio-Abonnements](https://manage.visualstudio.com) wechseln.

### <a name="understanding-the-subscribers-page"></a>Grundlegendes zur Seite „Abonnenten“
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

### <a name="understanding-the-details-page"></a>Grundlegendes zur Seite „Details“
Weitere Informationen zu der Vereinbarung, die Ihnen gerade angezeigt wird, erhalten Sie auf der Registerkarte „Details“. Dort werden Vereinbarungsstatus, Einkaufskonto, Organisationsdetails, primäre Ansprechpartner (VLSC), Superadministratoren (falls vorhanden) und andere relevante Informationen angezeigt.
> [!div class="mx-imgBorder"]
> ![Details-Seite des Portals zur Verwaltung von Visual Studio-Abonnements](_img/using-admin-portal/details-page.png)
