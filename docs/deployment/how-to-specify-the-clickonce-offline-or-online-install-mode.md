---
title: 'Gewusst wie: Angeben des Offline-oder Online Installationsmodus von ClickOnce | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcd9eeedfdd2a4661e3744da369a6fadc11039a3
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381755"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Vorgehensweise: Angeben des Offline- oder Onlineinstallationsmodus von ClickOnce
Der `Install Mode` für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung bestimmt, ob die Anwendung offline oder online verfügbar ist. Wenn Sie auswählen, dass **die Anwendung nur online verfügbar ist**, muss der Benutzer Zugriff auf den [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Veröffentlichungs Speicherort (entweder eine Webseite oder eine Dateifreigabe) haben, um die Anwendung auszuführen. Wenn Sie auswählen, dass **die Anwendung auch offline verfügbar ist**, fügt die Anwendung dem **Startmenü** und **dem Dialogfeld** "Software" Einträge hinzu. der Benutzer kann die Anwendung ausführen, wenn er nicht verbunden ist.

Der `Install Mode` kann auf der Seite **veröffentlichen** des **Projekt-Designers**festgelegt werden.

> [!NOTE]
> `Install Mode`Kann auch mit dem Veröffentlichungs-Assistenten festgelegt werden. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>So machen Sie eine ClickOnce-Anwendung nur online verfügbar

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie im Bereich **Installationsmodus und Einstellungen** auf die Options Schaltfläche **nur online verfügbar** .

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>So machen Sie eine ClickOnce-Anwendung online oder offline verfügbar

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie im Bereich **Installationsmodus und Einstellungen** auf die options **Schaltfläche Anwendung ist offline verfügbar** .

     Wenn die Anwendung installiert ist, werden dem **Startmenü** Einträge hinzugefügt und Programme in der Systemsteuerung **hinzugefügt oder entfernt** .

## <a name="see-also"></a>Siehe auch
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [How to: Publish a ClickOnce application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Veröffentlichungs-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)