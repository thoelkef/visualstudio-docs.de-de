---
title: "Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterungs | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be1402da1677388712472d4309c40ce767358f7b
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2018
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterungs

In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine Visual Studio-Erweiterung zu Visual Studio Marketplace veröffentlicht. Wenn Sie die Erweiterung auf dem Markt hinzufügen, können auf Entwicklerseite **Erweiterungen und Updates** dort nach neuen und aktualisierten Erweiterungen suchen.

## <a name="prerequisites"></a>Erforderliche Komponenten

 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Erstellen einer Visual Studio-Erweiterungs

In diesem Fall verwenden wir eine Standard-VSPackage-Erweiterung, aber die gleichen Schritte gelten für jede Art von Erweiterung.

1. Erstellen Sie ein VSPackage in c# mit dem Namen "TestPublish", die über einen Menübefehl verfügt. Weitere Informationen finden Sie unter [Erstellen Ihrer ersten Erweiterung: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Packen Sie die Erweiterung

1. Aktualisieren der Erweiterung Vsixmanifest mit den richtigen Informationen zu Produktnamen, Author und Version.

  ![Aktualisieren der Erweiterung vsixmanifest](media/update-extension-vsixmanifest.png)

2. Erstellen Sie Ihre Erweiterung **Version** Modus. Die Erweiterung wird jetzt als eine VSIX im Ordner "\bin\Release" verpackt werden.

3. Sie können doppelte VSIX-Pakete zum Überprüfen der Installation klicken.

## <a name="test-the-extension"></a>Testen Sie die Erweiterung

 Bevor Sie die Erweiterung verteilen, erstellen Sie und Testen Sie, um sicherzustellen, dass es richtig in der experimentellen Instanz von Visual Studio installiert ist.

1. Starten Sie das Debuggen in Visual Studio. Um eine experimentelle Instanz von Visual Studio zu öffnen.

2. Wechseln Sie in der experimentellen Instanz zu den **Tools** Menü **Erweiterungen und Updates...** . Die Erweiterung TestPublish sollten im mittleren Bereich angezeigt werden, und aktiviert werden.

3. Auf der **Tools** Menü, stellen Sie sicher, dass Sie den Testbefehl angezeigt.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Die Erweiterung Visual Studio Marketplace veröffentlichen

1. Stellen Sie sicher, dass Sie die endgültigen Produktversion der Erweiterung erstellt haben und es auf dem neuesten Stand ist.

