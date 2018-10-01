---
title: 'Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterungs | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66f6c6e4f59f271999294991dc66f71f16cf4a2f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511574"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Beachten Sie**: der Visual Studio-Katalog wird von Visual Studio Marketplace ersetzt wird. Die neueste Version dieses Themas Weitere Informationen anzeigen.

Die neueste Version dieses Themas finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-publishing-a-visual-studio-extension).  
  
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie Visual Studio-Erweiterung in der Visual Studio Gallery veröffentlichen. Wenn Sie die Erweiterung im Katalog hinzufügen, können Entwickler **Erweiterungen und Updates** dort nach neuen und aktualisierten Erweiterungen suchen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-a-visual-studio-extension"></a>Erstellen Sie eine Visual Studio-Erweiterung  
 In diesem Fall verwenden wir eine Standard-VSPackage-Erweiterung, aber die gleichen Schritte gelten für jede Art von Erweiterung.  
  
1.  Erstellen Sie ein VSPackage in c# mit dem Namen `TestPublishing` , das einen Menübefehl hat. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="test-the-extension"></a>Testen Sie die Erweiterung  
 Bevor Sie die Erweiterung verteilen, erstellen Sie und Testen Sie, um sicherzustellen, dass es in der experimentellen Instanz von Visual Studio ordnungsgemäß installiert ist.  
  
1.  In Visual Studio debuggen. Um eine experimentelle Instanz von Visual Studio zu öffnen.  
  
2.  Wechseln Sie in der experimentellen Instanz zu den **Tools** Menü **Erweiterungs-Manager**. Die Erweiterung TestPublishing sollten im mittleren Bereich angezeigt werden, und aktiviert werden.  
  
3.  Auf der **Tools** Menü sicherzustellen, dass den Testbefehl.  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Die Erweiterung in der Visual Studio Gallery veröffentlichen  
 Jetzt können Sie die Erweiterung in der Visual Studio Gallery veröffentlichen.  
  
1.  Stellen Sie sicher, dass Sie die endgültigen Produktversion von Ihrer Erweiterung erstellt haben und dass sie auf dem neuesten Stand ist.  
  
2.  Öffnen Sie die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329) -Website in einem Webbrowser.  
  
3.  Klicken Sie in der oberen rechten Ecke auf **SIGN IN**.  
  
4.  Melden Sie sich mit dem Microsoft-Konto an. Wenn Sie nicht über ein Microsoft-Konto verfügen, können Sie eine an diesem Punkt erstellen.  
  
5.  Klicken Sie auf **Hochladen**.  
  
6.  In **Schritt 1: Erweiterungstyp**Option **Tool** , und klicken Sie dann auf **Weiter**.  
  
7.  In **Schritt2: Hochladen**, können Sie direkt in Visual Studio Gallery hochladen oder einfach einen Link zu Ihrer eigenen Website hinzufügen. Wählen Sie in diesem Fall **ich möchte mein Tool hochladen**. Die **wählen Sie das Steuerelement** Feld wird angezeigt. Klicken Sie auf **Durchsuchen** und wählen Sie dann im Ordner \bin\Release des Projekts TestPublish.vsix. Klicken Sie auf **Weiter**.  
  
8.  In **Schritt 3: grundlegende Informationen**, Felder aus der Datei "Source.Extension.vsixmanifest" angezeigt. Wählen Sie einen geeigneten **Kategorie** und fügen **Tags** können Benutzer Ihre Erweiterung zu finden. Möglicherweise möchten hinzufügen, eine detaillierte Zusammenfassung und Beschreibung (die Beschreibung muss mindestens 280 Zeichen lang sein). Lassen Sie **Erweiterungstyp** als **nicht für eine Microsoft-Erweiterung** und **Kosten Kategorie** als **Testversion**.  
  
9. Lesen der Beitragsvereinbarung am unteren Rand der Seite, und überprüfen Sie **ich stimme zu**.  
  
10. Klicken Sie auf **Beitrag erstellen**. Die Seite, die Ihre Erweiterung in der Visual Studio Gallery, mit der Meldung aufweist, dass die Seite noch nicht veröffentlicht wurde angezeigt.  
  
11. Klicken Sie auf **Veröffentlichen**.  
  
12. Suchen Sie die Visual Studio Gallery für die Erweiterung. Die Auflistung für die Erweiterung TestPublish sollte angezeigt werden.  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installieren Sie die Erweiterung von Visual Studio Gallery  
 Nun, dass die Erweiterung veröffentlicht wurde, installieren Sie es in Visual Studio, und Testen sie dort.  
  
1.  In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.  
  
2.  Klicken Sie auf **Online** und suchen Sie nach TestPublish. Die Auflistung für die Erweiterung TestPublish sollte angezeigt werden.  
  
3.  Klicken Sie auf **Download**. Nachdem die Erweiterung heruntergeladen wurde, klicken Sie auf **Installieren**.  
  
4.  Starten Sie Visual Studio neu, um die Installation abzuschließen.  
  
## <a name="removing-the-extension"></a>Die Erweiterung entfernen  
 Sie können die Erweiterung von Visual Studio Gallery und von Ihrem Computer entfernen.  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>So entfernen Sie die Erweiterung aus der Visual Studio Gallery  
  
1.  Öffnen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329) Website.  
  
2.  Klicken Sie in der oberen rechten Ecke auf **Meine Extenions**. Die Liste für TestPublish wird angezeigt.  
  
3.  Klicken Sie auf **Löschen**.  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>Um die Erweiterung auf Ihrem Computer zu entfernen.  
  
1.  Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungs-Manager**.  
  
2.  Wählen Sie TestPublish aus, und klicken Sie dann auf **Deinstallieren**.  
  
3.  Starten Sie Visual Studio neu, um die Deinstallation abzuschließen.

