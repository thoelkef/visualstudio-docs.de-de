---
title: 'Exemplarische Vorgehensweise: Veröffentlichung von Visual Studio-Erweiterung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86ed2455b19a3f7e56c92a37a9402b7d65bf70a3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337925"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Exemplarische Vorgehensweise: Veröffentlichen von Visual Studio-Erweiterung

Diese exemplarische Vorgehensweise veranschaulicht die Visual Studio-Erweiterung in Visual Studio Marketplace zu veröffentlichen. Wenn Sie die Erweiterung zum Marketplace hinzufügen, können Entwickler **Erweiterungen und Updates** nach neuen und aktualisierten Erweiterungen suchen.

## <a name="prerequisites"></a>Vorraussetzungen

 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Erstellen Sie eine Visual Studio-Erweiterung

In diesem Artikel wird eine standardmäßige VSPackage-Erweiterung, aber die Schritte für jede Art von Erweiterung gültig sind.

1. Erstellen Sie ein VSPackage in c# mit dem Namen `TestPublish` , das einen Menübefehl hat. Weitere Informationen finden Sie unter [Erstellen Ihrer erste Erweiterung: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Packen Sie die Erweiterung

1. Aktualisieren Sie die Erweiterung *vsixmanifest* mit den richtigen Informationen zu den Produktnamen, Autor und Version.

   ![Aktualisieren Sie die Erweiterung vsixmanifest](media/update-extension-vsixmanifest.png)

2. Erstellen Sie Ihre Erweiterung **Version** Modus. Jetzt wird die Erweiterung als einer im Ordner \bin\Release des VSIX-Datei verpackt.

3. Sie können die Überprüfung die Installation des VSIX-Datei doppelklicken.

## <a name="test-the-extension"></a>Testen Sie die Erweiterung

 Bevor Sie die Erweiterung verteilen, erstellen Sie und Testen Sie, um sicherzustellen, dass es in der experimentellen Instanz von Visual Studio ordnungsgemäß installiert ist.

1. Starten Sie in Visual Studio debugging, um eine experimentelle Instanz von Visual Studio zu öffnen.

2. Wechseln Sie in der experimentellen Instanz zu den **Tools** Menü **Erweiterungen und Updates**. Die Erweiterung TestPublish sollten im mittleren Bereich angezeigt werden, und aktiviert werden.

3. Auf der **Tools** Menü sicherzustellen, dass den Testbefehl.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Veröffentlichen Sie die Erweiterung in Visual Studio Marketplace

1. Stellen Sie sicher, dass Sie die endgültigen Produktversion von Ihrer Erweiterung erstellt haben und dass sie auf dem neuesten Stand ist.

