---
title: Inventur von Präproduktionsumgebungen | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/17/2020
ms.topic: conceptual
description: Hier erfahren Sie mehr über die Aufgaben eines Administrators bei der Inventur der Präproduktionsumgebung.
ms.openlocfilehash: 6d7dd3b49c11e94ffa09bc07bd745582f348763d
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476740"
---
# <a name="inventory-of-pre-production-environment"></a>Inventur der Präproduktion
Visual Studio-Abonnements vereinfachen das Ressourcenmanagement, indem die Anzahl der Benutzer und nicht die der Geräte im Vordergrund steht.

Visual Studio-Administratoren müssen Visual Studio-Abonnements **bestimmten Personen** zuweisen. Namenskonventionen wie „Dev1“, „Dev2“ oder die Verwendung von Teamnamen wie „FeatureTeam“ sind **nicht zulässig**.

Im Folgenden werden einige Möglichkeiten aufgelistet, um das Inventar Ihrer Präproduktionsumgebung zu vereinfachen:
- Prüfen Sie die Benutzerzuweisungen. Es gibt eine Website von Microsoft mit dem Namen [Visual Studio Administration Portal (Visual Studio-Administrationsportal)](https://manage.visualstudio.com/), die Ihnen dabei helfen soll, die Zuweisungen von Visual Studio-Abonnements nachzuverfolgen.
- Verwenden Sie eine lokale oder cloudbasierte Version von Active Directory, um Benutzer aufzulisten. Wenn Sie Active Directory verwenden, um den Benutzerzugriff zu verwalten, können Sie möglicherweise Entwicklungs- und Testbenutzer anhand Ihrer Directory-Mitgliedschaft erkennen.
- Verwenden Sie automatisierte Tools, um eine Inventur für Systeme durchzuführen. Möglicherweise müssen Sie auch ein Tool für die Softwareinventur verwenden, um Ihre Softwareobjekte besser verwalten und Präproduktionsumgebungen von Produktionsumgebungen unterscheiden zu können. Viele Kunden des Microsoft System Center erstellen Namenskonventionen, um die Automatisierung dieses Teils des Inventurprozesses voranzubringen.
- Lassen Sie sich bei der manuellen Abstimmung helfen. Erstellen Sie eine Liste Ihrer Mitarbeiter, damit Sie die Entwicklungs- und Testbenutzer auf die Entwicklungs- und Testumgebungen abstimmen können.

## <a name="resources"></a>Ressourcen
- [Whitepaper zur Lizenzierung von Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Nutzungsbedingungen für die Volumenlizenzierung](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu den Aufgaben von Administratoren:
- [Administratoraufgaben](admin-responsibilities.md)
- [Verwalten von großen Teams und externen Vertragspartnern](manage-teams.md)
- [Nachverfolgen von Benutzerzuweisungen und Verarbeiten von Bestellungen](assignments-orders.md)
- Verwenden der [maximalen Auslastung](maximum-usage.md) zum Nachverfolgen von Kaufverpflichtungen

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentation zu Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Microsoft 365](https://docs.microsoft.com/microsoft-365/)

