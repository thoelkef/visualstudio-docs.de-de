---
title: Probleme beim Anmelden bei Visual Studio-Abonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 03/11/2020
ms.topic: conceptual
description: In diesem Artikel erfahren Sie etwas über Probleme, die bei der Anmeldung bei Visual Studio-Abonnements auftreten können.
ms.openlocfilehash: 5d8a71115cd1a1aa7d850945806c22a64e7721cc
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801879"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Probleme beim Anmelden bei Visual Studio-Abonnements
Um Ihr Visual Studio-Abonnement zu nutzen, müssen Sie sich zuerst anmelden.  Je nach Abonnement haben Sie es entweder mit einem Microsoft-Konto (MSA) oder einer Azure Active Directory-Identität (AAD) eingerichtet.  In diesem Artikel werden einige der Probleme besprochen, die beim Anmelden bei Ihrem Abonnement auftreten können.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Microsoft-Konten (MSA) können nicht mit Geschäfts-, Schul- oder Uni-E-Mail-Adressen erstellt werden
Ein neues persönliches Microsoft-Konto (MSA) mit einer Geschäfts-, Schul- oder Uni-E-Mail-Adresse zu erstellen, ist nicht länger zulässig, wenn die E-Mail-Domäne in Azure AD konfiguriert wurde. Was bedeutet dies? Wenn Ihre Organisation Microsoft 365 oder andere Unternehmensdienste von Microsoft verwendet, die auf Azure AD basieren, und Sie einen Domänennamen zu Ihrem Azure AD-Mandanten hinzugefügt haben, können Benutzer kein neues persönliches Microsoft-Konto mit einer E-Mail-Adresse in Ihrer Domäne mehr erstellen.

### <a name="why-was-this-change-made"></a>Warum wurde diese Änderung vorgenommen?
Über ein persönliches Microsoft-Konto mit einer Arbeitsadresse als Benutzername zu verfügen, stellt sowohl Endbenutzer als auch IT-Abteilungen vor Probleme. Beispiel:
- Benutzer könnten denken, dass ihr persönliches Microsoft-Konto unternehmenskonform ist und sie sich an die Unternehmensrichtlinie halten, wenn sie geschäftliche Dokumente auf ihrem OneDrive speichern.
- Benutzer, die eine Organisation verlassen, verlieren in der Regel den Zugriff auf ihre geschäftliche E-Mail-Adresse. In diesem Fall können sie sich nicht mehr bei ihrem persönlichen Microsoft-Konto anmelden, wenn sie ihr Kennwort vergessen. Die Kehrseite davon ist, dass die IT-Abteilung ihr Kennwort zurücksetzen und so in die persönlichen Konten ehemaliger Mitarbeiter gelangen könnte.
- IT-Abteilungen haben eine falsche Vorstellung von Kontoeigentum und -sicherheit. Aber Benutzer müssen nur einmal einen Code an ihre geschäftliche E-Mail-Adresse senden und können ihr Konto dann zu einem beliebigen Zeitpunkt in der Zukunft umbenennen.

Die Situation ist besonders verwirrend bei Benutzern, die über zwei Konten mit denselben E-Mail-Adressen verfügen (eine in Azure AD und ein Microsoft-Konto).

### <a name="what-does-this-experience-look-like"></a>Wie sieht diese Benutzeroberfläche aus?
Wenn Sie versuchen, sich bei einer Microsoft-Verbraucher-App mit einer Geschäfts-, Schul- oder Uni-E-Mail-Adresse anzumelden, wird die untenstehende Meldung angezeigt.

   > [!div class="mx-imgBorder"]
   > ![Konto kann nicht mit geschäftlicher E-Mail-Adresse erstellt werden](_img/sign-in-issues/cannot-use-work-email.png)

