---
title: Mögliche Fehler beim Anmelden bei Visual Studio-Abonnements bei Verwendung von Aliasen | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Mögliche Fehler beim Anmelden, wenn Aliase oder Anzeigenamen verwendet werden.
ms.openlocfilehash: 392b86699b1116f45ca75df3b611fff6a2aebc62
ms.sourcegitcommit: 485881e6ba872c7b28a7b17ceaede845e5bea4fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2019
ms.locfileid: "68378024"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Mögliche Fehler beim Anmelden bei Visual Studio-Abonnements bei Verwendung von Aliasen
Abhängig vom für die Anmeldung verwendeten Kontotyp werden verfügbare Abonnements möglicherweise nicht ordnungsgemäß angezeigt, wenn Benutzer sich bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmelden. Eine mögliche Ursache ist die Verwendung von „Aliasen“ oder „Anzeigenamen“ anstelle der Anmeldeidentität, der das Abonnement zugewiesen ist. Dieser Vorgang wird als „Aliasing“ bezeichnet.

## <a name="what-is-aliasing"></a>Was ist Aliasing?
Der Begriff „Aliasing“ bezieht sich auf Benutzer, die über verschiedene Identitäten für die Anmeldung bei Windows (oder Ihrem Active Directory) und den Zugriff auf E-Mails verfügen.

Aliasing kann auftreten, wenn ein Unternehmen über einen Microsoft Online-Dienst für die Verzeichnisanmeldung verfügt (z. B. JohnD@contoso.com), aber Benutzer auf ihre E-Mail-Konten über Aliase oder Anzeigenamen (z. B. John.Doe@contoso.com) zugreifen. Für viele Kunden, die ihre Abonnements über das Volume Licensing Service Center (VLSC) verwalten, kann dies zu einer erfolglosen Anmeldung führen. Das liegt daran, dass die angegebene E-Mail-Adresse (John.Doe@contoso.com) nicht mit der Verzeichnisadresse (JohnD@contoso.com) übereinstimmt, die für eine erfolgreiche Authentifizierung über die Option „Geschäfts-, Schul- oder Unikonto“ erforderlich ist.

