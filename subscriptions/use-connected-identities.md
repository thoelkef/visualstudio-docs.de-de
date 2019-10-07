---
title: 'Vorgehensweise: Verwenden von verbundenen Microsoft-Konten und Azure Active Directory-Identitäten | Microsoft-Dokumentation'
author: evanwindom
ms.author: lank
manager: lank
ms.date: 09/27/2019
ms.topic: conceptual
robots: noindex, nofollow
description: Erfahren Sie, wie Sie mit verbundenen Microsoft-Konten und Azure Active Directory-Identitäten arbeiten.
ms.openlocfilehash: d0d30092f34a3cb17b41455612cd336af3e58d30
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686266"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Verwenden von verbundenen Identitäten in Visual Studio-Abonnements
Wenn Sie über Ihr Geschäfts-, Schul- oder Unikonto ein Visual Studio-Abonnement erhalten und Ihr Microsoft-Konto (MSA) zum Anmelden verwenden, verknüpft Ihr Abonnementadministrator möglicherweise Ihr MSA mit Ihrer Identität im Azure Active Directory (Azure AD) Ihrer Organisation.  Damit ändert sich der Zugriff auf einige der Vorteile, die in Ihrem Abonnement enthalten sind. 

## <a name="overview-of-connected-ids"></a>Übersicht über verbundene Identitäten
Organisationen setzen verstärkt auf Azure AD-basierte Identitäten, um verbesserte Sicherheitsfunktionen und Unterstützung für die automatisierte Verwaltung von Abonnements zu bieten.  Wenn Ihr Abonnement ein MSA wie z. B. @outlook.com oder eine andere persönliche E-Mail-Adresse verwendet, ändert Ihr Administrator möglicherweise die E-Mail-Adresse, mit der Sie sich anmelden, in Ihre Azure AD-Identität.  Damit ändert sich die Art und Weise, in der Sie sich beim Abonnentenportal unter https://my.visualstudio.com anmelden, aber möglicherweise nicht der Zugriff auf all Ihre Vorteile.  

Wenn Ihr Administrator Ihre MSA- und Azure AD-Identitäten verbindet, erhalten Sie eine E-Mail, in der Sie darüber informiert werden, dass Sie statt mit Ihrem MSA mit Ihrer Azure AD-Identität auf Ihr Visual Studio-Abonnement zugreifen müssen. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Zugreifen auf Vorteile bei Verwendung von Azure AD-Identitäten
Nachdem Ihr Administrator Ihr MSA mit Ihrer Azure AD-Identität verbunden hat, müssen Sie sich mit dieser Azure AD-Identität beim Abonnentenportal unter https://my.visualstudio.com anmelden, um auf Vorteile zuzugreifen, die Azure AD erfordern.  Dazu gehören:
- Visual Studio-IDE
- Azure DevOps
- Azure-Gutschriften

## <a name="how-to-access-benefits-using-your-msa"></a>Zugreifen auf Vorteile bei Verwendung eines MSA
Für viele der Vorteile, die in Visual Studio-Abonnements angeboten werden – z. B. Pluralsight, LinkedIn, CloudPilot und viele weitere –, erstellen Sie tatsächlich Benutzerkonten auf den Websites der entsprechenden Partner.  Bei diesen Konten sollten Sie weiterhin die Identität verwenden, die Sie beim Erstellen des Kontos verwendet haben.  Wenn Sie beispielsweise Ihre Pluralsight-Vorteile mit Ihrem MSA aktiviert haben, sollten Sie an Pluralsight-Schulungen weiterhin mit Ihrem MSA teilnehmen – unabhängig von der Identität, die Sie zum Anmelden beim Abonnentenportal verwenden.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Verwenden einer alternativen Identität für den Zugriff auf Ihr Abonnement
Wenn Sie Ihrem Visual Studio-Abonnement ein alternatives Konto hinzufügen, haben Sie Zugriff auf Abonnementvorteile wie Azure DevOps und Azure, obwohl Sie eine andere Identität als die dem Abonnement zugewiesene verwenden. In der Vergangenheit war diese Funktion nur verfügbar, wenn Ihr Visual Studio-Konto einem Microsoft-Konto zugewiesen war. Jetzt wurde diese Funktion auf Geschäfts-, Schul- oder Unikonten in Azure Active Directory (Azure AD) erweitert.  Weitere Informationen zur Verwendung alternativer Konten finden Sie im Artikel [Alternative Identitäten](vs-alternate-identity.md). 

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
### <a name="q-how-can-i-contact-my-admin-about-this"></a>Frage: Wie kontaktiere ich meinen Administrator zu diesem Thema?
Antwort:  Informationen zur Kontaktaufnahme mit Ihrem Administrator finden Sie im Artikel [Kontaktieren des Abonnementadministrators](contact-my-admin.md).  

## <a name="next-steps"></a>Nächste Schritte
Nachdem Ihr Administrator Ihr Azure AD-Konto und Ihr MSA verknüpft hat, ist es ratsam, sich davon zu überzeugen, dass Sie sich weiterhin beim [Abonnementportal](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmelden und auf Vorteile wie Azure DevOps, Visual Studio und Ihr Azure-Guthaben zugreifen können. 