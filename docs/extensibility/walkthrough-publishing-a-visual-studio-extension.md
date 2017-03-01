---
title: "Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterungs | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 574af4ff2b3858201c13121475de02a763572f6b
ms.openlocfilehash: fcfb0724b89d60553d6686a0705ab1e9459014ce
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterungs
In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie Visual Studio-Erweiterung der Visual Studio Gallery veröffentlichen. Wenn Sie die Erweiterung in der Galerie hinzufügen, können Entwickler **Erweiterungen und Updates** , es nach neuen und aktualisierten Erweiterungen zu suchen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-a-visual-studio-extension"></a>Erstellen Sie eine Visual Studio-Erweiterung  
 In diesem Fall verwenden wir eine standardmäßige VSPackage-Erweiterung, aber die gleichen Schritte gelten für jede Art von Erweiterung.  
  
1.  Erstellen Sie ein VSPackage in c# mit dem Namen `TestPublishing` , das einen Menübefehl hat. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="test-the-extension"></a>Testen Sie die Erweiterung  
 Bevor Sie die Erweiterung verteilen, erstellen Sie und Testen Sie, um sicherzustellen, dass es ordnungsgemäß in der experimentellen Instanz von Visual Studio installiert ist.  
  
1.  In Visual Studio debuggen. Um eine experimentelle Instanz von Visual Studio zu öffnen.  
  
2.  Wechseln Sie in der experimentellen Instanz, zu der **Tools** Menü **Extension Manager**. Die Erweiterung TestPublishing im mittleren Bereich angezeigt und aktiviert werden.  
  
3.  Auf der **Tools** Menü, stellen Sie sicher, dass Sie den Testbefehl angezeigt.  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Veröffentlichen Sie die Erweiterung in der Visual Studio Gallery  
 Jetzt können Sie die Erweiterung der Visual Studio Gallery veröffentlichen.  
  
1.  Stellen Sie sicher, dass Sie die Releaseversion der Erweiterung erstellt haben und auf dem neuesten Stand ist.  
  
2.  Öffnen Sie die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329) -Website in einem Webbrowser.  
  
3.  Klicken Sie in der oberen rechten Ecke auf **Anmeldung IN**.  
  
4.  Melden Sie sich mit dem Microsoft-Konto an. Wenn Sie nicht über ein Microsoft-Konto verfügen, können Sie zu diesem Zeitpunkt erstellen.  
  
5.  Klicken Sie auf **Hochladen**.  
  
6.  In **Schritt 1: Erweiterungstyp**auf **Tool** , und klicken Sie dann auf **Weiter**.  
  
7.  In **Schritt2: Hochladen**, Sie können direkt in Visual Studio Gallery hochladen, oder fügen Sie einfach einen Link zu Ihrer eigenen Website. Wählen Sie in diesem Fall **ich möchte mein Tool hochladen**. Die **wählen Sie das Steuerelement** angezeigt. Klicken Sie auf **Durchsuchen** und wählen Sie dann im Ordner \bin\Release des Projekts TestPublish.vsix. Klicken Sie auf **Weiter**.  
  
8.  In **Schritt 3: grundlegende Informationen**, Felder aus der Datei "Source.Extension.vsixmanifest" werden angezeigt. Wählen Sie die entsprechende **Kategorie** und fügen **Tags** , damit Benutzer Ihre Erweiterung suchen können. Möglicherweise möchten eine detaillierte Übersicht und Beschreibung (die Beschreibung muss mindestens 280 Zeichen lang sein) hinzufügen. Lassen Sie **Erweiterungstyp** als **nicht auf eine Microsoft-Erweiterung** und **Kosten Kategorie** als **Testversion**.  
  
9. Lesen Sie den Lizenzvertrag Beteiligung am unteren Rand der Seite, und überprüfen Sie **zustimmen**.  
  
10. Klicken Sie auf **Beitrag erstellen**. Die Seite, die die Erweiterung der Visual Studio Gallery mit einer Nachricht hat, dass die Seite noch nicht veröffentlicht wurde angezeigt.  
  
11. Klicken Sie auf **Veröffentlichen**.  
  
12. Suchen Sie die Visual Studio Gallery für die Erweiterung. Die Liste für die Erweiterung TestPublish sollte angezeigt werden.  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installieren Sie die Erweiterung von Visual Studio Gallery  
 Nun, dass die Erweiterung veröffentlicht wird, installieren Sie es in Visual Studio, und Testen sie es.  
  
1.  In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.  
  
2.  Klicken Sie auf **Online** und suchen Sie nach TestPublish. Die Liste für die Erweiterung TestPublish sollte angezeigt werden.  
  
3.  Klicken Sie auf **Download**. Nachdem die Erweiterung heruntergeladen wurde, klicken Sie auf **Installieren**.  
  
4.  Starten Sie Visual Studio neu, um die Installation abzuschließen.  
  
## <a name="removing-the-extension"></a>Die Erweiterung entfernen  
 Sie können die Erweiterung von Visual Studio Gallery und von Ihrem Computer entfernen.  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>So entfernen Sie die Erweiterung aus der Visual Studio Gallery  
  
1.  Öffnen Sie die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329) Website.  
  
2.  Klicken Sie auf der Mitte auf **My-Erweiterungen**. Die Liste für TestPublish wird angezeigt.  
  
3.  Klicken Sie auf **löschen**.  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>So entfernen Sie die Erweiterung von Ihrem computer  
  
1.  Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungs-Manager**.  
  
2.  Wählen Sie TestPublish aus, und klicken Sie dann auf **Deinstallieren**.  
  
3.  Starten Sie Visual Studio neu, um die Deinstallation abzuschließen.