## <a name="as-an-administrator-what-options-do-i-have"></a>Welche Möglichkeiten habe ich als Administrator?
Als Administrator haben Sie zwei Möglichkeiten, um sicherzustellen, dass die Anmeldung Ihrer Abonnenten bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) erfolgreich ist.
- Die erste (empfohlene) Option ist die Nutzung des Verzeichniskontos als zugewiesene Adresse im Volume Licensing Service Center (VLSC). Weitere Informationen hierzu finden Sie in diesem Artikel im Abschnitt [Zuweisen von Abonnenten zu einem Verzeichniskonto](#assigning-subscribers-to-a-directory-account).
- Die zweite (weniger sichere) Option erlaubt es Ihren Abonnenten, ihre Geschäfts-, Schul- oder Uni-E-Mail-Adresse mit einem „persönlichen“ Konto zu verknüpfen (auch Microsoft-Konto oder Microsoft Account (MSA) genannt). Weitere Informationen hierzu finden Sie in diesem Artikel im Abschnitt [Festlegen eines Geschäfts-, Schul- oder Unikontos als persönliches Konto](#defining-a-work-or-school-account-as-a-personal-account).

> [!NOTE]
> Sobald Ihr Unternehmen zum neuen [Verwaltungsportal](https://manage.visualstudio.com) für Visual Studio-Abonnements migriert ist, können Sie die Vorteile der neuen Administrationsfunktionen nutzen. Mit diesen können Sie sowohl Verzeichnis- als auch E-Mail-Adressen als Teil des Abonnentenprofils angeben. In diesem Artikel finden Sie weitere Informationen zur [Migration](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="assigning-subscribers-to-a-directory-account"></a>Zuweisen von Abonnenten zu einem Verzeichniskonto
In jedem Fall muss der Abonnement-Manager im Volume Licensing Service Center (VLSC) die Verzeichnisadresse für neue Abonnenten verwenden oder die E-Mail-Adresse für „vorhandene“ Abonnenten aktualisieren. Dabei ist zu beachten, dass bei Verwendung der Verzeichnisadresse neue Abonnenten keine Begrüßungs-E-Mail erhalten und der Administrator die Abonnenten darüber informieren muss, dass ihnen ein Abonnement zugewiesen wurde. Nachdem Sie die folgenden Schritte ausgeführt haben, können Sie auch die [E-Mail-Vorlage](#notifying-your-subscribers-with-directory-addresses) verwenden, um Ihre Abonnenten zu benachrichtigen und ihnen bei der Anmeldung zu helfen.

### <a name="adding-new-subscribers"></a>Hinzufügen neuer Abonnenten
Führen Sie die folgenden Schritte aus, um einen neuen Abonnenten mit einem Verzeichniskonto hinzuzufügen.

1. Besuchen Sie das [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC), und melden Sie sich an.
2. Klicken Sie auf der VLSC-Administratorseite auf **Abonnements** und dann auf **Visual Studio-Abonnements**.

    > [!div class="mx-imgBorder"]
    > ![Menü „Abonnements“](_img//vlsc/vlsc-subscriptions.png)

3. Klicken Sie auf die mit dem Visual Studio-Abonnement verknüpfte **Vertragsnummer**.

    > [!div class="mx-imgBorder"]
    > ![Auswählen der Vereinbarung](_img/vlsc/vlsc-agreement.png)

4. Klicken Sie auf **Abonnement zuweisen**.
5. Wählen Sie die gewünschte **Abonnementstufe**.
6. Stellen Sie sicher, dass Abonnements für eine Zuweisung vorhanden sind, und klicken Sie auf **Weiter**.
7. Geben Sie die Abonnentendetails und die Verzeichnisadresse im Feld „E-Mail-Adresse“ ein, und klicken Sie auf **Weiter**.
8. Überprüfen Sie die Abonnenteninformationen, und klicken Sie auf **Fertig stellen**.
9. Benachrichtigen Sie den Abonnenten mithilfe der folgenden [Vorlage](#notifying-your-subscribers-with-directory-addresses) darüber, dass sein Abonnement bereitgestellt wurde.

### <a name="updating-an-existing-subscriber"></a>Aktualisieren eines vorhandenen Abonnenten
Führen Sie die folgenden Schritte aus, um einen vorhandenen Abonnenten mit einem Verzeichniskonto zu aktualisieren.

1. Besuchen Sie das [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC), und melden Sie sich an.
2. Klicken Sie auf der VLSC-Administratorseite auf **Abonnements** und dann auf **Visual Studio-Abonnements**.
3. Klicken Sie auf die mit dem Visual Studio-Abonnement verknüpfte **Vertragsnummer**.
4. Klicken Sie in der Suchleiste auf den **Abwärtspfeil**.
5. Suchen Sie über das Feld „E-Mail-Adresse“ nach dem Abonnenten.
6. Klicken Sie in der Ergebnisliste auf den **Nachnamen** des Abonnenten.
7. Klicken Sie auf **Bearbeiten**.
8. Ändern Sie die Eingabe im Feld für die E-Mail-Adresse in die gewünschte Verzeichnisadresse, und klicken Sie auf **Speichern**.
9. Benachrichtigen Sie den Abonnenten mithilfe der folgenden E-Mail-Vorlage darüber, dass sein Abonnement bereitgestellt wurde.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Benachrichtigen Ihrer Abonnenten mit Verzeichnisadressen
Da die Begrüßungs-E-Mail Ihren Abonnenten nicht erfolgreich erreichen wird, kopieren Sie die unten stehende Nachricht, um diese in einer E-Mail an den Abonnenten zu senden. Ersetzen Sie „%WORT%“ durch die entsprechenden Informationen für jeden Abonnenten.

```
----------- Copy Below (Ctrl+C) -----------

Hello %SUBSCRIBER NAME%

You have been assigned a Visual Studio subscription. Please visit https://my.visualstudio.com, and log in with your %DIRECTORY ADDRESS% address to activate and access your subscription.

If you’re having trouble, please contact the support team (https://visualstudio.microsoft.com/subscriptions/support/).

At the bottom of the page, select the following:
   - Accounts, Subscriptions, and Billing Support
   - From Issue, choose Subscription sign in support
   - Choose the appropriate Country
   - Select the desired Assisted Support option

----------- End Copy -----------
```

## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Festlegen eines Geschäfts-, Schul- oder Unikontos als persönliches Konto
Nutzen Sie die Anweisungen, die im Abschnitt [Zuweisen von Abonnenten zu einem Verzeichniskonto](#assigning-subscribers-to-a-directory-account) beschrieben sind, um einen neuen Benutzer hinzuzufügen oder die E-Mail-Adresse eines Benutzers im Volume Licensing Service Center (VLSC) zu aktualisieren.  In Fällen, in denen die E-Mail-Adresse nicht vom Verzeichnis erkannt wird, muss der Benutzer schrittweise ein neues Konto erstellen, um die E-Mail-Adresse als persönliches Konto festzulegen.  Für den Übergang hat das Visual Studio-Abonnementteam eine Ausnahme von der unten definierten Identitätsrichtlinie eingerichtet. Wir investieren jedoch in die erforderlichen Ressourcen, um diese Richtlinie künftig zu entfernen.

> [!WARNING]
> Die Kombination von Geschäfts-, Schul- oder Uniidentitäten mit persönlichen Identitäten wird von Microsoft nicht empfohlen.  Der Grund hierfür ist, dass die Organisation nicht mehr Besitzer des Kontos ist und die Kontrolle darüber verliert. Folglich kann der Mitarbeiter – auch nach dem Verlassen des Unternehmens – weiterhin auf bestimmte Produkte oder Dienste zugreifen.  

### <a name="defining-an-email-address-as-a-personal-account"></a>Festlegen einer E-Mail-Adresse als persönliches Konto
Nachdem einem Abonnenten ein Abonnement zugewiesen wurde, wird dieser per E-Mail aufgefordert, die Website [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) zu besuchen, um die Vorteile seines Abonnements zu nutzen.  Beim Anmeldeversuch für das Abonnement wird in Visual Studio jedoch eine Fehlermeldung angezeigt, die darauf hinweist, dass das Konto nicht erkannt wird.  Bitten Sie daher den Abonnenten, folgende Anweisungen auszuführen, bevor er sich bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmeldet.  Verwenden Sie ggf. diese [Vorlage](#notifying-your-subscribers-using-personal-accounts), um den Abonnenten nach dem Zuweisen eines Abonnements darüber zu informieren.

1. Navigieren Sie zu https://my.visualstudio.com, und klicken Sie auf **Neues Microsoft-Konto erstellen**.

2. Füllen Sie die Felder aus:
   - Geben Sie im Feld Someone@example.com die E-Mail-Adresse ein, an die die Begrüßungs-E-Mail gesendet wurde.
   - Erstellen Sie Ihr Kennwort.
   - Wählen Sie Ihre Werbeeinstellungen.
   - Klicken Sie auf **Weiter**.

3. Schließen Sie die Validierungsschritte ab, und klicken Sie auf **Weiter**.

4. Neue Benutzer müssen ggf. das Visual Studio-Profil ausfüllen.

5. Das Abonnement und die Vorteile sollten jetzt angezeigt werden.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Benachrichtigen Ihrer Abonnenten über persönliche Konten
Im oben dargelegten Szenario erhalten Abonnenten zwar eine Begrüßungs-E-Mail, können sich aber aufgrund von Aliasing möglicherweise nicht anmelden.  Sie können den unten stehenden Text verwenden, um Ihre Abonnenten über die oben beschriebenen Schritte zu informieren und, falls erforderlich, Supportoptionen zu empfehlen.  Ersetzen Sie „%WORT%“ durch die entsprechenden Informationen für jeden Abonnenten.

```
----------- Copy Below (Ctrl+C) -----------

Hello %SUBSCRIBER NAME%

You have been assigned a Visual Studio subscription, and may have been directed to log into https://my.visualstudio.com based on your Welcome email.  While this is the correct website for consuming benefits, our organization requires you to take a few extra steps before you can access the site.  Please follow the below instructions to help you create a “Microsoft Account” that is tied to our corporate email address.  Once these steps are completed, you will use your email address to access the Subscription benefits.
1. Visit https://my.visualstudio.com

2. Click Create new Microsoft Account on the right hand side

3. Complete the Form:
   - Use your corporate email address in the someone@example.com box
   - Enter a password
   - Select your promotional preference
   - Click Next

4. Complete the account validation steps

5. If necessary, complete the Visual Studio profile

6. You should now see your benefits

Note:  When visiting https://my.visualstudio.com in the future, you may be prompted to select which account you’d like to use (e.g. “Work or School Account” or “Personal Account”).  After following the steps above, you will need to leverage the “Personal Account” option.

If you’re having trouble, please contact the support team (https://visualstudio.microsoft.com/subscriptions/support/).

At the bottom of the page, select the following:
   - Accounts, Subscriptions, and Billing Support
   - From Issue, choose Subscription sign in support
   - Choose the appropriate Country
   - Select the desired Assisted Support option

----------- End Copy -----------
```
