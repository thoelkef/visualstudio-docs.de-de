---
title: Veröffentlichen einer Erweiterung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201971"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Hinweis**: die Visual Studio Gallery wird durch das Visual Studio Marketplace ersetzt. Weitere Informationen finden Sie in der neuesten Version dieses Themas.

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine Visual Studio-Erweiterung in der Visual Studio Gallery veröffentlichen. Wenn Sie Ihre Erweiterung dem Katalog hinzufügen, können Entwickler **Erweiterungen und Updates** verwenden, um dort nach neuen und aktualisierten Erweiterungen zu suchen.

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Erstellen einer Visual Studio-Erweiterung
 In diesem Fall wird eine standardmäßige VSPackage-Erweiterung verwendet, aber die gleichen Schritte sind für jede Art von Erweiterung gültig.

1. Erstellen Sie ein VSPackage in c# mit `TestPublishing` dem Namen, das über einen Menübefehl verfügt. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Testen der Erweiterung
 Bevor Sie die Erweiterung verteilen, erstellen und testen Sie Sie, um sicherzustellen, dass Sie ordnungsgemäß in der experimentellen Instanz von Visual Studio installiert ist.

1. Starten Sie in Visual Studio das Debuggen. , um eine experimentelle Instanz von Visual Studio zu öffnen.

2. Wechseln Sie **in der experimentellen Instanz zum Menü Extras** , und klicken Sie auf Erweiterungs- **Manager**. Die Erweiterung "testpublishing" sollte im mittleren Bereich angezeigt und aktiviert werden.

3. Vergewissern Sie sich, dass **im Menü Extras der Befehl** Test angezeigt wird.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Veröffentlichen der Erweiterung in der Visual Studio Gallery
 Nun können Sie die Erweiterung in der Visual Studio Gallery veröffentlichen.

1. Stellen Sie sicher, dass Sie die Releaseversion ihrer Erweiterung erstellt haben und auf dem neuesten Stand sind.

2. Öffnen Sie in einem Webbrowser die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Website.

3. Klicken Sie in der oberen rechten Ecke auf **Anmelden**.

4. Melden Sie sich mit dem Microsoft-Konto an. Wenn Sie keine Microsoft-Konto haben, können Sie an dieser Stelle eine erstellen.

5. Klicken Sie auf **Hochladen**.

6. Wählen Sie in **Schritt 1: Erweiterungstyp** **Tool** aus, und klicken Sie dann auf **weiter**.

7. In **Schritt 2: Hochladen**können Sie auswählen, ob Sie direkt in die Visual Studio Gallery hochladen oder einfach einen Link zu ihrer eigenen Website hinzufügen möchten. Wählen Sie in diesem Fall **die Option Ich möchte mein Tool hochladen**aus. Das **Kontrollkästchen Steuerelement auswählen** wird angezeigt. Klicken Sie auf **Durchsuchen** , und wählen Sie dann im Ordner \bin\release des Projekts die Option testpublish. VSIX aus. Klicken Sie auf **Weiter**.

8. In **Schritt 3: grundlegende Informationen**werden Felder aus der Datei "Source. Extension. vsixmanifest" angezeigt. Wählen Sie eine geeignete **Kategorie** aus, und fügen Sie **Tags** hinzu, damit Benutzer ihre Erweiterung finden Möglicherweise möchten Sie eine ausführlichere Zusammenfassung und Beschreibung hinzufügen (die Beschreibung muss mindestens 280 Zeichen lang sein). Belassen Sie für den **Erweiterungstyp** **keine Microsoft-Erweiterung** und **Kosten Kategorie** als **Testversion**.

9. Lesen Sie den Beitrags Vertrag unten auf der Seite, und überprüfen Sie, ob **Ich stimme**zu.

10. Klicken Sie auf **Beitrag erstellen**. Dadurch wird die Seite angezeigt, die ihre Erweiterung in der Visual Studio Gallery hat, und es wird eine Meldung angezeigt, dass die Seite noch nicht veröffentlicht wurde.

11. Klicken Sie auf **Veröffentlichen**.

12. Durchsuchen Sie die Visual Studio Gallery nach ihrer Erweiterung. Die Liste für die testpublish-Erweiterung sollte angezeigt werden.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installieren der Erweiterung aus der Visual Studio Gallery
 Nachdem die Erweiterung veröffentlicht wurde, installieren Sie Sie in Visual Studio und testen Sie dort.

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

2. Klicken Sie auf **Online** , und suchen Sie nach testpublish. Die Liste für die testpublish-Erweiterung sollte angezeigt werden.

3. Klicken Sie auf **Download**. Nachdem die Erweiterung heruntergeladen wurde, klicken Sie auf **Installieren**.

4. Starten Sie Visual Studio neu, um die Installation abzuschließen.

## <a name="removing-the-extension"></a>Entfernen der Erweiterung
 Sie können die Erweiterung aus der Visual Studio Gallery und von Ihrem Computer entfernen.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>So entfernen Sie die Erweiterung aus der Visual Studio Gallery

1. Öffnen Sie die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Website.

2. Klicken Sie in der oberen rechten Ecke auf **meine Extensionen**. Die Auflistung für testpublish wird angezeigt.

3. Klicken Sie auf **Löschen**.

#### <a name="to-remove-the-extension-from-your-computer"></a>So entfernen Sie die Erweiterung auf dem Computer

1. Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungs-Manager**.

2. Wählen Sie testpublish aus, und klicken Sie auf **deinstallieren**

3. Starten Sie Visual Studio neu, um die Installation abzuschließen.
