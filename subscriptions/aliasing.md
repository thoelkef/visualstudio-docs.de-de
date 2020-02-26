---
title: Mögliche Fehler beim Anmelden bei Visual Studio-Abonnements bei Verwendung von Aliasen | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: Mögliche Fehler beim Anmelden, wenn Aliase oder Anzeigenamen verwendet werden.
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276624"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Mögliche Fehler beim Anmelden bei Visual Studio-Abonnements bei Verwendung von Aliasen
Abhängig vom für die Anmeldung verwendeten Kontotyp werden verfügbare Abonnements möglicherweise nicht ordnungsgemäß angezeigt, wenn Benutzer sich bei [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmelden. Eine mögliche Ursache ist die Verwendung von „Aliasen“ oder „Anzeigenamen“ anstelle der Anmeldeidentität, der das Abonnement zugewiesen ist. Dieser Vorgang wird als „Aliasing“ bezeichnet.

## <a name="what-is-aliasing"></a>Was ist Aliasing?
Der Begriff „Aliasing“ bezieht sich auf Benutzer, die über verschiedene Identitäten für die Anmeldung bei Windows (oder Ihrem Active Directory) und den Zugriff auf E-Mails verfügen.

Aliasing kann auftreten, wenn ein Unternehmen über einen Microsoft Online-Dienst für die Verzeichnisanmeldung verfügt (z. B. olivia@contoso.com), aber Benutzer auf ihre E-Mail-Konten über Aliase oder Anzeigenamen (z. B. OliviaG@contoso.com) zugreifen. Sorgen Sie dafür, dass sich Ihre Benutzer mithilfe der Anmelde-E-Mail-Adresse anmelden, um auf ihre Abonnements zuzugreifen. Die Adressen sind im Verwaltungsportal für Visual Studio-Abonnements unter https://manage.visualstudio.com aufgeführt.

## <a name="as-an-administrator-what-options-do-i-have"></a>Welche Möglichkeiten habe ich als Administrator?

Je nach Kontotyp des Abonnenten finden Sie unten die entsprechende Lösung:

### <a name="work-or-school-account-upn-mismatch-issue"></a>Fehler bei fehlender Übereinstimmung des UPN von Geschäfts-, Schul- oder Unikonto

Eine fehlende Übereinstimmung des Benutzerprinzipalnamens (UPN) kann auftreten, wenn in einem Unternehmen Active Directory eingerichtet ist und der UPN nicht identisch mit der primären SMTP-Adresse ist. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>Erkennen, ob es für die Anmeldeadresse eines Benutzers keine UPN-Übereinstimmung gibt

Sorgen Sie dafür, dass der Benutzer die folgenden Schritte ausführt:

1. Der Benutzer muss sich mithilfe der Anmeldeadresse bei https://my.visualstudio.com anmelden, die er in der Abonnementzuweisungs-E-Mail findet.  

    > [!NOTE]
    > Wenn er seine Abonnementzuweisungs-E-Mail nicht zur Hand hat, können Sie ihm diese E-Mail über das Verwaltungsportal erneut senden.  

2. Klicken Sie auf die Registerkarte **Abonnements**.
3. Der Benutzer muss überprüfen, ob die E-Mail-Adresse, die oben rechts unter „Sie sind angemeldet als…“ angezeigt wird, identisch mit der Anmelde-E-Mail-Adresse ist, die er in der Abonnementzuweisungs-E-Mail findet.  Ist dies nicht der Fall, können Benutzer nicht auf ihre Abonnementsvorteile zugreifen. 

   > [!div class="mx-imgBorder"]
   > ![Abonnementsseite](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>Korrigieren der fehlenden Übereinstimmung des UPN

1. Greifen Sie auf das Verwaltungsportal für Visual Studio unter https://manage.visualstudio.com zu. 

2. Suchen Sie nach dem Benutzer, bei dem das Problem der fehlenden UPN-Übereinstimmung aufgetreten ist.  Das [Filterfeature](search-license.md) erleichtert Ihnen den Prozess, wenn es sehr viele Abonnements gibt. 

3. Ändern Sie die Anmelde-E-Mail-Adresse in den UPN des Benutzers.

4. Speichern der Änderungen 

5. Bitten Sie den Benutzer, sich im Abonnentenportal abzumelden, und sich mit dem UPN erneut anzumelden.   

### <a name="personal-account-aliasing-issue"></a>Aliasingprobleme bei persönlichen Konten

Aliasingprobleme können auch persönliche Konten betreffen. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>Erkennen, ob bei einem persönlichen Konto ein Aliasingproblem auftritt

1. Melden Sie sich unter https://my.visualstudio.com an.

2. Klicken Sie auf die Registerkarte **Abonnements**, und überprüfen Sie die Adresse, mit der Sie angemeldet sind. 

3. Wenn die E-Mail-Adresse, mit der Sie angemeldet sind, nicht identisch mit der E-Mail-Adresse ist, mit der auf die Website zugegriffen wurde, kommt es zu einem Konflikt zwischen Ihrem Konto und dem Alias. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>Beheben eines Aliasingproblems bei einem persönlichen Konto

Die Plattform mit Visual Studio-Abonnements priorisiert den primären Alias so, dass Abonnementdetails angezeigt werden.  Wenn Sie das Problem beheben möchten, müssen Sie einen anderen E-Mail-Alias zum primären Alias machen, um sich anzumelden. 

1. Navigieren Sie zu [Anmeldung bei Microsoft verwalten](https://go.microsoft.com/fwlink/p/?linkid=842796).
2. Melden Sie sich in Ihrem Microsoft-Konto an, wenn Sie dazu aufgefordert werden. 
3. Klicken Sie unter Kontoaliase neben der E-Mail-Adresse, die für die Zuweisung des Abonnements verwendet wurde, auf die Option **Als primär festlegen**. 
4. Klicken Sie unter Kontoaliase neben der E-Mail-Adresse, die für die Zuweisung des Abonnements verwendet wurde, auf die Option „Als primär festlegen“. 
5. Melden Sie sich vom Visual Studio-Portal für Abonnenten ab (https://my.visualstudio.com). 
6. Greifen Sie mit dem neuen primären Alias erneut auf das Portal zu. 

### <a name="ensure-a-successful-experience-for-your-users"></a>Garantieren einer problemlosen Anmeldung für Ihre Benutzer

Als Administrator haben Sie zwei Möglichkeiten, um sicherzustellen, dass die Anmeldung Ihrer Abonnenten bei https://my.visualstudio.com problemlos möglich ist. 

- Die erste Option (empfohlen) ist die Verwendung des Verzeichniskontos als Adresse für die Anmeldung bei https://manage.visualstudio.com.
- Die zweite Option ist weniger sicher, und besteht darin, Abonnenten die Möglichkeit zu geben, sich mit einer anderen E-Mail-Adresse als ihrer Verzeichnis-E-Mailadresse anzumelden.

Beide Option werden im Administratorportal konfiguriert, indem die folgenden Schritte ausgeführt werden:

1. Melden Sie sich bei https://manage.visualstudio.com an. 

2. Wenn Sie Änderungen für einen einzelnen Benutzer vornehmen möchten, wählen Sie diesen Benutzer in der Tabelle aus, und klicken Sie für das Bearbeiten mit der rechten Maustaste auf ihn. Dadurch wird ein Panel geöffnet, in dem Sie die E-Mail-Adresse für die Anmeldung ändern können.  

3. Nehmen Sie im Feld für die E-Mail-Adresse für die Anmeldung die erforderlichen Änderungen vor. 

4. Klicken Sie auf „Speichern“, und die Änderungen werden umgesetzt.  
Wenn Sie Änderungen an mehreren Benutzern gleichzeitig vornehmen möchten, können Sie das Feature für die Massenbearbeitung verwenden. Lesen Sie den Abschnitt **Bearbeiten mehrerer Abonnenten mithilfe der Massenbearbeitung** im Artikel „Bearbeiten von Visual Studio-Abonnementzuweisungen“ ([Edit subscriptions]](edit-license.md)), um weitere Informationen zu diesem Prozess zu erhalten.  

## <a name="next-steps"></a>Nächste Schritte
In diesen Artikeln erhalten Sie weitere Informationen zum Verwalten von Visual Studio-Abonnements.
- [Zuweisen von Lizenzen im Verwaltungsportal für Visual Studio-Abonnements](assign-license.md)
- [Zuweisen von Abonnements zu mehreren Benutzern](assign-license-bulk.md)
- [Bearbeiten von Abonnements](edit-license.md)
- [Löschen von Abonnements](delete-license.md)
- [Verwenden des Features „Maximum Usage“ (Maximale Auslastung) zur Übersicht der Anzahl zugewiesener Abonnements](maximum-usage.md)

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)