2. Öffnen Sie in einem Webbrowser die [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Website.

3. Klicken Sie in der oberen rechten Ecke auf **Anmeldung**.

4. Melden Sie sich mit dem Microsoft-Konto an. Wenn Sie nicht über ein Microsoft-Konto verfügen, können Sie eine an diesem Punkt erstellen.

5. Klicken Sie auf **Erweiterungen veröffentlichen**.  Diese Option gelangen Sie zur Seite für alle Ihre Erweiterungen verwalten. Wenn Sie nicht über ein herausgeberkonto verfügen, werden Sie aufgefordert, um eines zu diesem Zeitpunkt zu erstellen.

   ![Hochladen in Marketplace](media/upload-to-marketplace.png)

6. Wählen Sie den Verleger, die, den Sie verwenden, um Ihre Erweiterung hochladen möchten. Herausgeber können Sie durch Klicken auf die Herausgebernamen auf der linken Seite ändern. Klicken Sie auf **neue Erweiterung** , und wählen Sie **Visual Studio**.

7. In **1: Erweiterung hochladen**, können Sie eine VSIX-Datei direkt in Visual Studio Marketplace hochladen oder einfach einen Link zu Ihrer eigenen Website hinzufügen. In diesem Beispiel ist die Erweiterung *TestPublish.vsix* hochgeladen wird. Drag und drop von der Erweiterung aus, oder verwenden Sie die **klicken Sie auf** Link, um die Datei zu suchen. Suchen Sie die Erweiterung im Ordner \bin\Release des Projekts.  Klicken Sie auf **Weiter**.

8. In **2: Angeben der erweiterungsdetails**, einige Felder werden automatisch aus der *"Source.Extension.vsixmanifest"* -Datei aus der Erweiterung. Finden Sie weitere Informationen zu den folgenden:

    * **Interner Name** wird in der URL der Seite mit Details der Erweiterung verwendet. Ein Beispiel, Veröffentlichen einer Extension unter dem Herausgeber "Myname", und geben den internen Namen werden von "my-Erweiterung" führt zu einer URL von "marketplace.visualstudio\.com/items?itemName=myname.myextension" für die Erweiterung der Details Seite ".

    * **Der Anzeigename** Ihrer Erweiterung. Dieser Name wird automatisch aus der *"Source.Extension.vsixmanifest"* Datei.

    * **Version** Anzahl von der Erweiterung, die Sie hochgeladen werden. Diese Version wird automatisch aus der *"Source.Extension.vsixmanifest"* Datei.

    * **VSIX-ID** ist der eindeutige Bezeichner, die Visual Studio für die Erweiterung verwendet. Dieser Bezeichner ist erforderlich, wenn Sie, damit die Erweiterung automatisch aktualisiert möchten. Dieser Bezeichner wird automatisch aus der *"Source.Extension.vsixmanifest"* Datei.

    * **Logo** , die für die Erweiterung verwendet wird. Dieses Logo wird automatisch aus der *"Source.Extension.vsixmanifest"* Datei, sofern bereitgestellt.

    * **Kurze Beschreibung** der Funktionsweise Ihrer Erweiterungs. Diese Beschreibung wird automatisch aus der *"Source.Extension.vsixmanifest"* Datei.

    * **Übersicht über die** ist ein guter Ausgangspunkt, Screenshots und ausführliche Informationen zur Funktionsweise der Erweiterungs.

    * **Unterstützte Versionen von Visual Studio** können Sie wählen, welche Versionen von Visual Studio auf die Erweiterung funktioniert. Die Erweiterung ist nur auf diese Versionen installiert.

    * ** Unterstützt Visual Studio-Edition Ihnen ermöglicht, welche Editionen von Visual Studio auszuwählen, die die Erweiterung funktioniert. Die Erweiterung ist nur für diese Editionen installiert werden.

    * **Typ**. Der am häufigsten verwendete Erweiterungen sind **Tools**.

    * **Kategorien**. Wählen Sie bis zu drei, die optimal für Ihre Erweiterung sind.

    * **Tags** sind Schlüsselwörter, mit denen Benutzer suchen Sie nach Ihrer Erweiterung. Tags können die Suche nach Relevanz Ihrer Erweiterungen in Marketplace zu erhöhen.

    * **Preiskategorie** sind die Kosten für Ihre Erweiterung.

    * **Quellcode-Repository** können Sie einen Link zum Quellcode mit der Community teilen.

    * **F & A für Ihre Erweiterung zulassen** ermöglicht Benutzern, die Fragen auf der Seite für Ihre Erweiterung zu lassen.

9. Klicken Sie auf **speichern und Hochladen**. Diese Option verwendet, die Sie die Sicherung auf des Herausgebers verwalten (Seite). Die Erweiterung wurde noch nicht veröffentlicht. Zum Veröffentlichen Ihrer Extension Maustaste auf Ihre Erweiterung, und wählen **als öffentlich kennzeichnen**. Sehen Sie, wie die Erweiterung auf Marketplace dazu aussehen wird **Erweiterung anzeigen**. Genaue Zahlen zur Übernahme klicken Sie auf **Berichte**. Um die Erweiterung zu ändern, klicken Sie auf **bearbeiten**.

   ![Eintrag-Erweiterungsmenü](media/extension-entry-menu.png)

10. Nach dem Klicken auf **als öffentlich kennzeichnen**, Ihre Erweiterung ist jetzt öffentlich. Suchen Sie den Visual Studio-Marketplace für die Erweiterung.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Fügen Sie zusätzliche Benutzer zum Verwalten Ihres Veröffentlichungskontos hinzu

Marketplace unterstützt die zusätzlichen Benutzerberechtigungen zum Zugreifen auf und verwalten ein veröffentlichungskonto gewähren.

1. Navigieren Sie zu die Kontos für die Veröffentlichung, die, der Sie zusätzliche Benutzer hinzufügen möchten.

2. Wählen Sie **Mitglieder** und klicken Sie auf **hinzufügen**.

   ![Zusätzlichen Benutzer hinzufügen](media/add-users.png)

3. Sie können dann angeben, die e-Mail-Adresse des Benutzers, die Sie verwenden möchten, hinzufügen und gewähren die richtige Zugriffsebene unter **wählen Sie eine Rolle**.  Sie können eine der folgenden Optionen auswählen:

   * **Ersteller**: Der Benutzer kann von anderen Benutzern veröffentlichte Erweiterungen-Erweiterungen veröffentlichen, aber kann nicht anzeigen und verwalten.

   * **Reader**: Der Benutzer kann nicht anzeigen, Extensions aber veröffentlichen oder Verwalten von Erweiterungen.

   * **"Mitwirkender"** : Der Benutzer kann nicht zu veröffentlichen und Verwalten von Erweiterungen, jedoch herausgebereinstellungen bearbeiten oder Verwalten des Zugriffs auf.

   * **Besitzer**: Der Benutzer kann veröffentlichen und Verwalten von Erweiterungen, herausgebereinstellungen bearbeiten und Verwalten des Zugriffs auf.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installieren Sie die Erweiterung von Visual Studio Marketplace

Nun, dass die Erweiterung veröffentlicht wurde, installieren Sie es in Visual Studio, und Testen sie dort.

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.

2. Klicken Sie auf **Online** und suchen Sie nach **TestPublish**.

3. Klicken Sie auf **Download**. Die Erweiterung wird für die Installation geplant.

4. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

Sie können die Erweiterung von Visual Studio Marketplace und auf Ihrem Computer entfernen.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>So entfernen Sie die Erweiterung von Visual Studio Marketplace

1. Öffnen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Website.

2. Klicken Sie in der oberen rechten Ecke auf **veröffentlichen** Erweiterungen. Wählen Sie den Verleger, die Sie zum Veröffentlichen verwendet **TestPublish**. Die Liste für **TestPublish** angezeigt wird.

3. Mit der rechten Maustaste auf den Eintrag für die Erweiterung, und klicken Sie auf **entfernen**. Sie werden aufgefordert, zu überprüfen, ob Sie die Erweiterung entfernen möchten. Klicken Sie auf **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Um die Erweiterung auf Ihrem Computer zu entfernen.

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.

2. Wählen Sie **TestPublish** , und klicken Sie dann auf **Deinstallieren**. Die Erweiterung wird für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Deinstallation abzuschließen.