2. Öffnen Sie in einem Webbrowser die [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Website.

3. Klicken Sie in der oberen rechten Ecke auf **anmelden**.

4. Melden Sie sich mit dem Microsoft-Konto an. Wenn Sie nicht über ein Microsoft-Konto verfügen, können Sie zu diesem Zeitpunkt erstellen.

5. Klicken Sie auf **veröffentlichen Erweiterungen**.  Dadurch gelangen Sie auf der Seite "verwalten" für alle Ihre Erweiterungen.  Wenn Sie einen Verleger-Konto besitzen, werden Sie aufgefordert, um eines zu diesem Zeitpunkt zu erstellen.

  ![Hochladen in Marketplace](media/upload-to-marketplace.png)

6. Wählen Sie den Verleger, die, den Sie verwenden, um die Erweiterung hochladen möchten.  Sie können Verleger ändern, indem Sie durch Klicken auf den Herausgebernamen auf der linken Seite aufgeführt.  Klicken Sie auf **neue Erweiterung** , und wählen Sie **Visual Studio**.

7. In **1: Hochladen Erweiterung**, Sie können eine VSIX-Datei direkt in Visual Studio Marketplace hochladen oder einfach einen Link zu Ihrer eigenen Website hinzufügen. In diesem Fall werden wir unsere Erweiterung TestPublish.vsix hochladen.  Ziehen Sie und Ihre Erweiterung löschen, oder verwenden Sie die **klicken Sie auf** Link, um die Datei zu suchen.  Die Erweiterung kann im Ordner "\bin\Release" des Projekts gefunden werden.  Klicken Sie auf **Weiter**.

8. In **2: Geben Sie die Details der**, einige Felder aus der Datei "Source.Extension.vsixmanifest" von der Erweiterung werden automatisch aufgefüllt.  Weitere Informationen zu den einzelnen finden Sie unter:

    * **Interner Name** in der URL der Detailseite für die Erweiterung verwendet werden. Ein Beispiel veröffentlichen eine Erweiterung unter dem Publisher "Myname" und den internen Namen "Myextension" werden angeben führt zu einer URL von "marketplace.visualstudio\.com/items?itemName=myname.myextension" für der Erweiterungs Detailseite.
    
    * **Anzeigename** der Erweiterung.  Dies wird automatisch aufgefüllt, aus der Datei "Source.Extension.vsixmanifest".
   
    * **Version** Anzahl von der Erweiterung, die Sie hochladen.  Dies wird automatisch aufgefüllt, aus der Datei "Source.Extension.vsixmanifest".
    
    * **VSIX-ID** ist der eindeutige Bezeichner, der für die Erweiterung Visual Studio verwendet.  Dies ist erforderlich, wenn Ihre Erweiterung werden automatisch aktualisiert werden sollen.  Dies wird automatisch aufgefüllt, aus der Datei "Source.Extension.vsixmanifest".
    
   * **Logo** , für die Erweiterung verwendet wird.  Dies wird automatisch aus der Datei "Source.Extension.vsixmanifest", falls vorhanden sein.
    
    * **Kurze Beschreibung** der Wirkungsweise der Erweiterungs.  Dies wird automatisch aus der Datei "Source.Extension.vsixmanifest" sein.
    
    * **Übersicht über die** ist ein guter Ausgangspunkt Screenshots und detaillierte Informationen über die Funktionsweise die Erweiterung enthalten.
    
    * **Unterstützte Versionen von Visual Studio** können Sie wählen, welche Versionen von Visual Studio die Erweiterung funktionieren.  Die Erweiterung wird nur auf diese Versionen installiert werden.
    
    * **Unterstützte Editionen von Visual Studio** können Sie wählen, welche Editionen von Visual Studio die Erweiterung arbeiten möchten.  Die Erweiterung wird nur für diese Editionen installiert werden.
    
    * **Typ**.  Die am häufigsten verwendete Typ der Erweiterungen werden **Tools**.
    
    * **Kategorien**.  Wählen Sie bis zu drei, die für die Erweiterung einer am besten geeignet sind.
    
    * **RFID-Transponder** werden Schlüsselwörter, mit denen Benutzer suchen Sie nach der Erweiterung. Tags können die Suche nach Relevanz mit Ihren Erweiterungen auf dem Markt zu erhöhen.
    
    * **Preise Kategorie** sind die Kosten der Erweiterung.
    
    * **Quellcoderepository** ermöglicht es Ihnen, einen Link zum Quellcode mit der Community teilen.
    
    * **Fragen und Antworten für die Erweiterung zulassen** ermöglichen es Benutzern, die Fragen auf Ihre Erweiterung Einstiegsseite lassen.

9. Klicken Sie auf **speichern und Hochladen**. Dadurch gelangen Sie zurück zum Herausgeber Ihres verwalten (Seite).  Die Erweiterung wurde noch nicht veröffentlicht.  Um die Erweiterung zu veröffentlichen, mit der Maustaste, auf die Erweiterung, und wählen **als öffentlich kennzeichnen**.  Sie können anzeigen, wie Ihre Erweiterung in Marketplace dazu aussieht **Erweiterung**.  Klicken Sie bei Erhalt Zahlen auf **Berichte**.  Um die Erweiterung zu ändern, klicken Sie auf **bearbeiten*.

  ![Eintrag-Erweiterungsmenü](media/extension-entry-menu.png)

10. Nach dem Klicken auf **als öffentlich kennzeichnen**, die Erweiterung ist jetzt öffentlich.  Suchen Sie die Visual Studio Marketplace für die Erweiterung ein.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Fügen Sie zusätzliche Benutzer zum Verwalten Ihres Kontos für Verleger hinzu

Marketplace unterstützt das Gewähren von zusätzlichen Benutzerberechtigungen zum Zugriff auf und verwalten Sie ein Konto für Verleger.

1. Navigieren Sie zu der Publisher-Konto, dem Sie zusätzliche Benutzer hinzufügen möchten.

2. Wählen Sie **Elemente** , und klicken Sie auf **hinzufügen**

  ![Fügen Sie zusätzliche Benutzer hinzu](media/add-users.png)

3. Geben Sie Sie dann die e-Mail-Adresse des Benutzers, die Sie verwenden möchten, hinzufügen, und erteilen die richtige Zugriffsebene unter **wählen Sie eine Rolle**.  Sie können folgende Optionen zur Auswahl:

  * **Ersteller**: der Benutzer-Erweiterungen zu veröffentlichen, jedoch nicht anzeigen oder Verwalten von Erweiterungen, die von anderen Benutzern veröffentlicht kann.
  
  * **Reader**: der Benutzer-Erweiterungen anzeigen, jedoch kann nicht veröffentlicht und Verwalten von Erweiterungen kann.
  
  * **Contributor**: der Benutzer kann zu veröffentlichen und Verwalten von Erweiterungen, jedoch kann nicht verlegereinstellungen bearbeiten oder Verwalten des Zugriffs auf.
  
  * **Besitzer**: der Benutzer zu veröffentlichen und Verwalten von Erweiterungen, verlegereinstellungen bearbeiten und Verwalten des Zugriffs auf.
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installieren Sie die Erweiterung von Visual Studio Marketplace

Nun, dass die Erweiterung veröffentlicht wurde, installieren Sie es in Visual Studio, und Testen sie dort.

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates...** .

2. Klicken Sie auf **Online** und suchen Sie nach TestPublish.

3. Klicken Sie auf **Download**. Die Erweiterung wird dann für die Installation geplant werden.

4. Um die Installation abzuschließen, schließen Sie alle Instanzen von Visual Studio.

## <a name="remove-the-extension"></a>Entfernen Sie die Erweiterung

Sie können die Erweiterung von Visual Studio Marketplace und von Ihrem Computer zu entfernen.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>So entfernen Sie die Erweiterung von Visual Studio Marketplace

1. Öffnen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Website.

2. Klicken Sie in der oberen rechten Ecke auf **veröffentlichen** Erweiterungen.  Wählen Sie den Verleger, den Sie zum Veröffentlichen von TestPublish verwendet.  Die Liste für TestPublish wird angezeigt.

3. Mit der rechten Maustaste auf den Eintrag, und klicken Sie auf **entfernen** werden Sie aufgefordert zu überprüfen, ob Sie die Erweiterung entfernen möchten.  Klicken Sie auf **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>So entfernen Sie die Erweiterung von Ihrem computer

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates...** .

2. Wählen Sie TestPublish, und klicken Sie dann auf **Deinstallieren**. Die Erweiterung wird dann für die Deinstallation geplant werden.

3. Schließen Sie alle Instanzen von Visual Studio, zum Abschließen der Deinstallation.
