---
title: Mögliche Fehler beim Anmelden bei Visual Studio-Abonnements bei Verwendung von Aliasen | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/02/2018
ms.topic: conceptual
description: Mögliche Fehler beim Anmelden, wenn Aliase oder Anzeigenamen verwendet werden.
searchscope: VS Subscription
ms.openlocfilehash: f0b18aca4c6188c23998c8a87f86359895198b95
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58195150"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Mögliche Fehler beim Anmelden bei Visual Studio-Abonnements bei Verwendung von Aliasen

Abhängig vom für die Anmeldung verwendeten Kontotyp werden verfügbare Abonnements möglicherweise nicht ordnungsgemäß angezeigt, wenn Benutzer sich bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmelden. Eine mögliche Ursache ist die Verwendung von „Aliasen“ oder „Anzeigenamen“ anstelle der Anmeldeidentität, der das Abonnement zugewiesen ist. Dieser Vorgang wird als „Aliasing“ bezeichnet.

## <a name="what-is-aliasing"></a>Was ist Aliasing?

Der Begriff „Aliasing“ bezieht sich auf Benutzer, die über verschiedene Identitäten für die Anmeldung bei Windows (oder Ihrem Active Directory) und den Zugriff auf E-Mails verfügen.

Aliasing kann auftreten, wenn ein Unternehmen über einen Microsoft Online Service für die Verzeichnisanmeldung verfügt, wie z.B. JohnD@contoso.com, aber Benutzer auf ihre E-Mail-Konten über Aliase oder Anzeigenamen, z.B. John.Doe@contoso.com, zugreifen. Für viele Kunden, die ihre Abonnements über das Volume Licensing Service Center (VLSC) verwalten, kann dies zu einer erfolglosen Anmeldung führen. Dies liegt daran, dass die angegebene E-Mail-Adresse (John.Doe@contoso.com) nicht mit der Verzeichnisadresse (JohnD@contoso.com) übereinstimmt, die für eine erfolgreiche Authentifizierung über die Option „Geschäfts-, Schul- oder Unikonto“ erforderlich ist.

## <a name="as-an-administrator-what-options-do-i-have"></a>Welche Möglichkeiten habe ich als Administrator?

