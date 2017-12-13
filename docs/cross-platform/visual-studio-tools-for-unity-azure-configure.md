---
title: "Visual Studio-Tools für Unity: Konfigurieren – Exemplarische Vorgehensweise (Azure) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: BAE62C27-CA7A-4466-8738-3DB880221CE1
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 4e1cf47420cafda2552cdbb625d6d41626c32971
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="configure-easy-tables-in-azure"></a>Konfigurieren einfacher Tabellen in Azure

„Einfache Tabellen“ sind ein Feature von [Azure Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/), welches das Einrichten und Verwalten von SQL-Tabellen direkt in der grafischen Benutzeroberfläche des Azure-Portals ermöglicht. Azure Mobile Apps unterstützt viele Features, jedoch wird in diesem Beispiel nur das Lesen und Schreiben von Daten eines Unity-Projekts behandelt, die im Back-End einer Azure Mobile App gespeichert sind.

## <a name="create-a-new-azure-mobile-app"></a>Eine neue Azure Mobile App erstellen

Melden Sie sich beim [Azure-Portal](https://ms.portal.azure.com) an. Wenn Sie über kein Azure-Abonnement verfügen, sind die [kostenlose Testversion](https://azure.microsoft.com/en-us/free/) oder mitgelieferte Gutschriften von [Visual Studio Dev Essentials](https://www.visualstudio.com/dev-essentials/) für diese exemplarische Vorgehensweise mehr als ausreichend.

**Sobald Sie im Portal sind, tun Sie Folgendes:**

1. Wählen Sie **Neu > Web + Mobil > Mobile App > Erstellen** aus.

  ![Neue mobile App erstellen](media/vstu_azure-configure-easy-tables-image1.png)

2. Konfigurieren der neuen mobilen App:

  * **App-Name**. Dadurch wird die URL erstellt, die zum Herstellen einer Verbindung mit dem Azure Mobile App-Back-End verwendet wird. Sie müssen einen eindeutigen Namen wählen. Wenn der Name eindeutig ist, wird ein grünes Häkchen angezeigt.

  * **Abonnement**. Wählen Sie das Abonnement aus, das die neue mobile App zur Abrechnung verwendet.

  * **Ressourcengruppe**. Ressourcengruppen ermöglichen die einfachere Verwaltung der zugehörigen Ressourcen. In Azure wird standardmäßig eine neue Ressourcengruppe mit dem gleichen Namen wie die neue App erstellt. Die Standardeinstellung eignet sich für die exemplarische Vorgehensweise gut.

  *  **App Service-Plan/Speicherort**. Durch den Diensttarif werden die Rechenleistung, der Speicherort und die Kosten für die Ressourcen bestimmt, die Azure zum Hosten der neuen Mobile App verwendet. In Azure wird standardmäßig ein neuer Diensttarif mit einigen Standardeinstellungen erstellt. Das ist für diese exemplarische Vorgehensweise die einfachste Option. Sie können aber auch mithilfe dieses Menüs den Tarif oder den geographischen Ort eines neuen Diensttarifs anpassen. Des Weiteren können die Einstellungen eines Diensttarifs nach dessen Bereitstellung geändert werden.

  ![Neue mobile App erstellen](media/vstu_azure-configure-easy-tables-image2.png)

3. Klicken Sie auf **Erstellen**, und warten Sie kurz, bis Azure die neue Ressource bereitgestellt hat. Wenn die Bereitstellung abgeschlossen ist, wird im Azure-Portal eine Benachrichtigung angezeigt.

## <a name="add-a-new-data-connection"></a>Neue Datenverbindung hinzufügen

4. Klicken Sie nach Abschluss der Bereitstellung auf die Schaltfläche **All resources** (Alle Ressourcen), und wählen Sie anschließend die neu erstellte mobile App.

  ![Die neue mobile App auswählen](media/vstu_azure-configure-easy-tables-image3.png)

5. Scrollen Sie im neu geöffneten Blatt im Menü auf der linken Seite nach unten, und klicken Sie auf die Schaltfläche **Einfache Tabellen**, die sich unter der Überschrift **MOBIL** befindet.

  ![Auswählen von „Einfachen Tabellen“](media/vstu_azure-configure-easy-tables-image4.png)

6. Klicken Sie auf den blauen Hinweis **Need to configure Easy Tables/Easy APIs** (Einfache Tabellen/Einfache APIs müssen konfiguriert werden), der am oberen Rand des Blatts „Easy Tables“ angezeigt wird.

  ![Klicken Sie auf den Hinweis, der Sie zum Konfigurieren einfacher Tabellen auffordert.](media/vstu_azure-configure-easy-tables-image5.png)

7. Klicken Sie auf den Hinweis mit folgendem Text: **You need a database to use Easy Tables.  Click here to create one** (Sie benötigen eine Datenbank, um „Einfache Tabellen“ zu verwenden. Klicken Sie hier, um eine zu erstellen.).

  ![Klicken Sie auf den Hinweis, der Sie zum Erstellen einer Datenbank auffordert.](media/vstu_azure-configure-easy-tables-image6.png)

8. Klicken Sie auf dem Blatt „Datenverbindungen“ auf die Schaltfläche **Hinzufügen**.

  ![Klicken Sie auf die Schaltfläche „Hinzufügen“.](media/vstu_azure-configure-easy-tables-image7.png)

9. Wählen Sie auf dem Blatt „Add a data connection“ (Eine Datenverbindung hinzufügen) **SQL-Datenbank** aus.

  ![Wählen Sie „SQL-Datenbank“ aus.](media/vstu_azure-configure-easy-tables-image8.png)

10. Jetzt wird ein Blatt zum Konfigurieren einer neuen SQL-Datenbank und eines neuen SQL-Servers geöffnet.

  * **Name**. Geben Sie einen Namen für die Datenbank ein.

  * **Zielserver**. Klicken Sie zum Öffnen des Blatts „Neuer Server“ auf **Zielserver**.

      * **Servername**. Geben Sie einen Namen für den Server ein.

      * **Server admin login and Password** (Anmelde-ID und Kennwort für den Server-Administrator). Erstellen Sie einen Benutzernamen und ein Kennwort für den Server-Administrator.

      * **Speicherort**. Wählen Sie einen nahe gelegenen Speicherort für den Server aus.

      * Stellen Sie sicher, dass das Kontrollkästchen **Allow azure services to access server** (Serverzugriff für Azure Services erlauben) aktiviert ist.

      * Klicken Sie zum Abschließen der Serverkonfiguration auf **Auswählen**.

    * **Tarif**. Behalten Sie die Standardeinstellung für die exemplarische Vorgehensweise bei. Diese kann später geändert werden.

    * **Sortierung**. Behalten Sie die Standardeinstellung bei.

    * Klicken Sie zum Abschließen der Datenbankkonfiguration auf **Auswählen**.

    ![SQL-Server und -Datenbank konfigurieren](media/vstu_azure-configure-easy-tables-image9.png)

11. Auf dem Blatt „Datenverbindung hinzufügen“ klicken Sie auf **Verbindungszeichenfolge**. Wenn das Blatt „Verbindungszeichenfolge“ angezeigt wird, übernehmen Sie die Standardeinstellungen, und klicken Sie auf **OK**.

  ![Klicken auf „Verbindungszeichenfolge“.](media/vstu_azure-configure-easy-tables-image9.1.png)

12. Auf dem Blatt „Datenverbindung hinzufügen“ sollte der Text „MS_TableConnectionString“ nicht mehr kursiv geschrieben sein. Klicken Sie auf **OK**, und warten Sie kurz, bis Azure die neue Datenverbindung erstellt hat. Wenn der Vorgang abgeschlossen ist, werden Sie benachrichtigt.

  ![Klicken Sie auf „OK“.](media/vstu_azure-configure-easy-tables-image9.2.png)

## <a name="complete-the-easy-table-initialization"></a>Das Initialisieren einfacher Tabellen abschließen

13. Sobald die neue Datenverbindung erfolgreich erstellt wurde, klicken Sie auf die Schaltfläche **All resources** (Alle Ressourcen), und navigieren Sie wieder zurück zur Mobile App. Es ist wichtig, diesen Schritt abzuschließen, damit der Hinweis bezüglich der Konfiguration einfacher Tabellen aktualisiert wird.

14. Scrollen Sie nach unten, wählen Sie **Einfache Tabellen** aus, und klicken Sie anschließend erneut auf den blauen Hinweis **Need to configure Easy Tables/Easy APIs** (Einfache Tabellen/Einfache APIs müssen konfiguriert werden).

  ![Klicken auf den Hinweis „Einfache Tabellen“.](media/vstu_azure-configure-easy-tables-image5.png)

15. Dieses Mal sollte auf dem jetzt angezeigten Blatt unter der Überschrift **1** Folgendes stehen: „Sie verfügen bereits über eine Datenverbindung.“ Aktivieren Sie unter der Überschrift **2** das Kontrollkästchen, neben dem Folgendes steht: **I acknowledge that this will overwrite site contents** (Mir ist bewusst, dass hierdurch Websiteinhalte überschrieben werden). Klicken Sie nun auf **Initialize App** (App initialisieren), und warten Sie einige Minuten, bis Azure den Initialisierungsvorgang abgeschlossen hat. Wenn der Vorgang abgeschlossen ist, werden Sie erneut benachrichtigt.

  ![Klicken Sie auf „Initialize App“ (App initialisieren).](media/vstu_azure-configure-easy-tables-image10.png)

## <a name="next-step"></a>Nächster Schritt

* [Erstellen einfacher Tabellen](visual-studio-tools-for-unity-azure-setup.md)