Wenn Sie jedoch versuchen, sich bei einer Microsoft-App anzumelden, die persönliche sowie Geschäfts-, Schul- und Uni-Konten unterstützt, sollte folgende Meldung erscheinen:

   > [!div class="mx-imgBorder"]
   > ![Geschäfts-, Schul- und Uni-Konten werden unterstützt](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Sind bestehende Konten davon betroffen?
Die hier beschriebene Blockierung der Anmeldung verhindert nur die Erstellung neuer Konten. Sie wirkt sich nicht auf Benutzer aus, die bereits über ein Microsoft-Konto mit einer Geschäfts-, Schul- oder Uni-E-Mail-Adresse verfügen. Falls Sie bereits in dieser Situation sind, haben wir das Umbenennen eines persönlichen Microsoft-Kontos vereinfacht. Dieser [Support-Artikel](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) enthält eine einfache Schritt-für-Schritt-Anleitung. Das Umbenennen Ihres persönlichen Microsoft-Kontos bedeutet, dass der Benutzername geändert wird, und hat keine Auswirkung auf Ihre geschäftlichen E-Mails oder auf die Art und Weise, wie Sie sich bei Unternehmensdiensten wie Microsoft 365 anmelden. Es hat auch keine Auswirkung auf Ihre persönlichen Angelegenheiten. Es ändert sich nur die Art und Weise, wie Sie sich anmelden. Sie können eine andere (persönliche) E-Mail-Adresse verwenden, eine neue @outlook.com-E-Mail-Adresse von Microsoft anfordern oder Ihre Telefonnummer als neuen Benutzernamen verwenden.

> [!NOTE]
> Wenn Ihre IT-Abteilung Sie darum gebeten hat, ein persönliches Microsoft-Konto mit Ihrer Geschäfts-, Schul- oder Uni-E-Mail-Adresse zu erstellen, um zum Beispiel auf Microsoft-Unternehmensdienste wie Premier Support zuzugreifen, sollten Sie zuerst mit Ihrem Administratorenteam sprechen, bevor Sie Ihr Konto umbenennen.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Das Löschen einer Anmeldeadresse kann den Zugriff auf ein Abonnement verhindern
Wenn Sie eine oder mehrere Identitäten (MSA oder AAD) löschen, die mit Ihrem Abonnement verbunden sind, können Ihre Abonnenteninformationen einschließlich Benutzername und Anmelde-ID anonymisiert werden, wodurch Sie den Zugriff auf Ihr Abonnement verlieren.

Um Auswirkungen auf Ihren Abonnementzugriff zu vermeiden, können Sie eine der folgenden Methoden verwenden.
- Stellen Sie ein einziges Identitätsverwaltungssystem bereit – entweder MSA oder AAD, aber nicht beide.
- Ordnen Sie die AAD- und MSA-Identitäten über den Mandanten zu.

## <a name="signing-in-may-fail-when-using-aliases"></a>Anmeldefehler bei der Verwendung von Aliasen
Abhängig vom für die Anmeldung verwendeten Kontotyp werden verfügbare Abonnements möglicherweise nicht ordnungsgemäß angezeigt, wenn Benutzer sich bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmelden. Eine mögliche Ursache ist die Verwendung von „Aliasen“ oder „Anzeigenamen“ anstelle der Anmeldeidentität, der das Abonnement zugewiesen ist. Dieser Vorgang wird als „Aliasing“ bezeichnet.

### <a name="what-is-aliasing"></a>Was ist Aliasing?
Der Begriff „Aliasing“ bezieht sich auf Benutzer, die über verschiedene Identitäten für die Anmeldung bei Windows (oder Ihrem Active Directory) und den Zugriff auf E-Mails verfügen.

Aliasing kann auftreten, wenn ein Unternehmen über einen Microsoft Online Service für die Verzeichnisanmeldung verfügt, wie z.B. JohnD@contoso.com, aber Benutzer auf ihre E-Mail-Konten über Aliase oder Anzeigenamen, z.B. John.Doe@contoso.com, zugreifen. Für viele Kunden, die ihre Abonnements über das Volume Licensing Service Center (VLSC) verwalten, kann dies zu einer erfolglosen Anmeldung führen. Dies liegt daran, dass die angegebene E-Mail-Adresse (John.Doe@contoso.com) nicht mit der Verzeichnisadresse (JohnD@contoso.com) übereinstimmt, die für eine erfolgreiche Authentifizierung über die Option „Geschäfts-, Schul- oder Unikonto“ erforderlich ist.

### <a name="what-options-do-i-have"></a>Welche Optionen stehen mir zur Verfügung?
Als Abonnent sollten Sie sich zunächst unbedingt an Ihren Administrator wenden, um sich mit dem Identitätskonfiguration für Ihr Unternehmen vertraut zu machen. Gegebenenfalls muss der Administrator Ihre Kontoeinstellungen von seinem Verwaltungsportal aus aktualisieren, oder Sie müssen ein Microsoft-Konto (MSA) mit Ihrer Firmen-E-Mail-Adresse erstellen. Bevor Sie die Schritte zur Erstellung eines MSA ausführen, sprechen Sie mit Ihrem Administrator über Richtlinien oder Probleme bei der Durchführung dieser Aktion. 

## <a name="see-also"></a>Weitere Informationen
- [Dokumentation zu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentation zu Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Azure-Dokumentation](https://docs.microsoft.com/azure/)
- [Dokumentation zu Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
- Weitere Informationen zum Verknüpfen von MSA- und AAD-Konten innerhalb von AAD finden Sie unter [Hinzufügen von Azure Active Directory B2B-Zusammenarbeitsbenutzern über das Azure-Portal](/azure/active-directory/b2b/add-users-administrator).
- Weitere Informationen zur Anonymisierung finden Sie unter [Anonymization of Visual Studio subscriber information (Anonymisierung von Visual Studio-Abonnenteninformationen)](anonymization.md).