Als Administrator haben Sie zwei Möglichkeiten, um sicherzustellen, dass die Anmeldung Ihrer Abonnenten bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) erfolgreich ist.
- Die erste (empfohlene) Option ist die Nutzung des Verzeichniskontos als zugewiesene Adresse im Volume Licensing Service Center (VLSC). Weitere Informationen hierzu finden Sie in diesem Artikel im Abschnitt [Zuweisen von Abonnenten zu einem Verzeichniskonto](#assigning-subscribers-to-a-directory-account).
- Die zweite (weniger sichere) Option erlaubt es Ihren Abonnenten, ihre Geschäfts-, Schul- oder Uni-E-Mail-Adresse mit einem „persönlichen“ Konto zu verknüpfen (auch Microsoft-Konto oder Microsoft Account (MSA) genannt). Weitere Informationen hierzu finden Sie in diesem Artikel im Abschnitt [Festlegen eines Geschäfts-, Schul- oder Unikontos als persönliches Konto](#defining-a-work-or-school-account-as-a-personal-account).

> [!NOTE]
> Sobald Ihr Unternehmen zum neuen [Verwaltungsportal](https://manage.visualstudio.com) für Visual Studio-Abonnements migriert ist, können Sie die Vorteile der neuen Administrationsfunktionen nutzen. Diese ermöglichen es Ihnen, sowohl Verzeichnis- als auch E-Mail-Adressen als Teil des Abonnentenprofils anzugeben. Weitere Informationen zur [Migration](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>Welche Möglichkeiten habe ich als Abonnent?

Als Abonnent sollten Sie sich zunächst unbedingt an Ihren Administrator wenden, um sich mit dem Identitätskonfiguration für Ihr Unternehmen vertraut zu machen. Gegebenenfalls muss der Administrator Ihre Kontoeinstellungen von seinem Verwaltungsportal aus aktualisieren, oder Sie müssen ein Microsoft-Konto (MSA) mit Ihrer Firmen-E-Mail-Adresse erstellen. Bevor Sie die Schritte zur Erstellung eines MSA ausführen, sprechen Sie mit Ihrem Administrator über Richtlinien oder Probleme bei der Durchführung dieser Aktion. Weitere Informationen hierzu finden Sie in diesem Artikel im Abschnitt [Festlegen eines Geschäfts-, Schul- oder Unikontos als persönliches Konto](#defining-a-work-or-school-account-as-a-personal-account).

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

----------- Kopieren Sie Folgendes (Strg+C) -----------

Hallo %ABONNENTENNAME%,

Ihnen wurde ein Visual Studio-Abonnement zugewiesen. Besuchen Sie https://my.visualstudio.com, und melden Sie sich mit Ihrer Adresse „%VERZEICHNISADRESSE%“ an, um Ihr Abonnement zu aktivieren und darauf zuzugreifen.

Wenn Sie Probleme haben, wenden Sie sich an das Supportteam (https://visualstudio.microsoft.com/subscriptions/support/).

Wählen Sie unten auf der Seite Folgendes aus:
   - Konten, Abonnements und Abrechnungssupport
   - Geben Sie als Problem an, dass Sie Support bei der Anmeldung für ein Abonnement benötigen.
   - Wählen Sie das entsprechende Land.
   - Wählen Sie die gewünschte Option für persönlichen Support.

----------- Textende -----------

## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Festlegen eines Geschäfts-, Schul- oder Unikontos als persönliches Konto

Nutzen Sie die Anweisungen, die im Abschnitt [Zuweisen von Abonnenten zu einem Verzeichniskonto](#assigning-subscribers-to-a-directory-account) beschrieben sind, um einen neuen Benutzer hinzuzufügen oder die E-Mail-Adresse eines Benutzers im Volume Licensing Service Center (VLSC) zu aktualisieren.  In Fällen, in denen die E-Mail-Adresse nicht vom Verzeichnis erkannt wird, muss der Benutzer schrittweise ein neues Konto erstellen, um die E-Mail-Adresse als persönliches Konto festzulegen.  Für den Übergang hat das Visual Studio-Abonnementteam eine Ausnahme von der unten definierten Identitätsrichtlinie eingerichtet. Wir investieren jedoch in die erforderlichen Ressourcen, um diese Richtlinie künftig zu entfernen.

> [!WARNING]
> Die Kombination von Geschäfts-, Schul- oder Uniidentitäten mit persönlichen Identitäten wird von Microsoft nicht empfohlen.  Der Grund hierfür ist, dass die Organisation nicht mehr Besitzer des Kontos ist und die Kontrolle darüber verliert. Folglich kann der Mitarbeiter – auch nach dem Verlassen des Unternehmens – weiterhin auf bestimmte Produkte oder Dienste zugreifen.  Weitere Informationen zu dem Thema finden Sie in diesem [Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/) vom Microsoft-Identitätsteam.

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

----------- Kopieren Sie Folgendes (Strg+C) -----------

Hallo %ABONNENTENNAME%,

Ihnen wurde ein Visual Studio-Abonnement zugewiesen, und Sie wurden möglicherweise in Ihrer Begrüßungs-E-Mail aufgefordert, sich bei https://my.visualstudio.com anzumelden.  Damit Sie alle Vorteile Ihres Abonnements über diese Website nutzen können, benötigen wir jedoch Ihre Mithilfe. Führen Sie bitte zunächst einige zusätzliche Schritte aus, um auf die Website zugreifen zu können.  Folgen Sie den unten stehenden Anweisungen, um ein „Microsoft-Konto“ zu erstellen, das mit unserer Firmen-E-Mail-Adresse verknüpft ist.  Anschließend können Sie Ihre E-Mail-Adresse verwenden, um auf die Abonnementvorteile zuzugreifen.
1. Besuchen Sie https://my.visualstudio.com.

2. Klicken Sie rechts auf „Neues Microsoft-Konto erstellen“.

3. Füllen Sie das Formular aus:
   - Geben Sie im Feld someone@example.com Ihre Firmen-E-Mail-Adresse ein.
   - Geben Sie ein Kennwort ein.
   - Wählen Sie Ihre Werbevoreinstellungen aus.
   - Klicken Sie auf Weiter.

4. Schließen Sie die Schritte zur Kontovalidierung ab.

5. Füllen Sie ggf. das Visual Studio-Profil aus.

6. Ihre Vorteile sollten jetzt angezeigt werden.

Hinweis:  Wenn Sie künftig die Website https://my.visualstudio.com besuchen, werden Sie möglicherweise aufgefordert, das Konto auszuwählen, das Sie verwenden möchten (z.B. „Geschäfts-, Schul- oder Unikonto“ oder „Persönliches Konto“).  Nachdem Sie die obigen Schritte ausgeführt haben, müssen Sie die Option „Persönliches Konto“ nutzen.

Wenn Sie Probleme haben, wenden Sie sich an das Supportteam (https://visualstudio.microsoft.com/subscriptions/support/).

Wählen Sie unten auf der Seite Folgendes aus:
   - Konten, Abonnements und Abrechnungssupport
   - Geben Sie als Problem an, dass Sie Support bei der Anmeldung für ein Abonnement benötigen.
   - Wählen Sie das entsprechende Land.
   - Wählen Sie die gewünschte Option für persönlichen Support.

----------- Textende -----------
