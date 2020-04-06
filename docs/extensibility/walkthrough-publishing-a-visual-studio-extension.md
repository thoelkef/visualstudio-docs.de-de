---
title: 'Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697143"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie eine Visual Studio-Erweiterung im Visual Studio Marketplace veröffentlichen. Wenn Sie Ihre Erweiterung zum Marketplace hinzufügen, können Entwickler **Erweiterungen und Updates** verwenden, um nach neuen und aktualisierten Erweiterungen zu suchen.

## <a name="prerequisites"></a>Voraussetzungen

 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Erstellen einer Visual Studio-Erweiterung

Dieser Artikel verwendet eine standardmäßige VSPackage-Erweiterung, aber die Schritte sind für jede Art von Erweiterung gültig.

1. Erstellen Sie ein VSPackage `TestPublish` mit dem Namen "C" mit einem Menübefehl. Weitere Informationen finden Sie unter [Erstellen Ihrer ersten Erweiterung: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Packen der Erweiterung

1. Aktualisieren Sie die Erweiterung *.vsixmanifest* mit den richtigen Informationen zu Produktname, Autor und Version.

   ![Update-Erweiterung vsixmanifest](media/update-extension-vsixmanifest.png)

2. Erstellen Sie **Release** Ihre Erweiterung im Release-Modus. Jetzt wird Ihre Erweiterung als VSIX im Ordner .bin-Release verpackt.

3. Sie können auf den VSIX doppelklicken, um die Installation zu überprüfen.

## <a name="test-the-extension"></a>Testen der Erweiterung

 Bevor Sie die Erweiterung verteilen, erstellen und testen Sie sie, um sicherzustellen, dass sie in der experimentellen Instanz von Visual Studio ordnungsgemäß installiert ist.

1. Starten Sie in Visual Studio mit dem Debuggen, um eine experimentelle Instanz von Visual Studio zu öffnen.

2. Wechseln Sie in der experimentellen Instanz zum Menü **Extras,** und klicken Sie auf **Erweiterungen und Updates**. Die TestPublish-Erweiterung sollte im mittleren Bereich angezeigt und aktiviert sein.

3. Stellen Sie im Menü **Extras** sicher, dass der Testbefehl angezeigt wird.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Veröffentlichen der Erweiterung im Visual Studio Marketplace

1. Stellen Sie sicher, dass Sie die Release-Version Ihrer Erweiterung erstellt haben und dass sie auf dem neuesten Stand ist.

2. Öffnen Sie in einem Webbrowser die [Visual Studio Marketplace-Website.](https://marketplace.visualstudio.com/vs)

3. Klicken Sie in der oberen rechten Ecke auf **Anmelden .**

4. Melden Sie sich mit dem Microsoft-Konto an. Wenn Sie kein Microsoft-Konto haben, können Sie an dieser Stelle eines erstellen.

5. Klicken Sie auf **Erweiterungen veröffentlichen**.  Mit dieser Option gelangen Sie zur Seite Verwalten für alle Erweiterungen. Wenn Sie kein Publisher-Konto haben, werden Sie zu diesem Zeitpunkt aufgefordert, eines zu erstellen.

   ![Hochladen in den Marketplace](media/upload-to-marketplace.png)

6. Wählen Sie den Herausgeber aus, den Sie zum Hochladen Ihrer Erweiterung verwenden möchten. Sie können Herausgeber ändern, indem Sie auf die auf der linken Seite aufgeführten Herausgebernamen klicken. Klicken Sie auf **Neue Erweiterung** und wählen Sie **Visual Studio**.

7. In **1: Upload-Erweiterung**können Sie eine VSIX-Datei direkt in Visual Studio Marketplace hochladen oder einfach einen Link zu Ihrer eigenen Website hinzufügen. In diesem Beispiel wird die Erweiterung *TestPublish.vsix* hochgeladen. Ziehen Sie Ihre Erweiterung per Drag & Drop oder verwenden Sie den **Klicklink,** um nach der Datei zu suchen. Suchen Sie Ihre Erweiterung im Ordner "bin-Release" des Projekts.  Klicken Sie auf **Weiter**.

8. In **2: Geben Sie Erweiterungsdetails**an, einige Felder werden automatisch aus der *Datei source.extension.vsixmanifest* aus Ihrer Erweiterung aufgefüllt. Weitere Informationen zu den folgenden Finden Sie unter:

    * **Interner Name** wird in der URL der Detailseite der Erweiterung verwendet. Beispielsweise führt das Veröffentlichen einer Erweiterung unter dem Herausgebernamen "myname" und das Angeben des internen Namens "meine Erweiterung" zu einer URL von "marketplace.visualstudio\.com/items?itemName=myname.myextension" für die Detailseite Ihrer Erweiterung.

    * **Anzeigename** Ihrer Erweiterung. Dieser Name wird automatisch aus der Datei *source.extension.vsixmanifest* aufgefüllt.

    * **Versionsnummer** der Erweiterung, die Sie hochladen. Diese Version wird automatisch aus der Datei *source.extension.vsixmanifest* aufgefüllt.

    * **VSIX-ID** ist der eindeutige Bezeichner, den Visual Studio für Ihre Erweiterung verwendet. Dieser Bezeichner ist erforderlich, wenn Sie Ihre Erweiterung automatisch aktualisieren möchten. Dieser Bezeichner wird automatisch aus der Datei *source.extension.vsixmanifest* aufgefüllt.

    * **Logo,** das für Ihre Erweiterung verwendet wird. Dieses Logo wird automatisch aus der Datei *source.extension.vsixmanifest* aufgefüllt, sofern angegeben.

    * **Kurze Beschreibung,** was Ihre Erweiterung tut. Diese Beschreibung wird automatisch aus der Datei *source.extension.vsixmanifest* aufgefüllt.

    * **Übersicht** ist ein guter Ort, um Screenshots und detaillierte Informationen darüber, was Ihre Erweiterung tut.

    * **Mit unterstützten Visual Studio-Versionen** können Sie auswählen, an welchen Versionen von Visual Studio Ihre Erweiterung arbeiten soll. Ihre Erweiterung wird nur in diesen Versionen installiert.

    * **Unterstützte Visual Studio-Edition enkt mit der Auswahl der Editionen von Visual Studio, an denen Ihre Erweiterung funktioniert. Ihre Erweiterung wird nur für diese Editionen installiert.

    * **Typ**. Die häufigste Art von Erweiterungen sind **Tools**.

    * **Kategorien**. Holen Sie sich bis zu drei, die am besten für Ihre Erweiterung passen.

    * **Tags** sind Schlüsselwörter, die Benutzern helfen, Ihre Erweiterung zu finden. Tags können dazu beitragen, die Suchrelevanz Ihrer Erweiterungen im Marketplace zu erhöhen.

    * **Die Preiskategorie** ist der Preis für Ihre Erweiterung.

    * Mit dem **Quellcode-Repository** können Sie einen Link zu Ihrem Quellcode für die Community freigeben.

    * **Lassen Sie Q&A für Ihre Erweiterung** zulassen, können Benutzer Fragen auf Ihrer Erweiterungseingabeseite hinterlassen.

9. Klicken Sie auf **Speichern & Hochladen**. Mit dieser Option gelangen Sie zurück zu Ihrer Publisher-Verwaltungsseite. Ihre Erweiterung wurde noch nicht veröffentlicht. Um Ihre Erweiterung zu veröffentlichen, klicken Sie mit der rechten Maustaste auf Ihre Erweiterung und wählen **Sie Öffentlich machen**. Sie können anzeigen, wie Ihre Erweiterung auf Marketplace aussehen wird, indem Sie **Erweiterung anzeigen**auswählen. Für Akquisitionsnummern klicken Sie auf **Berichte**. Um Änderungen an Ihrer Erweiterung vorzunehmen, klicken Sie auf **Bearbeiten**.

   ![Erweiterungseintragsmenü](media/extension-entry-menu.png)

10. Nachdem Sie auf **"Öffentlich erstellen"** geklickt haben, ist Ihre Erweiterung nun öffentlich. Durchsuchen Sie den Visual Studio Marketplace nach Ihrer Erweiterung.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Hinzufügen zusätzlicher Benutzer zum Verwalten Ihres Publisher-Kontos

Marketplace unterstützt das Gewähren zusätzlicher Benutzerberechtigungen für den Zugriff auf und die Verwaltung eines Publisher-Kontos.

1. Navigieren Sie zu dem Publisher-Konto, dem Sie weitere Benutzer hinzufügen möchten.

2. Wählen Sie **Mitglieder** aus und klicken Sie auf **Hinzufügen**.

   ![Hinzufügen von zusätzlichen Benutzern](media/add-users.png)

3. Sie können dann die E-Mail-Adresse des Benutzers angeben, den Sie hinzufügen möchten, und die richtige Zugriffsebene unter **Rolle auswählen**angeben.  Sie können zwischen folgenden Optionen wählen:

   * **Ersteller**: Der Benutzer kann Erweiterungen veröffentlichen, aber keine von anderen Benutzern veröffentlichten Erweiterungen anzeigen oder verwalten.

   * **Reader**: Der Benutzer kann Erweiterungen anzeigen, aber keine Erweiterungen veröffentlichen oder verwalten.

   * **Mitwirkender**: Der Benutzer kann Erweiterungen veröffentlichen und verwalten, aber keine Herausgebereinstellungen bearbeiten oder den Zugriff verwalten.

   * **Besitzer**: Der Benutzer kann Erweiterungen veröffentlichen und verwalten, Herausgebereinstellungen bearbeiten und den Zugriff verwalten.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installieren der Erweiterung aus dem Visual Studio Marketplace

Nachdem die Erweiterung veröffentlicht wurde, installieren Sie sie in Visual Studio und testen Sie sie dort.

1. Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungen und Updates**.

2. Klicken Sie auf **Online,** und suchen Sie dann nach **TestPublish**.

3. Klicken Sie auf **Download**. Die Erweiterung wird dann für die Installation geplant.

4. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

Sie können die Erweiterung aus dem Visual Studio Marketplace und von Ihrem Computer entfernen.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>So entfernen Sie die Erweiterung aus dem Visual Studio Marketplace

1. Öffnen Sie die [Visual Studio Marketplace-Website.](https://marketplace.visualstudio.com/vs)

2. Klicken Sie in der oberen rechten Ecke auf Erweiterungen **veröffentlichen.** Wählen Sie den Herausgeber aus, den Sie zum Veröffentlichen von **TestPublish**verwendet haben. Die Auflistung für **TestPublish** wird angezeigt.

3. Klicken Sie mit der rechten Maustaste auf den Erweiterungseintrag und klicken Sie auf **Entfernen**. Sie werden aufgefordert zu bestätigen, ob Sie die Erweiterung entfernen möchten. Klicken Sie auf **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>So entfernen Sie die Erweiterung von Ihrem Computer

1. Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungen und Updates**.

2. Wählen Sie **TestPublish** aus, und klicken Sie dann auf **Deinstallieren**. Die Erweiterung wird dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Deinstallation abzuschließen.
